+++
title = "nixos config share"
date = 2022-05-13
description = "my nixos configuration analysis"
+++

## Why NixOS

Nix, pure by design.
The advantages are not explained. This article more like a tutorial.

## Configuration analysis

- [my nixos config](https://github.com/ocfox/nixos-config)

enable flake `configuration.nix`
```nix
nix = {
  extraOptions = ''
    experimental-features = nix-command flakes
  '';
};
```

### boot
I use grub because its easy to use os prober and colorful theme.
```nix
boot.loader = {
  grub = {
    enable = true;
    device = "nodev";
    useOSProber = true; # os prober will auto add other system to grub
    efiSupport = true;
  };
  efi.canTouchEfiVariables = true;
};
```

### network
Simply use network-manager.
```nix
networking = {
  hostName = "whitefox";
  useDHCP = false;

  networkmanager = {
    enable = true;
    wifi.macAddress = "random";
    ethernet.macAddress = "random";
  };
};
# gui tool
programs.nm-applet.enable = true;
```

## TODO

The rest may be made up tomorrow.

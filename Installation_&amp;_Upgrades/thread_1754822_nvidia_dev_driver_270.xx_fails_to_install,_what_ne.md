---
title: "nvidia dev_driver 270.xx fails to install, what next?"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by vfulco on 2011-05-10
Dear Ubuntuer's

Have tried every combo of driver installation in hopes of installing Cuda 4.0 on vers. 10.10 and 11.04:

1) using pre-packaged PPAs from a number of generous contributors
2) stripping out separately and together nvidia-common, nvidia-current, nouveau drivers prior to adding latest
3) acpi, apic options in grub
4) incorporated earlier gcc/g++/cpp combo and soft linking before compiling
5) modifying xorg.conf to incorporate BusID info etc.
6) install of proprietary driver provided right after fresh OS install (260.xx version)

The nvidia supplied driver installs w/o error and nvidia-xconfig builds an xorg.conf.  While new to Ubuntu, not new to linux (usually run Fedora boxes).  Machine is a tyan h2000m 8 core with 12GB and a PNY GeForce 470 GTX. Virtualization and onboard video are turned off.  TIA for any trailheads.

---

### Post by Je Et on 2011-05-11
I used these instructions to load the latest drivers for my **GeForce 8400 GS**.  I forgot where I got it from, so thanks.

1. Add the PPA:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

```



2. Install the nVidia display drivers in Ubuntu 10.04, 10.10 or 11.04:

```
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```



Then go to** System** > **Administration **> **Hardware Drivers** and make sure** "Nvidia current"** ("current" means latest so that would be 270.18 for Ubuntu 10.04 and 10.10 and 270.2 for Ubuntu 11.04) is activated.


And finally,[B] restart.

[/B]

---


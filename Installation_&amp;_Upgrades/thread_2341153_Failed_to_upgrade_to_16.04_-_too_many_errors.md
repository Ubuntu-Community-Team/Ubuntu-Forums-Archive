---
title: "Failed to upgrade to 16.04 - too many errors?"
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by beenny on 2016-10-25
Hello,

I tried to upgrade from 14.04 to 16.04 and it stopped part way through saying there were too many errors. 

it says that the version is 16.04

```

]$lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

```

However when I try: sudo dpkg --configure -a

```

]$sudo dpkg --configure -a
...
Errors were encountered while processing:
 binfmt-support
 speech-dispatcher
 whoopsie
 grub-common
 initscripts
 kerneloops-daemon
 irqbalance
 cron
 sane-utils
 gnome-orca
 ubuntu-standard
 keyboard-configuration
 grub-pc-bin
 grub-pc
 grub2-common
 xserver-xorg-core
 mdadm
 xserver-xorg-video-radeon
 procps
 xserver-xorg
 grub-gfxpayload-lists
 openssh-server
 xserver-xorg-video-vesa
 openvpn
 udev
 xserver-xorg-video-amdgpu
 gnome-bluetooth
 xserver-xorg-video-cirrus
 xserver-xorg-video-tdfx
 upstart
 samba
 ubuntu-minimal
 xserver-xorg-input-wacom
 console-setup-linux
 nvidia-340
 nvidia-331-updates
 xserver-xorg-input-synaptics
 unity-greeter
 bluez
 xserver-xorg-video-mach64
 indicator-bluetooth
 python3-checkbox-support
 xorg
 python3-checkbox-ng
 xserver-xorg-video-ati
 nvidia-340-updates
 pulseaudio
 plainbox-provider-checkbox
 xserver-xorg-video-sisusb
 console-setup
 xserver-xorg-video-intel
Processing was halted because there were too many errors.

```

Running: sudo apt-get upgrade gives a whole bunch of errors (i get forum errors when trying to paste the full output)

Things mostly seem to be working normally but I am noticing some random errors - for example it doesn't seem to recognize my network printer anymore - and am obviously a bit concerned that things underneath are not stable.

Before I try to reinstall the backup image from 14.04 or just go for fresh install any thoughts would be appreciated...

bg

---

### Post by ian-weisser on 2016-10-25
Try installing 16.04 afresh first.
If that fails, then use your 14.04 backup image.

Most upgrade failures are due to non-Ubuntu software. Non-Ubuntu software should be uninstalled before upgrading to a new release of Ubuntu.

---

### Post by beenny on 2016-10-25
Thanks for the reply - that seems odd as I've never had that issue before. And while I know direct upgrades aren't the safest approach, having to reinstall and configure external software (virtual box, vpns etc.) is a pretty big nuisance and the appeal of the direct upgrade.

is there a way to fix the errors without a fresh install or have i missed the boat on that?

---


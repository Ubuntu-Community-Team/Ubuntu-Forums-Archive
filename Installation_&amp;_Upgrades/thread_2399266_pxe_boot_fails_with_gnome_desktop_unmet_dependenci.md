---
title: "pxe boot fails with gnome desktop unmet dependencies - libmutter Bionic"
date: 2018-08-23
forum: Installation &amp; Upgrades
---

### Post by apwhawkins on 2018-08-23
Hi, new to pxe booting (and reasonably new to linux really) so probably cocking something up but I'm getting 

I've tried putting standard before ubuntu-desktop in the preseed.cfg but same error (does the order here make a difference to the install order?)

```
Aug 23 13:51:17 in-target: xserver-xorg is already the newest version (1:7.7+19ubuntu7.1).Aug 23 13:51:17 in-target: xserver-xorg-input-all is already the newest version (1:7.7+19ubuntu7.1).
Aug 23 13:51:17 in-target: xserver-xorg-input-all set to manually installed.
Aug 23 13:51:17 in-target: xserver-xorg-video-all is already the newest version (1:7.7+19ubuntu7.1).
Aug 23 13:51:17 in-target: xserver-xorg-video-all set to manually installed.
Aug 23 13:51:17 in-target: Some packages could not be installed. This may mean that you have
Aug 23 13:51:17 in-target: requested an impossible situation or if you are using the unstable
Aug 23 13:51:17 in-target: distribution that some required packages have not yet been created
Aug 23 13:51:17 in-target: or been moved out of Incoming.
Aug 23 13:51:17 in-target: The following information may help to resolve the situation:
Aug 23 13:51:17 in-target:
Aug 23 13:51:17 in-target: The following packages have unmet dependencies.
Aug 23 13:51:18 in-target:  gnome-shell : Depends: libmutter-2-0 (>= 3.28.3-1~ubuntu18.04.1) but 3.28.2-2~ubuntu18.04.1 is to be installed
Aug 23 13:51:18 in-target: E
Aug 23 13:51:18 in-target: : Unable to correct problems, you have held broken packages.
Aug 23 13:51:18 in-target:
Aug 23 13:51:18 in-target: tasksel: apt-get failed (100)
Aug 23 13:51:18 /bin/in-target: warning: /target/etc/mtab won't be updated since it is a symlink.
Aug 23 13:51:18 main-menu[286]: WARNING **: Configuring 'pkgsel' failed with error code 1
Aug 23 13:51:18 main-menu[286]: WARNING **: Menu item 'pkgsel' failed.
```



pxe
```
LABEL ubuntu_install      menu label ^Install ubuntu bionic (amd64) with desktop
      TEXT HELP 
      Installs Ubuntu 18.04 desktop
      ENDTEXT
      kernel ubuntu/ubuntu-installer/amd64/linux
        append vga=normal nomodeset locale=en_GB vga=788 initrd=ubuntu/ubuntu-installer/amd64/initrd.gz auto=true url=192.168.21.4/d-i/bionic/./with-desktop.cfg hostname=unassigned-hostname domain=unassigned-domain --- quiet 
```




without-desktop.cfg - happy to include others as necessary 
```
d-i preseed/include string standard_settings.cfgd-i debconf/priority string critical


#### Packages #####
#include the standard ubuntu packages with desktop
tasksel tasksel/first multiselect ubuntu-desktop standard


d-i debian-installer/add-kernel-opts string nomodeset


d-i anna/choose_modules string network-console
d-i network-console/password password test
d-i network-console/password-again password test
```

also ends up calling packages.cfg
```
# Allow non-free firmwared-i hw-detect/load_firmware boolean true


##packages
d-i pkgsel/update-policy select unattended-upgrades


d-i pkgsel/include string openssh-server,git,curl,python,r8168-dkms,wakeonlan,etherwake,ansible
```

---


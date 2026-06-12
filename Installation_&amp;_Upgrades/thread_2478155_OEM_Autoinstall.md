---
title: "OEM Autoinstall"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by specig on 2022-08-18
Due the high demand of Ubuntu laptops on my customer I wanted to make UEFI Netboot to OEM install laptops because it more convenient than using customized USB stick.

I did set this up: [https://ubuntu.com/server/docs/install/netboot-amd64](https://ubuntu.com/server/docs/install/netboot-amd64)
Had little tuning to suit my needs.
```
menuentry 'Ubuntu 20.04' {
        gfxmode $linux_gfx_mode
        linux /vmlinuz ip=dhcp url=http://192.168.0.1/ubuntu-20.04.4-live-server-amd64.iso autoinstall ds='nocloud-net;s=http://192.168.0.1/ks/' cloud-config-url=/dev/null fsck.mode=skip ---
        initrd /initrd
}
```
I also installed apt-cacher-ng in same machine as dnsmasq

Then started fine tuning user-data file which ended up to look like this:

```
#cloud-config
autoinstall:  
  proxy: http://192.168.0.1:3142/
  update: all
  debconf-selections: oem-config      oem-config/steps        multiselect language, timezone, keyboard, user, network, tasks
  interactive:
   - identity
  identity:
    hostname: ubuntu-oem-install
    password: $6$5lpwCLsKLEzMkSJc$keOAhA6aO/5RocGThmhVA7LSNuW911Rx5HHXFEa75oGK20cEdAAgn14H5f5nGeq6QgcSyLPrWcg1.JvjXbhrN/
    realname: OEM (Temporary user)
    username: oem
  keyboard:
    layout: fi
  locale: en_GB.UTF-8
  timezone: Europe/Helsinki
  packages:
    - ubuntu-desktop-minimal
    - cryptsetup
    - oem-config
    - oem-config-gtk
    - oem-config-slideshow-ubuntu
    - ubiquity
    - ubiquity-casper
    - ubiquity-frontend-debconf
    - ubiquity-ubuntu-artwork
    - firefox
  late-commands:
  - curtin in-target --target=/target -- sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=""/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/' /etc/default/grub
  - curtin in-target --target=/target -- apt update; apt -y upgrade
  - curtin in-target --target=/target -- update-grub
  - curtin in-target --target=/target -- oem-config-prepare --quiet
  - curtin in-target --target=/target -- rm /etc/apt/apt.conf.d/90curtin-aptproxy /etc/netplan/00-installer-config.yaml /etc/cloud/cloud.cfg.d/99-installer.cfg
  - curtin in-target --target=/target -- cp /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
  - curtin in-target --target=/target -- sed -i '/unmanaged/ s/$/,except:type:ethernet/' /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
  version: 1


```

In late-commands apt proxy settings and account creation are removed and LAN connection management is fixed.

Final installation is bare minimum Ubuntu 20.04 LTS installation. 22.04 version is still in progress as it uses more snap than 20.04 and I'm not keen to it.
What I've tested only change is this:
From:```
     - firefox
```
To:```
  snaps:
     - name: firefox
```

---

### Post by grahammechanical on 2022-08-18
I do not know what your question is. I do know, however, that the Ubuntu 22.04 software repositories do not contain a deb packaged version of Firefox. A fresh install of Ubuntu 22.04 will give the user a snap packaged version of Firefox. An upgrade from 20.04 to 22.04 will remove the deb packaged version of Firefox and replace it with the snap packaged version.

In Ubuntu 22.04 the snap packaged version of Firefox will update itself without requiring the user (or IT department) to run Software Updater. What is best for your customer regarding the web browser being up to date with security fixes?

Avoiding snap applications will complicate your install script but once the script has been perfected it will require little modification. That is a consolation. I am trying to avoid the usual taking of sides in the matter of snap packages.

Regards

---

### Post by specig on 2022-08-30
There was no question. This was meant to be guide to provide OEM  installation as net install with 20.04 LTS and 22.04, and as said, 22.04  portion not being tested as no snap wanted to be installed.
Question to do this is floating all over internet.

---


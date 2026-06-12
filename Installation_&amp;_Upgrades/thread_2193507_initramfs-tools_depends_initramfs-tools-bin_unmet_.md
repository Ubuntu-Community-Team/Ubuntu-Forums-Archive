---
title: "initramfs-tools depends initramfs-tools-bin unmet dependency"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by ph.gachoud on 2013-12-13
Cannot get rid of a dependency problem with Ubuntu server LTS, and dont want to reboot to see what comes....

```
pg@bmSrv01: /home/sshuser$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.3.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.4.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.2.0-57-generic-pae:
 linux-image-3.2.0-57-generic-pae depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-57-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.2.0-56-generic-pae:
 linux-image-3.2.0-56-generic-pae depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-56-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-56-generic-pae; however:
  Package linux-image-3.2.0-56-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.56.66); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-57-generic-pae
 linux-image-3.2.0-56-generic-pae
 linux-image-generic-pae
 linux-generic-pae


```
Tried to update software-source and to put it from other locations, but sucks 

Thx in advance

---

### Post by ian-weisser on 2013-12-13
> **ph.gachoud said:**
> ```

dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin ([COLOR=#ff0000]<< 0.99ubuntu13.3.1~[/COLOR]); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.4.

```

Version 0.99ubuntu13.3.1~ , and the requirement that the version be *lower* than that, looks a lot like a PPA or other non-Ubuntu software dependency.

Have you disabled all of your PPAs and Non-Ubuntu sources?

---

### Post by ph.gachoud on 2014-02-20
I solved it after a while searching by downloading initramfs-tools with right version [here]("http://packages.ubuntu.com/precise-updates/all/initramfs-tools/download").
so in commandline that does:
```
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.4_all.deb
sudo dpkg -i initramfs-tools_0.99ubuntu13.4_all.deb
sudo apt-get update
sudo apt-get dist-upgrade
```
Had to terminate it after for kernel headers which was also not resolved with apt-get -f install with:
```
aptitude update
aptitude safe-upgrade
aptitude build-dep
```

---

### Post by mörgæs on 2014-02-20
Good, please mark the thread 'solved'.

---

### Post by ph.gachoud on 2014-02-20
> **ian-weisser said:**
> Version 0.99ubuntu13.3.1~ , and the requirement that the version be *lower* than that, looks a lot like a PPA or other non-Ubuntu software dependency.

Have you disabled all of your PPAs and Non-Ubuntu sources?
Thx but didnt work did already not have PPAs

---


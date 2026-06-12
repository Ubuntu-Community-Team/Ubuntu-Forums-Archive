---
title: "kickstart to install VM ?"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by juju43 on 2014-08-23
Hello

I want to automate local install of my lubuntu and try the ubuntu adaptation of kickstart which I used to use on Redhat side.
I create a ks.cfg from a 12.04 install (14.04 one is broken [https://bugs.launchpad.net/ubuntu/+source/system-config-kickstart/+bug/1260107](https://bugs.launchpad.net/ubuntu/+source/system-config-kickstart/+bug/1260107))

I launched a VM from iso (desktop-amd64+mac) file and with usb key adding to other parameters (F6) ks=hd:sdb1:/ks-ubuntu.cfg
but installation starts interactively and with gui whereas I asked for text.
I can check than my usb key is sdb1 but I can't explain why it's ignore.

is it functional? or not like this post seems to imply
[http://ubuntuforums.org/showthread.php?t=2105286](http://ubuntuforums.org/showthread.php?t=2105286)

Booting with debug nosplash, doesn't give any indication on usage of kickstart


Thanks

---

### Post by TheFu on 2014-08-23
I've never used KS.
cobbler? [http://www.cobblerd.org/](http://www.cobblerd.org/)

Written by RH and the same guy who is behind Ansible today.

---


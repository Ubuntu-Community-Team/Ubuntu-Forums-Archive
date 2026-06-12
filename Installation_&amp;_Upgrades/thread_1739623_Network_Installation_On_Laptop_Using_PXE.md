---
title: "Network Installation On Laptop Using PXE"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by somepalli on 2011-04-26
HI!

     i want to install Ubuntu on my Local Network. I am able to boot and i am selecting one install Ubuntu from manual repository but i am not able to install. There i am getting message called " [COLOR="Red"]Bad image error[/COLOR]"  but same Iso i written and installed on my desktop but i want to install this through network.
I have followed [[COLOR="Navy"]https://help.ubuntu.com/community/Installation/LocalNet[/COLOR]]("https://help.ubuntu.com/community/Installation/LocalNet") this documentation. 

the following is my config

[INDENT]
[COLOR="RoyalBlue"]

DISPLAY boot.txt

DEFAULT ubuntu


LABEL ubuntu
        kernel ubuntu/lucid/i386/vmlinuz
        append vga=normal initrd=ubuntu/lucid/i386/initrd.gz boot=casper netboot=nfs nfsroot=192.168.2.178:/root/nfs/ubuntu --

PROMPT 1
TIMEOUT 0
[/COLOR]
[/INDENT]

please help me regarding this.

---


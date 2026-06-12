---
title: "unable to install packages"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by Scapegoat427 on 2011-09-28
when running: sudo dpkg --configure -a

i get:

Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Failed to symbolic-link boot/initrd.img-2.6.32-33-generic to initrd.img: File exists
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-33-generic; however:
  Package linux-image-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.33.39); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-33-generic
 linux-image-generic
 linux-generic

been searching around online and everyone's answer has been to run dpkg --configure -a to fix the problem... which obviously doesnt.

running xubuntu, 64 bit... not sure what else you'd need in order to assist me with this issue.

thanks in advance

---

### Post by vinterkind on 2011-09-29
if you've got all the conflicts why don't you

```
apt-get install -f
```

that should solve your problems ...

---

### Post by Scapegoat427 on 2011-09-29
i swear i gave that a try and i'd receive the same errors... but i just ran it and it worked...

been scowering the internet for a while looking for a solution and i know i'm come across that command.

thanks so much

---

### Post by vinterkind on 2011-09-29
yeah. 

its a devilish pair, dpkg and apt. :-)

good I could help.

---

### Post by vinterkind on 2011-09-29
you should mark this thread solved then... ):P

---


---
title: "Boot hang after v24 upgrade"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by John Franklin on 2010-09-07
Since allowing Upgrade Manager to perform an incremental upgrade of 10.04 to 2.6.32-24-386, boot-up hangs with the error message:

"udevadm trigger is not permitted while udev is unconfigured."

Subsequently:

"Gave up waiting for root device"

If I interrupt boot-up with ESC and select the previous version (2.6.32-23-386) all is OK again.

What do I do to resolve this issue or remove the v24 upgrade?

---

### Post by mörgæs on 2010-09-07
I wouldn't try to roll back a kernel update. The safe approach is doing as you do: Boot into an older kernel. 

When a new kernel is released, let's see if the bug is fixed.

---

### Post by andrewthomas on 2010-09-07
boot to an older kernel then do

```
sudo update-initramfs -u
```

---

### Post by bayouoldguy on 2010-09-07
Sorry for the duplicate problem post...same situation......have tried Update Manager, etc, no effect......will keep up on this thread also......."G"    ( a Bug! ???? not in our Ubuntu ! ):D

---

### Post by bayouoldguy on 2010-09-07
> **andrewthomas said:**
> boot to an older kernel then do

```
sudo update-initramfs -u
```

I just performed this operation.....got the same boot error message.
............."G"

---

### Post by andrewthomas on 2010-09-07
> **bayouoldguy said:**
> I just performed this operation.....got the same boot error message.
............."G"
what was the output of the update-initramfs command?  did it show that the initrd.img 2.6.32-24-386 was created? you may have to 
edit /etc/initramfs-tools/initramfs.conf 
```
gksudo gedit /etc/initramfs-tools/update-initramfs.conf 
```or 
```
sudo nano /etc/initramfs-tools/update-initramfs.conf 
```and change 
```
update_initramfs=yes
```to 
```
update_initramfs=all
```

---

### Post by John Franklin on 2010-09-08
Andrew,

Thank you very much. That's fixed it for me.

Should I reset update-initranfs=yes?
Also, for information, could you please tell me what initranfs does? Does it just produce a boot image (that, presumably, was originally corrupt)?

John

---

### Post by bayouoldguy on 2010-09-08
> **andrewthomas said:**
> what was the output of the update-initramfs command?  did it show that the initrd.img 2.6.32-24-386 was created? you may have to 
edit /etc/initramfs-tools/initramfs.conf 
```
gksudo gedit /etc/initramfs-tools/initramfs.conf 
```or 
```
sudo nano /etc/initramfs-tools/initramfs.conf 
```and change 
```
update_initramfs=yes
```to 
```
update_initramfs=all
```

update: ran the following in terminal:
  sudo update-initramfs -u -k2.6.32-24-386
fixed the 32-24-386 version, I need to fix the other 32-24-386 generic to keep everything in step
......."G"...:D      thanks guys

---


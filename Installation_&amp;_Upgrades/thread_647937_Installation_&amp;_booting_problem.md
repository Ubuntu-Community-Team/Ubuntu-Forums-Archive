---
title: "Installation &amp; booting problem"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by thomabrown on 2007-12-22
I am an absolute newbie to ubuntu, although I am a retired computer professional dating back to 1961. 

I am trying to install ubuntu 7.10 on a system consisting of an ASUS A7V133, 2 ide drives, an Athlon 900 MHz cpu, etc. The system also contains Windows 2000 and multiple versions of OS/2 (eComstation) with booting controlled by IBM's Boot Manager. No flames for this, please! :) I am trying to install to a 5 GiB logical partition (ext3) with a 1 GiB partition for the swap on ide. I am using the partitioner in Manual mode. Centos worked in this environment, but I decided to switch to ubuntu. 

I have tried both the CD and DVD desktop versions downloaded and burned on another machine. 

I do not want the ubuntu loader to clobber Boot Manager, so I have tried various things to this end:
1. Telling it NOT to install the loader.
2. Telling it to install the loader in the root partition (hda8).

I get an error message late in the installation:
    Executing 'grub-install (hda5)' failed.
    This is a fatal error.
    [OK]

When I click OK, the progress bar finishes, and I am left with an object named '/target' on the desktop. 

End-of-story... :(

How do I get the loader (grub, I guess) installed in the root partition? 

Thanks!

---

### Post by meierfra on 2007-12-23
If ubuntu is on hda5  this should work:
Boot from the live cd, open a terminal and  type
```
sudo grub
root (hd0,4)
setup (hd0,4)
quit

```
(You will get a non-fatal error message about stage1.5 files.  That's normal. )
If you get any other error message post it here.

If this did not work post the output of

```
sudo fdisk -lu
```

and 

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda5 /ubuntu
cat /ubuntu/boot/grub/menu.lst
```

---


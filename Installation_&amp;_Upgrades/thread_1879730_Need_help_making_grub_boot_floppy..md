---
title: "Need help making grub boot floppy."
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Fennecat on 2011-11-12
I'm following the directions at [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy) but I run into a roadblock at the final line of step 3.

The output is always ```
cp: cannot stat 'stage1': No such file or directory
cp: cannot stat 'stage1': No such file or directory
```Tried multiple disks, same result.  Please advise?

---

### Post by raja.genupula on 2011-11-12
[http://www.justlinux.com/forum/showthread.php?t=142409](http://www.justlinux.com/forum/showthread.php?t=142409)

[http://linux-sxs.org/administration/grubflop.html](http://linux-sxs.org/administration/grubflop.html)

---

### Post by oldfred on 2011-11-12
All the instructions are for grub legacy, but most today now have grub2 installed. Either you have to install grub legacy to have it to create a grub legacy boot or create a grub2 floppy or bootable CD.

Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by nobody00 on 2011-11-22
Referring to the above [http://members.iinet.net/~herman546/...l#GRUB2_CD-ROM](http://members.iinet.net/~herman546/...l#GRUB2_CD-ROM) when attempting to make a grub boot floppy I noticed that grub-mkrescue 1.99 with Grub2 no longer has a --image-type=floppy option.  I tried using --diet option but this only reduced the iso image to 1.6 MB - not below the 1.4 MB limit. I successfully made a custom boot CD with the 1.99 grub-mkrescue, but would prefer to free up the my only DVD/CD drive.  Should I assume that boot floppies are no longer supported by grub2?

---


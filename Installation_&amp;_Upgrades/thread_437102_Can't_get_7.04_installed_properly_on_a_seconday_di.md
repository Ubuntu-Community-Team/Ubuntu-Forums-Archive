---
title: "Can't get 7.04 installed properly on a seconday disk"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by feenster on 2007-05-08
Hi all,
I'm struggling to get Ubuntu installed and bootable on a Hard Drive that isn't my primary one. In my system, i have an NTFS SATA drive split into 2 partitions (sda1 and sda2). I then have a second IDE hard drive (hda) that i've installed Ubuntu onto (letting Ubuntu create all the partitions on the drive, and install Grub wherever it chooses).

So, this doesn't let me boot into Ubuntu. Therefore, I booted with a Live CD and took the first 512 blocks from the disk and put it into a *.bin file I could use to boot Ubuntu (as [seen here](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last&x-showcontent=text)). However, this hasn't worked either.

Can anyone give me a clue how to get XP and Ubuntu 7.04 dual booting from seperate hard drives?

Cheers,
  Matt

---

### Post by bulldog on 2007-05-08
Which hdd is your master boot device?
If it's the Sata hdd you should try and boot from the IDE hdd.
In most cases the IDE hdd is (hd0) and if you didn't change anything,it's most likely the hdd which has GRUB in the MBR.

If this is the case,you probably can't boot into windows from GRUB,we have to edit the menu.lst.
But give it a try to see if GRUB is on the IDE hdd.

---

### Post by feenster on 2007-05-08
Ah! That's done the trick. I assumed that hd0 would just mean the first hard disk in the boot sequence (hence, my SATA drive). Having changed this around in the BIOS, i can now get into Grub. It complains that Ubuntu hasn't been installed properly, but at least i can now get in there to switch things around. 

Many thanks for your help.

Matt

---

### Post by bulldog on 2007-05-08
Make the IDE hdd master boot device,and edit the menu.lst to boot into windows.
You have to add some lines in your windows entry,make it look like this [rootnoverify,and mapping lines]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1
```

---

### Post by feenster on 2007-05-09
Many thanks again. I'll reinstall Ubuntu and try again.

Cheers,
    Matt

---


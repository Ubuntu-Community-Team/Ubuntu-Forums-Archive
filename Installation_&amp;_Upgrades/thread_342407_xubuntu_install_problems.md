---
title: "xubuntu install problems"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by uthturn on 2007-01-20
i have tried to install xubuntu on an older pc (hp brio) with 64mb everytime i goto to install it makes it all the way to the grub install and fails say can't place in /target/ folder Did i partition wrong or what? Thanks for any help!:D

---

### Post by K.Mandla on 2007-01-20
Are you using the live CD or the alternate CD? If I remember right, those Brios were ~300Mhz, right? You might want to use the alternate CD if the live one is giving you problems.

---

### Post by uthturn on 2007-01-20
i'm using the alternative cd and low memory install
its 800mhz

---

### Post by Wofl on 2007-01-20
my install went fine on an ibm thinkpad i1200.
it was about the same configuration.
can you try installing lilo? maybe that one works.

---

### Post by K.Mandla on 2007-01-20
It might be worthwhile to run the CD check, just to be sure your CD didn't mis-burn.

You can also reinstall Grub by booting the alternate CD and picking "Rescue a broken system." When it asks, tell it you want to install Grub to /dev/hda (I'm assuming you used the default partition configuration).

If that doesn't work for you, you can install LILO as a bootloader and it won't make a bit of difference in how Ubuntu runs. Some people even like LILO better, although I can't imagine what sets the two apart ... except that Grub is finicky about the file system ... by the way, you're not trying to install Grub to an unusual file system, are you?

---

### Post by uthturn on 2007-01-20
lilo did the same thing i'll try the cd check i'm using the normal file system i think i may have messed in the partitioning of the drive i don't really know how to do it right and i have not found any good instructions yet

---

### Post by uthturn on 2007-01-20
it said the cd is valid is it possible that i did something in the partitioning that took up the boot sector or something(forgive me if i'm talking nonsense) it seems the grub or lilo cannot install to the boot sector

---

### Post by K.Mandla on 2007-01-20
It's possible. Do you have anything else (like Windows) on that drive? You're not trying to build a dual boot, are you?

---

### Post by uthturn on 2007-01-20
nope just xubuntu

---

### Post by K.Mandla on 2007-01-20
Check out some of these pages. These are community videos on how to install Ubuntu.

[http://www.ubuntuvideo.com/tutorial_installing_ubuntu](http://www.ubuntuvideo.com/tutorial_installing_ubuntu)
[http://ubuntuclips.org/videos/18](http://ubuntuclips.org/videos/18)

In general, if you're using only Xubuntu, you can use the default partition option -- I think it's  "Use entire disk" or something to that effect. It should set up two partitions for you and proceed with installation. Don't bother with LVM or manual partitioning until you're comfortable with the process.

---


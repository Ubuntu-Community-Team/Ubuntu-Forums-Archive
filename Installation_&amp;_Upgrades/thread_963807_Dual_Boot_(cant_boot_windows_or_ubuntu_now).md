---
title: "Dual Boot (cant boot windows or ubuntu now)"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by littletone2002 on 2008-10-30
I'm running windows xp
I have 3 hards drives, 2 ide and 1 SATA

IDE - 80gig (set jumper as primary/master)
  Partition 1 - Windows (NTFS)
  Partition 2 - Ubuntu (EXT3)

IDE - 200gig (set jumper as secondary/slave)
  1 partition - file storage

SATA - 750gig (no jumper)
  1 Partition - file storage

In windows under disk manager, it says the 80gig is Hd0, 200gig is Hd1 and 800gig is hd2. 

I installed UBUNTU, restarted and automatically Windows loaded, wasn't given the option to boot into Ubuntu. So i loaded the Ubuntu Live CD again, used GRUB to set HD1 as the location of my MBR (even though windows says it's Hd0). I think the SATA is messing it up.

RESTARTED...GREAT! Now i get a boot menu!

tried loading Ubuntu and it says, "unable to mount partition"

tried loading Windows and it says, "Invalid device requested"

HELP!

---

### Post by Mark Phelps on 2008-10-30
Post the results of "sudo fdisk -lu"

---

### Post by Pumalite on 2008-10-30
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by ABCC on 2008-10-30
It could be that grub is trying to load the kernel off of the wrong partition. One good way to trigger this is changing the boot order of your hdd's after an installation.

You can make one-off edits to your grub configuration from the boot menu. Select the kernel you're trying to boot and hit 'e' and you'll be given the ability to edit the settings. Look for the 'root (hdX,Y)' section and try editing the hdX part. 0 is the 1st hdd and 1 the 2nd, but you may need to flip these around to get it to boot.

ABCC

---

### Post by Pumalite on 2008-10-30
You have a problem of mix IDE and SATA. Grub tends to boot IDE even if Ubuntu is somewhere else. Review this thead. The answer lies within:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2008-10-30
If your Grub's menu.lst is not too far off, which it shouldn't be since you have a new install, this should get you into Ubuntu: on start up when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If that doesn't work, try X=1 or 2. Based on the info you gave, one of those combos should work. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to whichever (hdX,Y) worked to boot Ubuntu, save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set about booting Ubuntu. If you want help booting Windows, just let me know which (hdX,Y) worked to boot Ubuntu, and we can work from there. :)

---


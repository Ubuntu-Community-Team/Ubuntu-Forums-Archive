---
title: "Ubuntu on removable hard drive."
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by MadnessRed on 2008-10-01
Hi, my dad has installed ubuntu on his laptop, on a removable hard drive.

here is the problem, if the hard drive is removed then it says Error 21. (in grub boot loader)

Is it possible to any of these?

1) If the removable hard drive is plugged in use grub, else just boot windows normally.

2) Use the windows bootloader with a link to grub

3) Move grub to the internal hard drive, and use that.

4) Anything else that will let the computer run without the external HDD plugged in.

---

### Post by cariboo on 2008-10-01
The first hing to do is fix your windows boot, if you have a windows install disk (not a recovery disk) boot from it into the recovery console and use FIXMBR and FIXBOOT to get windows booting properly. Then follow this howto:

```
http://ubuntuforums.org/showthread.php?t=80811
```

It is for an older version but it will work. Follow the instructions to the letter, don't jump around, and you should have a working dual boot system.

Jim

---

### Post by lamagy on 2008-10-01
yo i did the same but grub ain't being recognised and only xp loads.

i updated the install screen of the bootloader to /dev/sdc  

which is my usb drive, problem is that there are 6 partitions on this disk, linux is in (h2,5) should i have installed the bootloader to /dev/sdc5  ?????

pls help guys, about to quit linux world...lol

---

### Post by MadnessRed on 2008-10-02
many thanks for the fast responce, I will let you know how it goes.

---

### Post by drudogg on 2008-10-02
if you are booting from an external hard drive, then i would use the BIOS boot device option to boot it, not any info on the internal drive... just make the external bootable, and leave teh internal alone.  
that way, internal works fine when external is not present, and external can bypass teh internal when it is hooked up.

---

### Post by MadnessRed on 2008-10-03
Hi (Dad here)
Thanks to cariboo907.
At least now have Windows XP back.
Unfortunately I am now in the same position as lamagy.
External hard drive just not recognised on boot up.
In my case I reformatted the entire external drive for Ubuntu.
Followed each step carefully, except that Rescue Mode wasn't available (used sudo to get round this and careful selection of the full paths) also used Gedit instead of VIM.

Any help greatfully received - Thanks

---

### Post by caljohnsmith on 2008-10-04
> **MadnessRed said:**
> Hi (Dad here)
Thanks to cariboo907.
At least now have Windows XP back.
Unfortunately I am now in the same position as lamagy.
External hard drive just not recognised on boot up.
In my case I reformatted the entire external drive for Ubuntu.
Followed each step carefully, except that Rescue Mode wasn't available (used sudo to get round this and careful selection of the full paths) also used Gedit instead of VIM.

Any help greatfully received - Thanks
Can you set your BIOS to boot the external (removable) HDD on start up? Usually the ideal strategy for your situation is if you can boot the external HDD, then you can just install Grub to the MBR (Master Boot Record) of the external drive and thus leave the Windows drive untouched. You can then add an entry in the Grub menu to boot your Windows drive so that you can easily boot Windows without changing the BIOS boot order. 

If you would like to do that, then first install Grub to the MBR of the external drive by doing the following from a terminal (applications > accessories > terminal) in Ubuntu:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y), for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also, please post the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there.

---

### Post by MadnessRed on 2008-10-04
Hi, is there a way to load Ubuntu from the live cd? not the live mode but the ubuntu currently installed, if I type in hd(1,5) for example in the boot options.

---


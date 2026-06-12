---
title: "hardy does not detect my sata hard drive"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jjf on 2008-04-26
I have a Dell Inspiron 530.  It's got a 500gb SATA hard drive and a SATA DVD-RW.  It runs AwardBIOS, which gives an option to set my SATA drives to either "IDE" mode or "RAID" mode.  By default it was set on "IDE" mode.  Changing it to "RAID" mode means Vista doesn't boot, so that's not an option.

I had 7.10 Gutsy running just fine.  Then I did a network upgrade to Hardy and my system would no longer boot.  So I tried a clean install from the alternate CD (I prefer the alternate for greatest compatibility), but the installer stopped early in the process, complaining that it couldn't find my CD drive.  

So I found an external CD drive, plugged it into my USB port, and the installer detected it and kept going.  But now it can't find my hard drive.  It gives me this message:

> No disk drive was detected.  If you know the name of the driver needed by your disk drive, you can select it from the list.

And it gives me a long list of drivers.

So in short, my SATA drives need to be in IDE mode for Vista.  Gutsy could recognize them just fine.  Hardy cannot.  Does anyone know a fix for this, or know which driver I might select from the list?  My BIOS reports my hard drive as a WDC WD5000AAKS-75YGA.

Thanks.  (I'm also downloading the regular install CD to see if there's a difference, but I doubt it.)

---

### Post by Pumalite on 2008-04-26
I have installed Hardy in IDE and SATA without a problem. Maybe you have a bad burn. Try burning a new CD at 4x or less after doing md5sum.

---

### Post by jjf on 2008-04-26
I've burned the standard CD this time (and I burn all my CDs in GnomeBaker at 2x or 4x with "BurnFree" enabled), and still no good.  As it's supposed to be booting from CD, it keeps giving this message:

> ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
ata2.00: status: { DRDY }

It records what I assume is the time off to the left, and so far it's been repeating this message for 866.098365 seconds.

edit:  I tried again and noticed this message buried in there:

> ata2.00: WARNING: synchronous SCSI scan failed without making any progress

---

### Post by Pumalite on 2008-04-26
Maybe is time to try some boot parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

Start with the most common ones. To be tried alone or in different combinations:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=775
all-generic-ide

---

### Post by jjf on 2008-04-26
Ok, I did some more googling, and it is a Hardy bug.  It was also a Gutsy bug, apparently, but Gutsy works just fine for me.  

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702)

From what I can see, there are three solutions.  

**1. switch to RAID mode in my BIOS**
disadvantage: Vista doesn't work.  (Anyone know how to configure Vista to work in RAID mode?)  I have a few games I play, so this is a deal killer.

**2. Use boot option all_generic_ide**
I'd need to edit my grub configuration file to always start Ubuntu with this option.  
disadvantage: Unknown (will I take a performance hit?  are there other disadvantages?)

**3. Following [Dell's instructions]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang"), write a script that loads the SATA drivers before the USB drivers**
This apparently obviates the conflict that causes Ubuntu to hang.
disadvantage: Somebody on the launchpad bug report page says, "that recipe forces loading ata_piix before USB. But the thing is that inspirons 530 (at least mine) comes with ICH9 chipset, so the right driver should be the more advanced AHCI, which will use all the advanced capabilities in the ICH9..."  I don't know what those capabilities are.  Does anyone here?

Thanks for any help.  For now I'll read Pumalite's links and try to figure out how to add the all_generic_ide option to grub.  But if somebody knows and can just tell me, I'd appreciate the time saved.

---

### Post by Pumalite on 2008-04-26
I'd say go with all_generic-ide. You will not take a performance hit. I forgot to add it to my previous post.

---

### Post by jjf on 2008-04-26
Adding all-generic-ide seems to work.  Some odd behavior (forcing me to log in twice :confused:), but things seem to be OK.

Thanks!

---

### Post by Pumalite on 2008-04-26
Youre welcome. Good luck.

---

### Post by Rocket2DMn on 2008-04-26
I had this problem when installing (I used the alternate install cd).   I had to add "acpi=off noapic" to the kernel boot options.
Then had to remember to add them manually to /boot/grub/menu.lst later and add savedefault.
In any case, glad you got it working.

---

### Post by jjf on 2008-04-26
It worked a few times and them started giving me the same problem again.  Not sure if it's a degenerating problem or just random.

Anyway, I followed the Dell instructions here:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

and my first boot was successful.  See if it keeps it up.

---

### Post by gentracer on 2008-06-08
Hi,

I am running ubuntu 7.10 and have purchased a Seagate 320GB SATA internal hard drive with a NexStar CX enclosure - it connects to my laptop (Inspiron E1505) via USB.  However, when I connect the hard drive, ubuntu doesn't recognize that a new drive has been attached so I can get to the point of formatting it.  I just want to use the drive to backup files, etc. - no OS, no booting from it, etc.

Any suggestions on how to proceed would be appreciated.

Thanks.

---

### Post by Rocket2DMn on 2008-06-08
Install GParted
```
sudo apt-get install gparted
```
You can then access it from System->Administration->Partition Editor
You can view attached drives/partitions by running
```
sudo fdisk -l
```
You should be able to select the new drive from the drop down box in the upper right corner in GParted, and then you can format it to the filesystem of your preference.

---

### Post by gentracer on 2008-06-08
That worked - guess I was trying to make it harder than it was.  I thought the system needed to "see" the drive before I could format it.

Thanks much!

---

### Post by SillyChild on 2008-06-24
> **jjf said:**
> Adding all-generic-ide seems to work.  Some odd behavior (forcing me to log in twice :confused:), but things seem to be OK.

When I add all-generic-ide option, my system goes into some testing phase that goes on for over 30 mins. Not sure if this is how it is suppose to behave. Any suggestions?

Thanks.

---


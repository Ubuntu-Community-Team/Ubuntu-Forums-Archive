---
title: "can't install ubuntu"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by bobetko on 2007-02-08
I have DELL laptop, Pentium 3, 533Mhz, 256 MB RAM with XP pro installed. (XP is corrupted since it is crashing all the time). I did CHKDSK and found no bad sectors on the hard drive.

I am trying to install Ubuntu 6.06. When I boot from CD, Ubuntu starts and I have "install" icon on the Ubuntu desktop. When I double click it, installation starts, but after about 10 minutes it freezes.  I would never reach a point where would I choose how would I like to partition disk. I was thinking to do clean Ubuntu installation and wipe out XP.

On some forum I found that LBA support on the NTFS partition has to be turned off. But, I have no clue how to do that. If I format hard disk, should I use NTFS or FAT, or something else? I was thinking to boot Knoppix (that works perfect) and then to format hard disk. As I said my disk is NTFS, will Knoppix be able to reformat it and how?. Would that help?

A lot of questions.... I know...
Can somebody help me? 
 
Thanks,

---

### Post by housam on 2007-02-08
You can format the entire HDD using Gparted ( it is a partitioning tool on ubuntu live cd). boot from the cd , then system >> admin. >> Gnome partition editor 
After formating (deleting ) the HDD , create a new 3 partitions : one for the root ( / ) ext3 format ( more than 5 GB. The second swap format 1 Gb for the swap partition. The third is ext3 for /home partition which has the rest of the HDD.
Then go for the installation.

---

### Post by go2dell on 2007-02-08
First off, that's a good machine for running Ubuntu.  If you install Ubuntu and decide it's too slow for you, give Xubuntu a try before you go running back to Windows or to another distro.

Also, I'm wondering if you chose Dapper (6.06) because you have an older machine.  If so, you can safely use Edgy (6.10), since newer versions typically work just as well on older machines.  This is not Windows, where each new version has skyrocketing hardware requirements.

[LIST=1]
[*] Are you *certain* you want to delete Windows?  I personally am in favor of it.  You can always reinstall later if you decide you want to dual-boot.  Just don't forget to back up your e-mail! ;)

[*] LBA support is something that's done in your computer's BIOS.  It's a method the computer uses to figure out how to access the drive.  I can't imagine any reason to turn it off for Windows XP or for pretty much any Linux distro.  Leave it on.

[*] If you are **not** keeping Windows, then there's no need for the NTFS filesystem.  The default Ubuntu filesystem (Windows term: format) is *ext3*.  There are others that work equally as well, or maybe even better, but unless you have a good reason to choose something else and fully know what you're doing, stick with ext3 and you'll have no worries.  If you **are** keeping Windows, you'll need an NTFS partition, since it won't recognize ext3.

[*] There are quite a few things that could halt your installation.  If you're wanting to keep Windows, then you might want to try Knoppix and resize your existing partition from there.  If you're happy with kicking Windows to the curb, then just download the Ubuntu Alternate Install CD.  It's a text-based install, so it's fairly light on system resources compared to the regular graphical install.
[/LIST]

Good luck!

---

### Post by bobetko on 2007-02-08
Thanks both... but it's not working....


As Housam said:
I divided HD on 3 partitions, first 7GB, second 1GB and rest I have 11GB. 
Question here: what do I choose for partition types? 1 GB partition, is that Linux Swap type?

Anyway, whatever I did, installation froze 5 minutes after I would double click Install icon.

During booting from CD, briefly, I would see a message (before graphics interface (GNOME or KNOME, or...) would start.

.... etc .... serio2/bus/failed ... etc...
Activating Swap
Mounting function not implemented 

One thing to mention, maybe it's important, CD rom on my laptop is external. I never had any problem with that (Ubuntu boots from it)... but... maybe later during installation something happen...

Is there way to manually install Ubuntu, or somehow to check where and why it failed.

Thanks

---

### Post by housam on 2007-02-08
> **bobetko said:**
> Thanks both... but it's not working....


As Housam said:
I divided HD on 3 partitions, first 7GB, second 1GB and rest I have 11GB. 
Question here: what do I choose for partition types? 1 GB partition, is that Linux Swap type?

Anyway, whatever I did, installation froze 5 minutes after I would double click Install icon.

During booting from CD, briefly, I would see a message (before graphics interface (GNOME or KNOME, or...) would start.

.... etc .... serio2/bus/failed ... etc...
Activating Swap
Mounting function not implemented 

One thing to mention, maybe it's important, CD rom on my laptop is external. I never had any problem with that (Ubuntu boots from it)... but... maybe later during installation something happen...

Is there way to manually install Ubuntu, or somehow to check where and why it failed.

Thanks

1Gb partition is the swap partition and its format is swap linux. the other two partitions should has an ext3 format. but this is not the problem. 
Did you checked the cd for defects ? did you run it and figured it out before the install ? 
If every thing is ok , I think you should download the alternate cd or xubuntu .

---

### Post by bobetko on 2007-02-08
I did that (1GB partition -> Linux Swap)

I tested CD installation several times... it is OK... did memory tests.... everything was fine....

I am running installation again and this time things are little bit different:
didn't have that message: **serio0/serio2/ failed**

and now, upon booting ubuntu I have dialog windo open with message:

[B]The Panel encountered a problem while loading "OAFIID:GNOME_panel_wirelessApplet"
Do you want to delete applet from configuration. <don't delete> <delete>
[/B]


Is this something about wireless modem?

Anyway, I will click "delete" and try one more time.

Thanks

---

### Post by Bartender on 2007-02-08
You mention Windows crashing all the time.  Ubuntu sounds like it's all over the place.

I'm wondering if it's hardware.  Failing power supply, bad capacitors on the motherboard, something like that?

---

### Post by bobetko on 2007-02-09
Windows would reboot itself every hour or so. First it would show some error message then, it would start counting until 0, then it would restart. It could be virus maybe... if it was, now it's gone... 

I am not sure if hardware is OK... I let it run that memory test, it did it for a while and didn't report any problems.

---


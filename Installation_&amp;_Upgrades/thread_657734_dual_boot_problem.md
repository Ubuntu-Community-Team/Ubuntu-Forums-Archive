---
title: "dual boot problem"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by rc33 on 2008-01-03
I've been poking around and trying to solve this on my own but keep hitting dead ends. Someone please help me. Here's my situation. I currently have XP home edition on a SCSI SATA 80g HD (sda1), and a second HD installed that is a 40g IDE1 (hda1)

I have a 10g partition for Linux Ubuntu 7.1 on the IDE, during the setup I went into Advanced to change the boot section from (hda1) to (sda1) because the other way was just booting windows. I got an error that GRUB failed to install on (sda1)

What i'd like to do is keep my single partition 80g SATA intact with XP on it and have 10gigs for Ubuntu on the IDE and the other 30gigs NTFS while having the dual boot process work. Is this possible?

---

### Post by logos34 on 2008-01-03
> **rc33 said:**
> ...during the setup **I went into Advanced to change the boot section from (hda1) to (sda1)** because the other way was just booting windows. I got an error that GRUB failed to install on (sda1)

The default grub location in 'Advanced' section is '(hd0)'--in your case the mbr of the IDE drive, which is almost certainly how grub is seeing it.  You wanted (hd**1**) or **/dev/sda**.  Reinstall and use the latter format preferably but make sure not to put a '1'--you want to overwrite the windows bootloader on the sata mbr, NOT the bootsector of the windows C: partition, sda1. (otherwise you won't be able to boot XP even if you fix grub)

---

### Post by rc33 on 2008-01-05
ok I did the /dev/sda now I have the boot menu which is good. But when I select Linux I get "Error 22: No such partition" and when I select Windows XP I get "NTLDR is missing"  I tried hitting "e" and changing around the root (hd0,1) to like every combo but nothing is working. I'm on the Live cd right now.

---

### Post by confused57 on 2008-01-05
You might want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by rc33 on 2008-01-05
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15921591

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4028    32354878+   7  HPFS/NTFS
/dev/hda2            4029        4822     6377805   83  Linux
/dev/hda3            4823        4865      345397+   5  Extended
/dev/hda5            4823        4865      345366   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95649564

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

---

### Post by confused57 on 2008-01-05
I would recommend trying to install grub to the mbr of your IDE drive, if your bios is capable of booting first to the IDE drive...you can do this with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in the howto, but you need to do something like this:
```
sudo grub
find /boot/grub/stage1
```
use the results of the above, then:
```
root (hdx,1)
setup (hdx)
quit
```
for example, if root is (hd1,1), then setup (hd1)

Then go into your bios setup & change the hard drive boot order to IDE, then SATA...if you get a grub boot menu, then highlight your Ubuntu entry, press "e", select the line with root, change root from (hd1,1) to (hd0,1), press "enter", then "b" to boot.

This is temporary if it works, but it can be made permanent and an entry to boot Windows can be added.

---

### Post by rc33 on 2008-01-05
It worked! Thanks alot man! Now you said something about making it permanant? Because I been updating and rebooting and it's been working fine. Am I all set you think?  Also since I am new to Linux Ubuntu is there anything I should know about as far as security software or firewalls or any of that to keep myself safe and spyware free?

thanks again... you are a life saver.

---

### Post by confused57 on 2008-01-05
> **rc33 said:**
> It worked! Thanks alot man! Now you said something about making it permanant? Because I been updating and rebooting and it's been working fine. Am I all set you think?  Also since I am new to Linux Ubuntu is there anything I should know about as far as security software or firewalls or any of that to keep myself safe and spyware free?

thanks again... you are a life saver.
Glad to hear it worked...while you're booted into Ubuntu, you may want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also, to make the changes permanent, you need to make the changes in your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change your root line(s)  to show (hd0,1) and make sure to change the line with #groot to (hd0,1)
quit & save

The Windows entry in this thread should boot Windows on your sda:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Ubuntu has a builtin firewall...iptables.  You can install firestarter which is a GUI frontend for iptables.  Ubuntu is quite secure, you shouldn't have to worry about viruses or spyware.

Added:  menu.lst is short for menu.list, not menu.first...it's usually better to copy & paste commands that are given.

---

### Post by zipperback on 2008-01-05
I posted links to dual boot tutorials on the following thread.
[http://ubuntuforums.org/showthread.php?t=653213](http://ubuntuforums.org/showthread.php?t=653213)

Scroll through until you find my postings.

- zipperback
:popcorn:

---

### Post by logos34 on 2008-01-05
> **rc33 said:**
> ok I did the /dev/sda now I have the boot menu which is good. But when I select Linux I get "Error 22: No such partition" and when I select Windows XP I get "NTLDR is missing"  I tried hitting "e" and **changing around the root (hd0,1) to like every combo but nothing is working**. I'm on the Live cd right now.

rc33,

Glad you fixed everything...confused57 can be a life-saver when it comes to dual-booting.

The only reason I suggested what I did (grub on sata mbr) was it was already the boot drive and I figured it would sidestep the potential pitfalls of booting xp on a non-first hard disk (map commands, etc,).  Of course I neglected to mention that you would have to edit the root lines.   But at any rate you say you tried every combo for (ubuntu) root...actually either (hd1,1) or (hd0,1) should have worked.  Why didn't it?  Did /boot/grub/device.map need to be edited also?  Confused57? Anyone? 

In the future it looks like I'll suggest putting grub on the IDE mbr--that way there will be no doubt about what drive is being seen by grub as (hd0)

---

### Post by confused57 on 2008-01-05
> **logos34 said:**
> rc33,

Glad you fixed everything...confused57 can be a life-saver when it comes to dual-booting.

The only reason I suggested what I did (grub on sata mbr) was it was already the boot drive and I figured it would sidestep the potential pitfalls of booting xp on a non-first hard disk (map commands, etc,).  Of course I neglected to mention that you would have to edit the root lines.   But at any rate you say you tried every combo for (ubuntu) root...actually either (hd1,1) or (hd0,1) should have worked.  Why didn't it?  Did /boot/grub/device.map need to be edited also?  Confused57? Anyone? 

In the future it looks like I'll suggest putting grub on the IDE mbr--that way there will be no doubt about what drive is being seen by grub as (hd0)

Hi logos34,
    I also would have thought that (hd1,1) would have worked, with grub installed to sda....it's possible that his device.map may have needed editing for this to work?
   I've seen it more than once when there is a mixture of IDE and SATA drives, the Ubuntu installer recognizes the IDE drive as (hd0), even if the SATA drive is the first boot drive in bios.  I'm wondering what was the output of "find /boot/grub/stage1"...it may already have been (hd0,1) and no modifications of his menu.lst were needed.  

   I have an IDE and 2 SATA drives, Gutsy recognizes them as sda, sdb, & sdc...I noticed Gutsy recognizes rc33's IDE drive as hda.  This probably depends on the hard drive controller/chipset and "may" make a difference in how the installer recognizes the hard drive boot priority?

---

### Post by logos34 on 2008-01-06
> **confused57 said:**
> Hi logos34,
    I also would have thought that (hd1,1) would have worked, with grub installed to sda....it's possible that his device.map may have needed editing for this to work?

Well, here's how I interpret it: the installer was seeing the ide drive as (hd0) despite the fact that it was second, and he installed grub to /dev/sda, aka (hd1), so it seems to me (on second thought) that it should have booted without further adjustment (assuming, as you say below, root was designated 'hd0,1').  

  >  I've seen it more than once when there is a mixture of IDE and SATA drives, the Ubuntu installer recognizes the IDE drive as (hd0), even if the SATA drive is the first boot drive in bios.  I'm wondering what was the output of "find /boot/grub/stage1"...it may already have been (hd0,1) and no modifications of his menu.lst were needed. 

  I have an IDE and 2 SATA drives, Gutsy recognizes them as sda, sdb, & sdc...I noticed Gutsy recognizes rc33's IDE drive as hda.  This probably depends on the hard drive controller/chipset and "may" make a difference in how the installer recognizes the hard drive boot priority?

hda vs. sda: That's exactly what I think it depends on--the controller or chipset.  What else it could be?  Because my ide's are recognized as 'hd_' not 'sd_'...I've been expecting it to change since feisty and it doesn't.  So I guess it's my chipset (nvidia nforce).  Maybe the latter also determines the boot order like you say, interesting...hadn't really considered that.

---


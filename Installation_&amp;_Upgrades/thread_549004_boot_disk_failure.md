---
title: "boot disk failure"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by bobgunnison on 2007-09-12
Ok I searched the forum and google and could not figure out what the deal is with my computer.  I got fed up with windows and decided to go with ubuntu.  I secure erased the one hard drive I have connected and only setup ubuntu, but everytime I try to load it, it says disk boot failure, insert system disk.  Then I have to put in winxp and press enter, then it loads to the grub screen.  I have turned everything in my bios off the doesn't need to be on.  I have used super grub disk to try to fix the mbr.  if anyone has any ideas as to what is going on please help out.  At least until then windows has some kind of purpose even if it is only to load a far better operating system.

---

### Post by dcstar on 2007-09-12
> **bobgunnison said:**
> Ok I searched the forum and google and could not figure out what the deal is with my computer.  I got fed up with windows and decided to go with ubuntu.  I secure erased the one hard drive I have connected and only setup ubuntu, but everytime I try to load it, it says disk boot failure, insert system disk.  Then I have to put in winxp and press enter, then it loads to the grub screen.  I have turned everything in my bios off the doesn't need to be on.  I have used super grub disk to try to fix the mbr.  if anyone has any ideas as to what is going on please help out.  At least until then windows has some kind of purpose even if it is only to load a far better operating system.

If your BIOS reports "disk boot failure" then the install process did not complete correctly on the hard disk you are trying to boot off.

If you say that Grub is on the disk with Windows, then it was installed there and not on the other hard disk.

Assuming you have PATA drives, set up your *empty" hard drive as a "Master" on the Primary channel, and your Windows drive as a "Slave" (or put it on the Secondary IDE channel), and then do the Ubuntu installation again.

This should ensure that the boot code is written to the new drive.

---

### Post by bobgunnison on 2007-09-12
I only have one hard drive and it did have windows on it but I secure erased it and set up only ubuntu on the drive after that. no more windows installed at all.  That is why it makes no since to me as to why I need to put in the winxp disk when I get the disk boot failure error.  After I insert the disk it scans it and says press any key to boot disk.  I dont press any keys, then it loads to grub and then straight into unbuntu.  I've tried reseting my cmos, it's like i have a brand new drive yet it is still asking for a windows cd. pretty much the only thing I haven't tried is throwing the computer out the window.  Once again, sorry to post, I usually search like hell before posting a question

---

### Post by dabl on 2007-09-12
> **bobgunnison said:**
> 

I secure erased it 



What exactly do you mean by this terminology "secure erase"?  Can you boot your Windows CD and use FDISK on that drive, to absolutely clear it?  It sounds like there is something in the Master Boot Record of that hard drive that is interfering with the installation of Linux.  Or, use my personal favorite, GParted, to make new partitions on it, which will also nuke the residuals. It is on the Ubuntu Live CD, and you can also make a GParted Live CD by downloading the ISO from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:)

---

### Post by eggdeng on 2007-09-12
Sounds like grub is installed to the / partition with the W*ndw*s bootloader still on the MBR. The only fix I can think of is to reinstall making sure to install grub to the MBR.
Edit: Just came across this thread [http://ubuntuforums.org/showthread.php?t=545666]("http://ubuntuforums.org/showthread.php?t=545666")

---

### Post by dcstar on 2007-09-12
> **bobgunnison said:**
> I only have one hard drive and it did have windows on it but I secure erased it and set up only ubuntu on the drive after that. no more windows installed at all.  That is why it makes no since to me as to why I need to put in the winxp disk when I get the disk boot failure error.  After I insert the disk it scans it and says press any key to boot disk.  I dont press any keys, then it loads to grub and then straight into unbuntu.  I've tried reseting my cmos, it's like i have a brand new drive yet it is still asking for a windows cd. pretty much the only thing I haven't tried is throwing the computer out the window.  Once again, sorry to post, I usually search like hell before posting a question

Possibly the boot flag has not been set on the partition - or there was an old "System utilities" partition on the disk that still has the boot flag set.

Get Linux loaded up, and then (in a terminal) run:
```
sudo cfdisk
```
You should see "Boot" under the flags of your Linux partition, if not then you should be able to set it.

If you install** gparted** that will also allow you to check (and set) this.

---

### Post by bobgunnison on 2007-09-12
By secure erase I meant I used "dban", darik's boot and nuke.  it made three passes of writing and and completely erasing the hard drive.  Took about 4 hours to do it, so I thought it would have worked. I got into ubuntu and ran sudo cfdisk and it came up with a  boot flag, so I guess I'll try gparted after I get off work.

---

### Post by bobgunnison on 2007-09-12
Alright,  I used gparted and it showed two partitions. one ext3 and one swap. the ext3 was flagged with boot.  Really not sure what else to do here.  I was using the 64 bit edition, so I am going to try the x86 one and see if anything works out better. will post how it goes

---

### Post by dabl on 2007-09-12
Mmmmmmmmmm... I would not predict different behavior out of the i386 version, regarding this particular issue.

Are there any BIOS options for the "mode" of that hard drive?  I recall seeing recent posts where folks had to change an IDE mode -- not sure if was from "ahcp" to "pata" or exactly how that worked, but apparently there are some modes that Linux doesn't like.  On my rig, I think the IDE drive actually has 3 possible BIOS settings for "mode" -- you might want to fiddle with that.  :)

---

### Post by psusi on 2007-09-12
Wait, so ubuntu boots if you just have the windows install cd in the drive but do not press the key to boot it?  Wow, sounds like a really messed up bios problem.

---

### Post by bobgunnison on 2007-09-12
dabl it didn't seem to work and psusi you explained it just right.  I think I just need to reinstall my bios.

---

### Post by dabl on 2007-09-12
> **bobgunnison said:**
>   I think I just need to reinstall my bios.



Maybe. At least check your OEM's site, and make sure you have the current version.

---

### Post by bobgunnison on 2007-09-12
hahahahahahahahahahahahaha, where to start.  Well I flashed the bios and that didn't work so as I was loading winxp to run the repair console and fixmbr, I was thinking of what to write in here off of the laptop.   Right when I started typing I hear a loud BOOM.  My winxp cd shattered into countless pieces in the drive as if to say HOW DARE YOU.  Needless to say whenever I can afford any computer I will be getting a Mac.  Somebody correct me if I'm wrong, but I think that since they use intel now your could load ubuntu and dual boot?  Anywho, I'm mentally drained and can't take anymore computer crap.

---

### Post by psusi on 2007-09-13
LOL, I had a feeling there was something screwed up with that drive.  Try unplugging it and seeing if you can now boot ubuntu from the hard disk.

---

### Post by Bothered on 2007-09-13
> **bobgunnison said:**
> I hear a loud BOOM.

Yikes :shock:

You may be able to use the ubuntu LiveCD to boot the system (selecting "Boot from first hard disk"), if your cd drive still works.

Are you sure that your bios is set to boot off the hard disk? If it is, is it set to boot from the hard disk first (is it first in the boot order). It sounds to me like it isn't trying to boot from the hard disk at all.

---

### Post by bobgunnison on 2007-09-13
Finally got it.  I think it was the dvd drive going out and messing with the bios while loading.  Replaced that and installed Feisty about three more times with little tweaks here and there, but it's finally working.  Thanks for all the help everybody.

---


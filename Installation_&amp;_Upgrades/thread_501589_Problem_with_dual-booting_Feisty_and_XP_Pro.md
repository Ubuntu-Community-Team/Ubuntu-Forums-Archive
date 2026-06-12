---
title: "Problem with dual-booting Feisty and XP Pro"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by whobutdrew on 2007-07-15
I have an old IBM T40 laptop that I would like to run XP Pro and Feisty on.  It has one 40GB hard drive, split roughly evenly between the two OSes.  I have installation CDs for both operating systems.

I followed the dual-boot instructions found here:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

Everything is fine until I try to boot Windows after Feisty is installed.  I get an "Unmountable Boot Volume" bluescreen error, followed by a prompt restart.  Windows worked fine prior to the installation of Feisty.

I booted to the XP install CD and ran *chkdsk /R* from the Recovery Console.  All I get is "The volume appears to contain one or more unrecoverable problems."  

Feisty worked fine prior to me trying *fixboot* to write over GRUB with NTLDR, not knowing that it was going to wipe out my entire partition structure.

I tried doing Feisty first and then XP, but the XP installer didn't recognize my partitions (1 FAT, 1 ext3, 1 swap) and saw just one "Unknown Partition" HD.

I'm willing to go XP then Ubuntu again, if someone can help me avoid XP freaking out when I add on Feisty.

Thanks!

---

### Post by dreadlord_chris on 2007-07-15
> **whobutdrew said:**
> I have an old IBM T40 laptop that I would like to run XP Pro and Feisty on.  It has one 40GB hard drive, split roughly evenly between the two OSes.  I have installation CDs for both operating systems.

I followed the dual-boot instructions found here:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

Everything is fine until I try to boot Windows after Feisty is installed.  I get an "Unmountable Boot Volume" bluescreen error, followed by a prompt restart.  Windows worked fine prior to the installation of Feisty.

I booted to the XP install CD and ran *chkdsk /R* from the Recovery Console.  All I get is "The volume appears to contain one or more unrecoverable problems."  

Feisty worked fine prior to me trying *fixboot* to write over GRUB with NTLDR, not knowing that it was going to wipe out my entire partition structure.

I tried doing Feisty first and then XP, but the XP installer didn't recognize my partitions (1 FAT, 1 ext3, 1 swap) and saw just one "Unknown Partition" HD.

I'm willing to go XP then Ubuntu again, if someone can help me avoid XP freaking out when I add on Feisty.

Thanks!

I think that at this point that's going to be your best bet. This time though, when you install XP, just have Windows split the drive - and leave the other half as unpartitioned space. This way the Ubuntu insall won't have to muck about with resizing partitions - which is the #1 reason dual-boots crap out....
Then I would follow this guide:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by whobutdrew on 2007-07-15
It does make a bit more sense to do it that way, in retrospect.  Going to try that now.  Thanks for the tip!

---

### Post by whobutdrew on 2007-07-15
Crap, no go.  Same BSOD with "Unmountable Boot Volume."

I had XP create a 15GB partition for itself when I installed it, left the rest alone.  Worked fine, installed a few hardware drivers, rebooted to install Feisty.  I told it to "Use largest unallocated space."  I took particular notice that it claimed /dev/sda2 for itself (and sda5 for swap).  Feisty itself runs fine, though.

Am I doomed to picking between the two?  I can try and grab an error code from the Windows boot if it would help.

---

### Post by bulldog on 2007-07-15
If you boot into feisty,can you copy your menu.lst to the forum?
```
cat /boot/grub/menu.lst
```

---

### Post by whobutdrew on 2007-07-15
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=51331317-490c-44f6-9ec0-ee7545554e2c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=51331317-490c-44f6-9ec0-ee7545554e2c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51331317-490c-44f6-9ec0-ee7545554e2c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51331317-490c-44f6-9ec0-ee7545554e2c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Figured you didn't want all of the comments in the beginning.  Default is '0' and timeout is '10', in case you were curious.  I didn't make any changes to this file after Feisty was installed.

I can also mount the XP partition and make changes to it, FWIW.

The BSOD error code is 0x000000ED.   I googled it, the prognosis isn't good.  :(

---

### Post by merlinus on 2007-07-15
You might try running

chdsk c: /f

on your windows partition from the recovery console, since it seemed there were errors in your original xp install.

It may be that your hard disk has bad blocks.

-merlin

---

### Post by bulldog on 2007-07-15
Can you give us the outcome of ```
sudo fdisk -l
``` as well?

I read that the BSOD could have something to do with wrong drivers for your motherboard,do you use the original drivers for the mobo?

---

### Post by whobutdrew on 2007-07-15
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15732328+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            1960        4738    22322317+  83  Linux
/dev/sda3            4739        4864     1012095    5  Extended
/dev/sda5            4739        4864     1012063+  82  Linux swap / Solaris

```

Now that's interesting... 

Just about any commands in the XP recovery console fail.  I poked around with *chkdsk* and *bootcfg*, I was wary of *fixboot* and *fixmbr* after what happened last time.

Thanks to everyone for your help!

---

### Post by whobutdrew on 2007-07-15
Missed your question at the end, I haven't changed any drivers for the mobo.  

This machine runs fine with one OS on it (XP or Ubuntu, its had both in its lifetime).  This only started when I wanted to do both.

---

### Post by bulldog on 2007-07-15
Partition 1 does not end on cylinder boundary.
This is not as it should be.

If you reinstall the windows boot loader,it doesn't wreck your ubuntu.
Just reinstall GRUB with the live cd and your ubuntu is running again.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

But it seems your hdd has some faults on it,try to correct them first.

---

### Post by whobutdrew on 2007-07-15
Should I run *fixmbr* first, then follow those steps, or just reinstall GRUB?

---

### Post by whobutdrew on 2007-07-17
*fixmbr* rewrote the MBR, but I still can't boot Windows, I get the same error.  I then ran *diskpart* from the Recovery Console and I got the same thing when I tried to install Ubuntu then XP: one big partition of "Unknown type' that spans the entire drive instead of the 3 that I have.

Something in the Feisty install is screwing up how Windows can see the hard drive.  I got past the "partition doesn't end on cylinder boundary" error at least.  After running *fixmbr* 3 megs of space became 'unallocated.'  I resized the Windows partition then ran *sudo fdisk -l* and everything came back clean.

Is giving this laptop 2 OSes simply not meant to be?

---

### Post by Vadi on 2007-07-27
I'm having the same problem here actually :/. Adapting to Ubuntu...

Also, T40's come with a hidden patrition that's supposed to restore everything. But for whatever reason, doing 'Restore Factory Settings' from Access IBM fails to get the right driver letters.

---

### Post by whobutdrew on 2007-07-27
Unfortunately, I don't have good news for you.  I gave up on the dual-boot scenario and am just running XP on the laptop now.  Ah well.  Dual boot would have been nice, but at least its functioning now.

At least you still have that recovery partition, that was blown away long ago by the friend I inherited this from.

I hope you have better luck than I did!

---

### Post by Vadi on 2007-08-14
Well I decided to stick with Ubuntu, it's fitting me quite nicely.

I am a bit confused though... I have this "IBM_PRELOAD" folder on the desktop that looks like Windows. I think that's the supposed hidden patrition that IBM would use when you select the restore factory settings option.

But if only I knew how to make use of it...

---

### Post by jimbob on 2007-08-14
For those who are still getting the "unmountable boot volume"  message I was able to fix my dual boot setup by creating my Ubuntu root and swap partitions beforehand using stand alone Gparted and then during the Ubuntu install by selecting "manual partitioning" instead of "use largest unallocated space".

I noticed that when I selected "use largest unallocated space" for some reason Ubuntu created an extended partition and put my root and swap under it even though the original ex pee disk had only one primary partition followed by 10Gb of unallocated space.  There is no reason to do this that I know of since a disk is allowed to have 4 primary partitions before moving into extended partitions.  

At any rate after doing it this way and forming 3 primary partitions everything worked perfectly.
It is my belief that it is the extended partitioning that causes Windows to declare the disk "unmountable".

Use Gparted to see if your HDD has extended partitions and get rid of them if it does.  Hope this works for you also.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Vadi on 2007-08-14
Thank you for replying, finally someone who can help me out with this.

I got gparted, launched it, but I can't really tell if there are extended patritions, so I took a screenshot - you can [see it here]("http://vadis.applets.googlepages.com/Screenshot--dev-sda-GParted.png").

Can you tell if I have the extended patritions?

---

### Post by jimbob on 2007-08-14
No you don't.  Your layout looks quite good as a matter of fact..

What exactly is happening on your system now?  If you boot the XP installation CD and choose R for recovery can you run chkdsk /p ?  If you can, and follow that with fixmbr and fixboot can you then boot windows normally?

How did you install Ubuntu - Live/Install CD or Alternate CD?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Vadi on 2007-08-14
I don't have an XP installation CD, IBM didn't ship me one (remember the hidden patrition deal?).

I installed Ubuntu with a Live CD - booted from it, clicked Install on the Desktop, got confused in the patritoner but somehow got it working.

I'll see if I can download the installation CD from somewhere.

---

### Post by Vadi on 2007-08-16
I'm thinking of reinstalling Ubuntu altogether, because I've messed it up quite a bit already.

What would you recommend I do when installing it again? Patrition the drive from Windows, not let the installer patritioner do it?

---

### Post by dabl on 2007-08-16
Download and burn a GParted Live CD from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) 

You can boot your GParted Live CD, and make sure your drives are partitioned as you wish.  Make a separate partition for your /home directory if you can -- it helps protect your data in case you need to reinstall the OS>

---

### Post by jimbob on 2007-08-16
> Patrition the drive from Windows, not let the installer patritioner do it?

This implies that your windows is working.  I was under the impression that it wasn't.

If so, your partitions look fine if they are as your attachment shows.  I would go ahead and install Ubuntu from the alternate CD (download/burn it if you don't have it) and choose "manual partitioning" and use those existing partitions.

It is also a good idea to burn the Gparted CD as dabl suggests above to avoid having some  partitions locked when you are trying to work with them.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Vadi on 2007-08-16
Well, I wiped my HD by accident by giving it a name or something. 

I've pre-patritioned my hd with gparted from the live cd before installing, and got ubuntu working fine now.

I think I'll try the virtualization option...

---

### Post by bliffle on 2007-08-17
I, too, have a T40 that I bought used 3 years ago with a fresh XP and which has been running just fine, except for slowing down lately as the XP deteriorated and accumulated viruses and fixes.

So I tried the ubuntu liveCD a couple of days and finally installed a new HDD and installed ubuntu on the new HDD. I put the old XP HDD into a USB box so I could grab data as necessary. That all works fine. I've replaced all the old XP programs with ubuntu/linux equivalents except for one: the HDTV display program for my USB OTA TV (ATSC) stick (but I only need that when traveling).

So everything is pretty good. But then I got the Big Idea of creating a new dual-boot HDD with the old XP and a copy of the ubuntu stuff I've developed. All on one drive so it would go with me whereever I go.

From what I've read it sounds like I must install the XP first so it is on the 1st partition and it owns the boot record (or MBR, whatever) for awhile, at least, until grub messes with things. Then it should be easy to add in ubuntu because that's the way it usually gets installed.

But I don't want to install a new XP, I want to copy the old XP partition entire to the new HDD. It seems to me that MS doesn't provide any way to do that, probably for DRM reasons, and the last time I tackled Norton Ghost it about killed me! 

So I looked around at ubuntu and found "dd" and "pcopy" as candidates to copy a partition from one HDD to another. But "dd" has a bad reputation, and looks doubtful just from the "man" info, so I abandoned it and tried "pcopy".

I put the new HDD in a USB box, ran Gnome Parted to setup 3 partitions on it (27gb for XP, 43gb for ubuntu, and 5gb for swap or whatever), and it all looked good. I was puzzled that I couldn't format the XP partition to NTFS, like the one on the old XP HDD, but I formatted it FaT32 figuring the copy program "pcopy" might set things right (which I have since concluded that it does).

With the old XP USB box in one USB port and the new HDD in another USB port I fired up "pcopy /dev/sdc1 /dev/sdb1" to copy the old XP onto the fresh new partition.

All went well, happily copying 17mb/sec, so that's 60sec for 1gb so it'll take about 25 minutes for the whole partition. But just as it gets toward the end it encounters unrecoverable IO Read errors. And when I kill pcopy with ctl-c there is just gibberish on the new HDD. So I retried several times, maybe allocating more space to the target partition, etc., but no change.

I'm guessing that the old XP has some data errors that pcopy can't handle, probably in the void past real data. As usual.

Has anyone tried this gimmick? Copying an old XP intact to a new partition? Using ubuntu utilities (parted and pcopy or dd)?

Have you had to resort to some XP program to cleanup the old partition?

---

### Post by bliffle on 2007-08-17
Think what I'll try next is to fire up the old XP drive and run "chkdsk" to cleanup the old XP partition. Then I'll retry that copy.

---

### Post by StephUb on 2007-08-17
Do you have a real XP install disk or is that a recovery disk.?
Some laptop have tatoo that restrict the use of the windows sold with it.
Most of the time the tatoo is located in the MBR which means that if you touch the MBR windows won't boot

I am thinking using grub4dos to avoid touching the MBR on my laptop

I might be wrong about the tatoo, i am still learning how it works..

---

### Post by Vadi on 2007-08-17
Best of luck to you! I meanwhile am playing with my VirtualBox... well, trying to get it to boot a fake xp (which I only need to compiling some programs on it).

---

### Post by bliffle on 2007-08-17
> **StephUb said:**
> Do you have a real XP install disk or is that a recovery disk.?
Some laptop have tatoo that restrict the use of the windows sold with it.
Most of the time the tatoo is located in the MBR which means that if you touch the MBR windows won't boot

I am thinking using grub4dos to avoid touching the MBR on my laptop

I might be wrong about the tatoo, i am still learning how it works..

I bought the T40 used about 3 yrs ago with a fresh XP installed. No disks.

---

### Post by Vadi on 2007-08-18
T40's don't come with an xp disk, there's supposed to be a hidden partition that Access IBM would use when you choose to restore the factory defaults (didn't work for me though).

---

### Post by jimbob on 2007-08-18
Has anyone ever seen a hidden partition show up using Gparted?  I would assume it would be indicated by showing "hidden" in the same column as the "boot" flag shows up.

I tried on my laptop to make one of my partitions hidden by setting the flag myself but the box will not allow itself to be checked.  I can toggle the boot flag all I want but not the hidden flag.  I have inquired about this on the Gparted forum but so far no answers.

I also wondered if using fdisk -l in Ubuntu would show it or if the only way to tell would be to notice a gap in consecutive cylinder numbers.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Malvolio on 2007-08-18
I've been wanting to run Windows 'sigh' again but my laptop came with Ubuntu installed.  Is installing Windows on Ubuntu really that much of a bad idea or can it be done without breaking the OSes?

---

### Post by jimbob on 2007-08-18
If I was you I would run Windows as a virtual machine inside Ubuntu.

Google "Virtualbox" and have a look at it.  It is the best of them IMHO.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Vadi on 2007-08-18
I'd recommend using virtualizatoin too (I'm setting mine up at the moment).

---

### Post by hh93 on 2007-08-28
> **whobutdrew said:**
> Unfortunately, I don't have good news for you.  I gave up on the dual-boot scenario and am just running XP on the laptop now.  Ah well.  Dual boot would have been nice, but at least its functioning now.

At least you still have that recovery partition, that was blown away long ago by the friend I inherited this from.

I hope you have better luck than I did!

Hi Drew,

You may want to try Wubi for dual boot ([http://www.download.com/Wubi/3000-2098_4-10689087.html](http://www.download.com/Wubi/3000-2098_4-10689087.html)). It does not neet a new partition; it installs Ubuntu in windows partition. Works great so far.

---

### Post by Vadi on 2007-08-29
How's the disk read/write speed?

I got my VirtualBox set up, and it's running very, very well.

---

### Post by hh93 on 2007-08-29
> **Vadi said:**
> How's the disk read/write speed?

I got my VirtualBox set up, and it's running very, very well.

Wubi? only have praise; the one transfered to real partition is a tad faster and more responsive, for 'daily' use negligible differences tho. Wubi definitely faster than XP for comparable tasks; and that's on a 3yrs old centrino 1500 laptop.

Nop, no complaints.

---

### Post by Vadi on 2007-08-29
Ahh great. I'll recommend it to my friend then, because explaining how to dual-boot over the internet is a daunting task :/

---

### Post by saltfish on 2007-10-26
I was having the same problem of not being able to booting into XP Pro after installing gutsy.  

To solve the problem, you have to install XP first then install gutsy.  When asked to partition the disk choose the option to manually edit the partitions and _**be sure to create a /boot **_ partition of at least 50M where grub can be installed.  You can follow the steps previously outlined in this thread or here [http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-710-gutsy-gibbon-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-710-gutsy-gibbon-and-windows-ntxpvista/).

Just be sure to create a /boot partition of at least 50M for grub.

---

### Post by xAnarChisTx on 2007-11-01
There is also another solution to the problem, especially for Thinkpad users.

IBM Thinkpads has a feature called PreDesktop, which stores the OS image, and for some reason Windows cannot see this at all.  But, Linux is able to, so when it goes to partition the drive, it includes that "hidden" area, and Windows goes ballistic.  

To disable the feature, go into your BIOS, then go Security > PreDesktop > Disable.  Then hit F10, Save and Exit.

I just found this out after I installed Gutsy Gibbon, and now I am more relieved!

---


---
title: "Almost ready for the dual boot plunge"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2010-04-17
I've added another hard drive to my Ubuntu 8.04 machine on which I've installed Windows XP Professional.  I've got XP running just fine, but it's not a dual boot yet.  I disconnected the hard drive that has Ubuntu while doing this.  

Ubuntu was the only OS on this PC previously.  It was installed on the computer's only hard drive, a 250 gig one.  XP is now on the new 1 TB drive.  When I reconnect the Ubuntu hard drive, will Ubuntu or XP sort out the dual boot thing for me?  Or is there something I need to do to make sure this goes smoothly?

---

### Post by texaswriter on 2010-04-17
Tom ZeCat> What you are doing is one way to do it. When you reconnect the hard drive, priority will go to the device which is set to boot first. What you are doing is not technically "dual booting", but you could call it that if you want. 

How I have my dual boot set up is by installing Windows first on a partition that I manually divide in half, leaving the other half unallocated [in Windows]. Windows will install in the other partition as I tell it to and it will also create a small partition for swap space or something [less than a GB]. 

After I have installed Windows, I will jump to a Ubuntu LiveCD and create a partition with the unallocated space. Ubuntu installs in that partition AND recognizes that the other partition has a Windows installation, adding it to the GRUB bootloader. 


What you are doing is akin to my usb flash disk with a full install of Ubuntu on it. As long as the computer knows to look there first, all I have to do is plug it in and reboot. 

I recommend dual booting the way I described I did [or the reverse, though I haven't tested that]. Use the extra hard drive for data storage. You can either split it up into two partitions [one ntfs and one ext2/3/4] if you want extra storage for both, or just one... I personally use my extra hard drive as an NTFS storage space for both [extra hd NOT partitioned].

---

### Post by dominiquec on 2010-04-17
You'll need to install GRUB on your main boot partition in order to recognize both Windows and Ubuntu.

See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

and 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Tom_ZeCat on 2010-04-17
> **dominiquec said:**
> You'll need to install GRUB on your main boot partition in order to recognize both Windows and Ubuntu.

See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

and 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I'll check out that link, thanks.  I do notice when Ubuntu boots up, it says something about Grub, so it may already be installed.  

All I want is for a choice of OSes to present itself when the computer begins its boot so that I pick whether to have Ubuntu or Windows load.  

I've heard of some systems where you can switch back and forth between Ubuntu and Windows.  I don't need to do that just yet.  I'll wait till this PC has more memory.  Right now it just has a gig.  It's capable of holding up to 4 gig.

---

### Post by texaswriter on 2010-04-18
ZeCat> I think the easiest solution would be to install them on one hard drive per my instructions. You can certainly try other things, but this is going to be alot harder. 

As long as the operating systems are on separate hard drives, I don't think you can get them in one grub boot menu without very special configuration. 

If you have MS already installed, resize the hard drive, boot to a livecd and and reinstall Ubuntu. 

My recommendation.

---

### Post by confused57 on 2010-04-18
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by cybrsaylr on 2010-04-18
I've been running dual boot systems with Windows 4 years now and have found them to run trouble free when you add Ubuntu to a HDD that already has Windows on it. I just setup a dual boot of W7 and Karmic for a friend yesterday. I did a clean install of W7 then installed Karmic which went in flawlessly. Both OSs run fine.

---

### Post by Tom_ZeCat on 2010-04-18
> **texaswriter said:**
> ZeCat> I think the easiest solution would be to install them on one hard drive per my instructions. You can certainly try other things, but this is going to be alot harder. 

As long as the operating systems are on separate hard drives, I don't think you can get them in one grub boot menu without very special configuration. 

If you have MS already installed, resize the hard drive, boot to a livecd and and reinstall Ubuntu. 

My recommendation.

I wanted them on separate physical drives to prevent the OSes from messing with one another.  That proved to work well on an old Win 98/Win 2K machine I previously owned.  However, your suggestion is a possibility.  I would partition the 1 TB drive with Partition Magic and install Ubuntu one one of the partitions, then format the other drive and use it for storage.  

However, I've already invested a bunch of time in the separate physical drive approach.  If I can get it to work, it has the advantage of leaving one OS in tact in the event that one of the hard drives crashes.

---

### Post by oldfred on 2010-04-18
I like having an OS on each drive and its boot loader in that drive so I have multiple ways to boot. Ubuntu/grub is good at finding other systems so I set BIOS to boot grub and choose my other systems. I boot the version of grub2 that is in my sdc.

I have three drives and currently 4 operating systems. The grub2 sudo update-grub finds them all (and all versions), so I have to limit menu entries and I modified my menu to suit my system.

If Ubuntu was sda and now it will be sdb you may have to reinstall grub. Most things are based on UUIDs and will still work, but sometimes grub and possibly your settings in fstab may have to be reviewed.

---


---
title: "set up dual boot for ubuntu with el capitan"
date: 2022-07-18
forum: Installation &amp; Upgrades
---

### Post by straitsfan on 2022-07-18
Hello guys.  I wanted to post this just in case, because I don't want to screw up anything.

I have an 11,6 iMac, quad core i7, 16 gb RAM, and want to install ubuntu.  I got the iso on a usb stick, etc, and can choose the EFI boot from the alt key at startup, etc. and I can get to the installation window, but I haven't done this in a long time (when I installed Elementary OS on my dell laptop, I knew how to use Gparted, and it was easy. 

BUT....

I don't want to screw up my el capitan partition.   Can someone point me to a link that talks specifically about setting up an ubuntu partition on Mac OS?  The problem also is that my iMac has a backlight issue and I have to shine a flashlight at the screen to see what's being displayed.   I thought that when I connected my external monitor to the machine that I could do it from there, but all I can get is a desktop/wallpaper type screen with an octopus looking image on it, and I can't see the actual installation widows on the external monitor.  If there's a way that I can see it on the monitor and you know how to do that, I'd appreciate it.

I know that hfs is the file system for apple, and there are two hfs sections (not sure of the right terminology for that).  I simply want to be able to install the ubuntu partiton on the hard drive (yes, it's an old machine), and dual boot depending on what I want to use.

My apologies if my questions are too basic, but I'd like to get this right the first time.  I definitely don't want to accidentally erase the el capitan partition, obviously.  Can I set up the partition for ubuntu directly from the ubuntu installation, or do I have to partition the disk with something like disk utility, etc, and then install ubuntu?  And i'm not sure what options to choose regarding the linux partion (format, etce) if I have to do that. 

Oh, and one more thing -- any recommendations on how big I should make the partition?  It's a 1 TB hard drive.  I was thinking half and half, but since I'm new to Linux and want to eventually switch over once my apples are done and gone (My MB Pro also has backlight issues) I'm not sure exactly how much space to give to Ubuntu.  I'm not sure how much it needs to run efficiently.



Many thanks in advace.  Please feel free to ask for more info if necessary.

---

### Post by grahammechanical on 2022-07-19
Your situation cannot be explained by just one person posting in one post. Please be patient. Others will have to join in.

I am guessing that the "octopus looking image" is in fact a Jellyfish. That would mean that you are trying to install Ubuntu 22.04 (code named Jammy Jellyfish). Knowing what version of Ubuntu is important as improvements bring changes to utilities.

The Ubuntu installer will offer to automatically set up a dual boot. Or, we can do a manual installation (called Something Else by the installer). Doing it through Something Else is more complicated. I have no experience doing a dual boot installation with Mac OS automatic or otherwise.. Others will have to help with that.

I would guess that you should use Mac utilities to shrink the El Capitan partition to create unallocated space for Linux. Test that the Mac OS can still load. Based upon my system with a UEFI motherboard and GPT partition table I have a 537MB partition mounted as a EFI System partition. It is formatted as FAT 32. The Mac OS might already have a EFI system partition that can be used by Ubuntu. The two OS boot files can exist alongside each other.

I also have a partition for Ubuntu formatted as Ext4 and mounted at / or root. The size is up to you. It can be from 30 GB upwards.

I do not have a separate /home partition as my system came pre-installed when I purchased the laptop. Otherwise, I would have a separate /home partition formatted as Ext4 and mounted at /home. The size is again our choice and depends on how much stuff we want to put in there.

As for the problem with the screen I ask can you see the Ubuntu live session? If you can and you are joined to another monitor by HDMI then open system settings>Screen Display>Display mode>Mirror. That should activate the other screen. You will have to do the same thing when you load Ubuntu.

Regards

---

### Post by oldfred on 2022-07-19
This old link shows installing 14.04 on 11.1MacBook Pro.
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Of course do not use obsolete versions, newer should work better. 

A lot of users with Mac seem to use rEFInd. I have used rEFInd for emergency boot on my PC.
rEFInd on newer MAC with Secure Boot
[https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25](https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25)
[https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind](https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind)

[https://florisvanbreugel.wordpress.com/tag/ubuntu-on-mac/](https://florisvanbreugel.wordpress.com/tag/ubuntu-on-mac/)
Ubuntu also does not like to install to external drives correctly.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Some work arounds posted in bug report & you have to manually partition in advance to have an ESP on any drive other than first drive.
If installing to one drive, only use the existing ESP.

---

### Post by straitsfan on 2022-09-05
Hello.  It's been a few weeks.  What I meant to say re: the inability to  see my iMac monitor is that there's a problem with it -- a backlight  issue, ad it goes black after a while, how long it takes to do that  varies.  I can see the screen if I shine a flashlight on it, but what I  meant to say is that when I have the monitor hooked up to it, it still  won't display the iMac screen for some reason, ad I don't know why.   I  have the settings on Mirror, but it just displays the ubuntu jellyfish  image.  The machine is running OS X at this point, and I haven't started  any of the installation process.  Could it be that I have the USB  installation stick mounted onto the iMac, and booting from that?

---

### Post by oldfred on 2022-09-05
Does it have a proprietary nVidia chip/card?
If so you need to use safe boot option and install the proprietary drivers, so it installs the nVidia driver as part of install.
Before that you had to manually add nomodeset boot parameter to use a default video mode.

---


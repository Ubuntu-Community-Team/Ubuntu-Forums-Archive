---
title: "Ubuntu 12.04.1 Won't Get to Install Screen"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by astrostu on 2012-09-12
Hi all, I've searched around for this but didn't know quite what to look for and what I found didn't work ... hopefully it's something simple?

I'm trying to install Ubuntu on a blank partition.  My 11.10 disk works fine in the sense that I boot from it, it shows the keyboard -> person screen, bootup screen, and then login screen.

My 12.04.1 disk shows the keyboard -> person screen for a second, and then a black screen with a blinking cursor and doesn't do anything else.  The disk works fine on a friend's laptop.

The machine is an Intel processor, 64-bit, and it was the i386 image I downloaded.

Thoughts?

---

### Post by 2F4U on 2012-09-13
Did you verify the checksum of the downloaded Ubuntu iso image? Even if it works on another machine doesn't necessarily mean that the image is ok. The hardware specification of the other laptop is probably different, so at least other drivers will be loaded.
If the checksum is correct, did you burn at the lowest possible speed? Not every CD drive behaves exactly as the other and some are a bit picky about the media.

---

### Post by astrostu on 2012-09-13
> **2F4U said:**
> Did you verify the checksum of the downloaded Ubuntu iso image? Even if it works on another machine doesn't necessarily mean that the image is ok. The hardware specification of the other laptop is probably different, so at least other drivers will be loaded.
If the checksum is correct, did you burn at the lowest possible speed? Not every CD drive behaves exactly as the other and some are a bit picky about the media.

Interesting question.  I did not, and on a Mac, I went to check it when I first saw your response and it would not mount on the Mac with the default mounter.  In Disk Utility, it said that it could not verify the disk because there was no checksum information.

I used the torrent version to obtain the file, so just now I've downloaded it from the main server.  Same thing.  However, putting the CD that was burned from the ISO image into the Mac mounts fine and I can see files, so I don't think that basic test of, "it won't mount in Mac" is necessarily valid.

It also loads okay in Windows 7 and the options for install on reboot works.

Thoughts?

---

### Post by Bucky Ball on 2012-09-13
First thought: Download the AMD64 image. You have a 64bit processor.

You don't need to check checksum with torrent. Already done. Best, safest, fastest way to download the ISO. You have more chance of corruption any other way.

So: Start with the basics. Torrent the 64bit ISO of your choice to be certain of the images' integrity, burn the CD/DVD/USB and try again. If you are really unlucky the burn might be corrupt but you can check that as you do it and 'Check the disk for defects'.

---

### Post by varunendra on 2012-09-13
> **Bucky Ball said:**
> First thought: Download the AMD64 image. You have a 64bit processor.

You don't need to check checksum with torrent. Already done. Best, safest, fastest way to download the ISO. You have more chance of corruption any other way.
**+1, **I can't agree more.

Besides, you should also try to boot in safe graphics mode to make sure it is not graphics related issue. To do so :

[LIST]
[*]press any key when the system just starts booting from the cd. This will bring up the advance boot menu
[*]After selecting language, press F6 to pop up "other options" menu
[*]Highlight "nomodeset" and press space to select it.
[*]Press 'Esc' then 'Enter' to boot with that option.
[/LIST]
A silly question though- do you have 1GB RAM or more? Silly because it is 'almost' obvious with a 64bit cpu... but just in case.. :)

---

### Post by astrostu on 2012-09-13
> **varunendra said:**
> [QUOTE=Bucky Ball;12235775]First thought: Download the AMD64 image. You have a 64bit processor.
**+1, **I can't agree more.

Besides, you should also try to boot in safe graphics mode to make sure it is not graphics related issue. To do so :

[LIST]
[*]press any key when the system just starts booting from the cd. This will bring up the advance boot menu
[*]After selecting language, press F6 to pop up "other options" menu
[*]Highlight "nomodeset" and press space to select it.
[*]Press 'Esc' then 'Enter' to boot with that option.
[/LIST]
A silly question though- do you have 1GB RAM or more? Silly because it is 'almost' obvious with a 64bit cpu... but just in case.. :)[/QUOTE]


It's an Intel processor, so I thought AMD64 was for AMD processors ... ?

And, actually, this is what I had done initially, accidentally.  Loading from that CD brings up a black screen with a white text menu of either booting Linux, installing it, or checking the disk.  I try any of the options and the screen just goes black with nothing happening for 10+ minutes.

I have 64 GB of RAM.  I built the computer specifically to run 4 programs for work, and run them well, and one is a RAM hog (was running a process eating up 49 GB of RAM).

Perhaps of interest, with the AMD64 version, the BIOS recognizes it as a UEFI thing it can boot from, but not the Intel version ... but the Intel version actually briefly brings up the purple screen.

With the Intel version, I tried your method of selecting the nomodeset ... and this actually seems to be working.  Will update in a bit with the verdict.

---

### Post by astrostu on 2012-09-13
Okay, so at this point, the Intel version will boot if I use that nomodeset option.  But, it's 32-bit and I do need 64.  So now I'm back to the AMD64 version, but it gets stuck at the "GNU GRUB version 1.99-21ubuntu3.1" menu and any option I select results in a black screen.  I apparently can edit the startup with "e" or "c" but I'm pretty new and don't know what I'm doing.

But, based on [this link](http://askubuntu.com/questions/128128/how-to-boot-without-nomodeset), I added nomodeset after "quiet splash" and hit F10 and it seems to be starting up.

Before going through installation, I'd like to get confirmation from someone that this was the right thing to do, I'm going to be installing a 64-bit version that'll work, and that my graphics card will be somewhat usable?

---

### Post by astrostu on 2012-09-13
Okay, confirmed it's 64-bit with uname -m (x86_64) and in Details (OS type 64-bit), and from what I've been reading, once I install, I can download the latest nvidia drivers and everything'll be good ... right?

---

### Post by astrostu on 2012-09-13
Bah ... went through installation, but now it put in two potential startup disks in the BIOS, and neither of them are booting Linux.

I'm tempted to start over and just install 11 again.

---

### Post by astrostu on 2012-09-13
Finally got it all working.  Here are my notes:


Installing from AMD64 Ubuntu version 12.04.1.  Putting in the disk and selecting it to boot from in the BIOS brings up a black screen with white menu.  Press "e" to edit the startup file and you'll see "set quiet"  add " nomodeset" (with the space).  Press F10 and it should boot up.

Double-clicked on Install on the desktop, selected English.  Checked the option to download updates, but not 3rd party stuff.

From here, it's the Installation Type ... as in where.  The sdd disk is the 128GB SSD.  sdd1 is a 104MB Windows partition (EFI), sdd2 is 134MB with no type, sdd3 was NTFS (the Windows OS), and then there was free space.  Double-click on the free space and a box opened up.  Create a new partition with all of the space and set it to EXT4 type (the default) and set the mount point to "/".

Change "Device for boot loader installation" to /dev/sdd, NOT sdd4.  This puts it on the hard disk, not the partition.

Make sure that the /sdd4 is selected, and press Install Now.  I got an error about not setting swap space, but because I have 64GB of RAM, I dismissed it.  Then did the normal setup while it was installing (time zone, language, account).

After installing, it wanted to reboot, and on reboot, I got a simple purple screen of nothing.  The BIOS showed that it had added not one, but two possible boots.  I don't remember which eventually worked, but in one of them, when I held down the shift key after the BIOS option, it brought up a menu.  Choose to enter in recover mode (I did try running a few fixes but that didn't change anything, then accidentally booted in recovery mode).  Then I went in, checked for updates, and part-way through updating, it notified me there were some proprietary drivers I could activate.  You MUST wait for other updates to finish (apparently).  Restarted.

On restart, got errors saying that it was running in low-graphics mode 'cause it couldn't figure out my input devices, monitor, etc. and I'd have to configure them manually.  Too bad I couldn't click on the "Ok" button.  Restarted, went into the BIOS, and selected the OTHER ubuntu bootup, and this worked.  Makes one understand the appeal of a Mac.  Also on this boot, the graphics were obviously working because it was at native screen resolution.

*****

I guess this thread can be set to [SOLVED].

---

### Post by Bucky Ball on 2012-09-13
Glad you got it all working. Good job. It gets easier and you've learnt something! Please mark as 'solved' from thread tools to help others. ;)

---

### Post by astrostu on 2012-09-15
> **Bucky Ball said:**
> Glad you got it all working. Good job. It gets easier and you've learnt something! Please mark as 'solved' from thread tools to help others. ;)

Ah, didn't know I could mark it as solved.

I will say that this makes me glad I have a Mac as my main machine ... ;)

---


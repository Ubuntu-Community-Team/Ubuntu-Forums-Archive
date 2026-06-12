---
title: "Installation Failure - Gigabyte Z68 Motherboard"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by jacrider on 2011-11-14
All:  I am finally building a new computer.  I have had it post to BIOS, all seems fine ... drives all visible, CPU temp is nice and low, memory all accounted for.

Specs:
  MB - Gigabyte GA Z68XP-UD4
  CPU - i7 2700K
  RAM - Corsair Vengance 8 GB 1600
  SSD's - 2 x OCZ Vertex 3
  Video - EVGA GTX 550 Ti 
   
I have gone in through the BIOS and put the two SSD's into a RAID 0 configuration for my boot drive.  That seems to work.

From there, I go to boot with my Ubuntu 11.10 CD and I see the purple splash screen for a few seconds, then I get a stream of messages, then modprobe seems to be timing out.

I read here that there was some problems with the USB 3.0 controller on the board, so I disabled it within the BIOS.  I also unplugged all other USB devices.

Anyone have any suggestions?  

I will try flashing the latest version of the BIOS on the motherboard. 

All suggestions greatly appreciated!

---

### Post by jacrider on 2011-11-14
I updated to the latest BIOS from Gigabyte.

Still the same problem ... I get to 6.802614

Then the screen shows a udevd[142]: timeout: killing '/sbin/modprobe -bv pci:{then a whole long number} [166]

I should also note that I have tried both 32 and 64 bit versions with similar results.

Again, any help would be appreciated.

---

### Post by jacrider on 2011-11-14
My trouble shooting continues ...

I have tried several things ...

1.  I did a memtest and the system passed without any errors

2.  I disconnected the SSD's and added an old HDD that was running in my old system.  I encountered the same problems.

Next I think I will swap in my old video card and see if that's the problem.

Otherwise, I think I have a motherboard problem.  Although the BIOS flashed without a hitch, there could still be a problem in one of the systems.

Any other suggestions?

---

### Post by jacrider on 2011-11-14
Well ... my new video card (EVGA GTX 550 Ti) seems to have been the culprit.  I swapped in my old GTS 250 card and it fired up fine.  Ubuntu 11.10 x64 is installing as I write this.

I will return it and try another.  Ugh.

My old one is very loud.  The EVGA was very quiet.  I am water-cooling this machine, so I want a very quiet video card.  

Has anyone had success with Ubuntu and a fanless card?  I don't really game.  Just desktop stuff and a movie once in a while.  The card I chose was way beyond my needs, I just heard great things about the quality (and low noise) of EVGA cards.

Thanks.

---

### Post by darkod on 2011-11-14
1. For raid installs you should use the alternate install cd, not the standard desktop cd. You end up with the same, but the installer is text mode, not GUI. However it does have raid support which the standard cd doesn't.

Another thing to consider, if you are not dual booting with windows, software raid seems a preferred choice over bios raid (fakeraid).

2. Lots of nvidia card require a parameter nomodeset to install and boot successfully. When using the desktop cd, hit F6 at the first menu, it should show you advanced options. Look around and select nomodeset. But I'm not sure if this applies to the alternate cd too, and as said above you should use that for raid. It might not apply since the installer is not GUI, but text.

---

### Post by oldfred on 2011-11-14
All these very new systems have both BIOS & UEFI. And often do not make it clear which is in use. The installer may be in either mode. Do you know which it is using?

UEFI is new and works with Windows, but some with grub2 have had issues.

---

### Post by jacrider on 2011-11-14
> **darkod said:**
> 1. For raid installs you should use the alternate install cd, not the standard desktop cd. You end up with the same, but the installer is text mode, not GUI. However it does have raid support which the standard cd doesn't.

Another thing to consider, if you are not dual booting with windows, software raid seems a preferred choice over bios raid (fakeraid).

2. Lots of nvidia card require a parameter nomodeset to install and boot successfully. When using the desktop cd, hit F6 at the first menu, it should show you advanced options. Look around and select nomodeset. But I'm not sure if this applies to the alternate cd too, and as said above you should use that for raid. It might not apply since the installer is not GUI, but text.

You are exactly correct on the first point.  I had trouble with the hardware RAID setup as I couldn't get GRUB to install ... it seems GRUB can't install to a RAID 0.  I don't know about others.  I ended up deleting the RAID and going back to two individual drives.  Then I used the Alternate Install CD and set up my system and swap in two partitions set up as software RAID 0's.  I had to leave a bit of space for the /boot partition on only one drive to allow GRUB to install.  Complicated to set-up, but it is working beautifully.  Very fast having two SATA III SSD's in a RAID 0.  Unbelievable.  Found a great tutorial on Youtube:  [http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)

I will investigate your second recommendation regarding newer NVidia cards.  Sounds very reasonable.  I will have to figure out how to do it now I have the OS installed.

Anyway, many thanks for your comments.  My computer is now back up and running with the new CPU, MB and SSD's and it is unbelievably fast.

Thanks.

---

### Post by ratcheer on 2011-11-14
> **jacrider said:**
> 
Has anyone had success with Ubuntu and a fanless card?

My old Ubuntu machine ran just fine for a year or more with a GT9400 fanless card. Coincidentally, my new PC has a similar motherboard to yours (Gigabyte Z68A something or other). I currently use an ATI 6770 HD card.

Tim

---

### Post by darkod on 2011-11-14
I'm not sure about fakeraid raid0 but yes, for softraid raid0 you need separate /boot partition outside the array. I guess that is because in raid0 the files are split on both drives, and the boot process can't handle that.
If it was raid1 you don't need separate /boot and can have the boot files on your /.

I guess you are aware but I better remind you: with raid0 your data is not protected with redundancy. If one disk goes, all the data is gone.

---

### Post by jacrider on 2011-11-14
Absolutely agree that RAID 0 provides no data back-up or redundancy.

I have two small SSD's for the RAID 0 and that just holds my OS and /home.  I use Back-In-Time to back up /home to USB HDD. I also have a HDD RAID 1 (mirrored) array for larger media data.  

Being somewhat paranoid ... I also use UbuntuOne for a secondary backup of photos and other critical documents.

I like the RAID 0 for performance.

---

### Post by Fraoch on 2011-11-16
> **jacrider said:**
> Has anyone had success with Ubuntu and a fanless card?  I don't really game.  Just desktop stuff and a movie once in a while.  The card I chose was way beyond my needs, I just heard great things about the quality (and low noise) of EVGA cards.

Thanks.

I've been using a Sparkle NVIDIA 9400 GT fanless card for probably going on 2 years now, through several Ubuntu versions.  Sure it's a cheap card but it's noiseless and works for what I use it for.

Do note that a recent install-from-scratch required the 'nomodeset' boot option for the standard graphical installer - otherwise the screen was corrupted.  I thought I would've had to install the 'nouveau' driver after install but the install detected the card and installed the appropriate driver, which was odd because the installer script itself couldn't use the card without the 'nomodeset' option.:rolleyes:

It seems that at any time there's only a limited subset of graphics processors that can be configured for fanless operation, and I currently see the following:

ATI:
5450
3450
6450
4350
6770*
FirePro 2460 (workstation)*

NVIDIA:
8400GS
210
6200
6200 LE
520
430

Most of these are well under $50, with the two asterisked ones notable exceptions.

As for RAID, it seems you've figured it out - Linux requires mdadm from the alternate install CD.  The RAID set in the BIOS usually requires Windows drivers.  Both rely on the OS and main CPU - true hardware RAID can get pretty expensive.

---

### Post by jacrider on 2011-11-17
Thanks for the suggestion of a fanless card.  

I now have my GTX 550 Ti up and running, but a silent card is very interesting.  My power supply is very quiet, the watercooling is almost silent, so the the only real noise is the video card.  Though my EVGA is fairly quiet.  I have always liked their products.

---


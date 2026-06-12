---
title: "New Lucid Installation won't boot"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by hogfan on 2010-08-12
I have installed the minimal installation of Lucid on my Acer Revo 1600 3 times now and the installation succeeds every time.  The when it says remove media and reboot system, it reboots, gets past the BIOS screen and then I just get a solid black screen when a single flashing "_" cursor in the upper left corner of the screen.  

This box was originally running Jaunty and I upgraded to Karmic, and then to Lucid.  However the Lucid upgrade broke some things (like ALSA), so I decided just to start fresh with lucid.  

The behavior described above happened after installing Lucid the first time, then again after I used GPARTED to first wipe all partitions from the disk.  

After the second time, I used a WinPE 2.0 disk and the diskpart utility and did a "clean" on the drive (this is supposed to wipe the MBR).   

After installing for the 3rd time I am getting the same results.  I tried booting into recue mode and re-installing Grub, but no success.

What do I need to do to get my system bootable with Lucid?  I did not have this issue installing Jaunty and Karmic in the past.   I have done everything short of zeroing out the HDD prior to installation.  

Suggestions?

Thanks.

-hogfan

---

### Post by Rubi1200 on 2010-08-12
First, how long did you wait after you saw the blinking cursor before you gave up (and presumably rebooted)? It can take a few minutes sometimes.

Second, what graphics card do you have installed?

Thanks.

---

### Post by hogfan on 2010-08-12
I let it sit there all day yesterday while I was at work for 9 hrs.  Video card is onboard Nvidia ION (Geforce 9400).

-hogfan

---

### Post by Rubi1200 on 2010-08-12
Hi,
not sure what to tell you. I thought it might be a graphics card issue. Did you try updating the drivers for the card?

Other than that, perhaps you want to consider going back to Karmic until either the next version has a solution for you or until someone else has another suggestion.

Sorry I am not able to get you further than this.

Good luck anyway!
:)

---

### Post by hogfan on 2010-08-12
I'm going to give this a try:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Rubi1200 on 2010-08-12
> **hogfan said:**
> I'm going to give this a try:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Ok, sounds like a plan. Let us know what happens please.

---

### Post by MAFoElffen on 2010-08-12
> **hogfan said:**
> I have installed the minimal installation of Lucid on my Acer Revo 1600 3 times now and the installation succeeds every time.  The when it says remove media and reboot system, it reboots, gets past the BIOS screen and then I just get a solid black screen when a single flashing "_" cursor in the upper left corner of the screen.  

This box was originally running Jaunty and I upgraded to Karmic, and then to Lucid.  However the Lucid upgrade broke some things (like ALSA), so I decided just to start fresh with lucid.  

The behavior described above happened after installing Lucid the first time, then again after I used GPARTED to first wipe all partitions from the disk.  

After the second time, I used a WinPE 2.0 disk and the diskpart utility and did a "clean" on the drive (this is supposed to wipe the MBR).   

After installing for the 3rd time I am getting the same results.  I tried booting into recue mode and re-installing Grub, but no success.

What do I need to do to get my system bootable with Lucid?  I did not have this issue installing Jaunty and Karmic in the past.   I have done everything short of zeroing out the HDD prior to installation.  

Suggestions?

Thanks.

-hogfan
Sorry for the delay..  Saw your post as I was going out the door and was hoping someone could get you going.  I just got back home.

So what's going on from your description is that you first wiped your partition table and MBR before you installed Ubuntu... Then after the install said it was "successful." you rebooted.  From your description, you said the computer went through it's BIOS routine, went to a blank screen... the cursor appeared in the upper left of the screen (0,0) and may or may not have dropped down one line (1,0) before it locked up.  So, you "are" locking up while GRUB2 is trying to Boot, before you even get to a a Grub Menu.  That would be before xorg initialises, so it would be before an xorrg or  graphic card/driver problem...  This is why you can't get into GRUB Rescue or the system rescue...  This "has" happened to me before- during Ubuntu 10.04beta. No worry, it's an easy fix.

What I found was wrong when I had the problem (had to research Grub and Grub2) was that I needed to start the first partition "AFTER" the first sector and leave that first sector free/unuseed for GRUB or GRUB2 to install.  You can do a repair on an old complex install (that would take forever to reconstruct) using Gparted, move/resize  the start of the first partion 1 sector back off the start of the device and then reinstall GRUB2.  

Since you did a fresh install (repetitively) and you have a lot of practice on the install process (as I had)-  You might find it easier and faster to create both your ext4 partition and linux swap partition with GParted (keeping in mind to leave that room for GRUB2 to install it's boot), then just do a fresh install using those partitions.

If that was were the cursor was stopping, then this is ilikely was the problem and those instructions should take care of that.  The video card you have is similar to mine.  If it's a "single" Nvidia ION (Geforce 9400) then the generic driver Ubuntu installs for it in the installation process should work... Or the work around you noted should get you passed the graphics init.  I'll let you  in on something- the prefferred/current NVidia Driver (at least for my NVidia Card) is a user install "after" the first reboot.  If you have multi-instances of an NVidia card, let me know... and I'll tell you a work around on how to "get passed" the generic video driver- It has problems with multiple instances of the same card... and will lock up at xorg init.  (After leaving grub... after the kernel boot, during device config, etc.)

Let me know if that makes sense/helped and/or what's going on.  I'm back home now and I'll try to help out..

---

### Post by hogfan on 2010-08-18
Thanks for the detailed reply.  I've been on vacation for the last several days, but sta1rted working on this issue again this evening after reading your suggestion regarding starting the first partition after the first sector.  I wiped the drive and setup my partitions using GParted (left 1Mib) before the first partition.  Then re-installed.  Same issue is still occurring. Bios screen, then just a black screen with cursor at 0,0.  Looks like Lucid doesn't give the option to stick with legacy GRUB.  This is the sixth time I have installed Lucid.  Is there a quick way to just install GRUB and forget about GRUB2?  So far it does not impress.   Thanks.

-hogfan

---

### Post by hogfan on 2010-08-19
Just bumping this post up.       Am I better off just going back and installing Karmic? I don't understand why I am having so many problems getting Lucid to boot.  I am using the mini install because I don't need the GUI, only the base system.

---

### Post by Rubi1200 on 2010-08-19
In my opinion, if Karmic works for you without all these issues you have mentioned then why not use it?

It is supported with updates until April 2011, meaning you will have a stable and secure system.

I think a lot of issues with Lucid are probably teething problems and within the next 6-9 months most, if not all, will be worked out.

Come back to Lucid later and give it another try; that is what I have done for the moment.

Good luck whatever you decide.

:-)

---

### Post by hogfan on 2010-08-19
Well, I may end up going back with Karmic, but then I will just have to upgrade sooner in the future.  The frustrating thing about all of this is that I don't believe this has anything to do with Lucid itself.  I think the entire problem is being caused by the GRUB2 bootloader.   I mean, I can't even get the Grub menu to come up after BIOS at boot.  

I haven't had this many boot problems in the past, even with dual-boot configs.  Very strange.


-hogfan

---


---
title: "New hard drive, unable to boot on CD"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by nostra16 on 2010-03-07
Hello to you all.

I had a little mission this week-end = my girlfriends 250Gb SATA hard drive laptop crashed this week (video card failure), and I wanted to help her by getting all her valuable data on an old Pachard Bell EasyNote laptop I have hanging around.

One big problem : this laptop does not boot on CD drive, nor USB drive, and does not have a Floppy slot. There is an old hard drive with a lot of bad sectors in it, and I have a 80Gb IDE drive I want to put in. 

My tools : a SATA to USB adapter, a IDE to USB adapter, a Ubuntu 9.10 LiveCD, a Windows7-run netbook, and the web.

My goal : to configure the hard drive in some sort for it to install Ubuntu on boot (much like when you buy a laptop : the OS installs on first boot).

I quickly found this to be impossible, as there is no Ubuntu pre-install format available (or that I found). So the next step was to get a complete install on the new hard drive, one way or another.

First I tried cloning the 250SATA drive on the 80GB IDE drive, but this clearly led to an error (Grub error 18. It was looking for a 250Gb drive where I only fed him 80.)

Next step was to get some kind of LiveCD-like boot from the hard drive. This is made possible by using the [UNetBootIn tool]("http://unetbootin.sourceforge.net/#install") and the related [Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive"). I met some problems during the real Ubuntu Install at the point where the laptop tried to format the drive the CD image was on. [This other Ubuntu Guide]("https://help.ubuntu.com/community/Installation/FromLinux") gives a few workarounds and tweaks for that situation, but they didn't solve the issue for me.

Final idea was to Live-CD like boot from the rubbish hard drive and install the system on the new hard drive plugged in through USB. This failed because the computer does not boot LiveCD-like on the old hard drive...

I'm kinda stuck on what to do now. I still don't have a nice boot on the computer (only a Live-CD like obtained with the UNetBootIn tool), and am still not capable of doing a "real" install on the Laptop.

I'm aware that solving the boot-from-cd issue would bring me a faster solution (maybe!), but the idea was to get a hang on this so that I can install Ubuntu on my CD-free netbook soon (Although my netbook might very well boot on USB, but still).

Any ideas, links or anything you can feed me?

My final and last idea is to go buy some kind of adapter that would let me plug the two hard drives into the laptop at the same time, LiveCD-like boot on the new one, install Ubuntu on the old one (connected directly via IDE) and then clone the old one to the new one. But I wish I don't have to go to that extreme ;o)

Writing this I just thought of one thing : I could install Live-CD like Ubuntu on a flash drive, launch it on my netbook and install Ubuntu on the new hard drive connected through USB... Would that work?

Thanks for the brave ones who had the courage to read up to here!

Cheers,

nostra16

---

### Post by C.S.Cameron on 2010-03-07
Once you are booted into the Live USB you should be able to install Ubuntu to any other drive connected to the system.

---

### Post by nostra16 on 2010-03-07
Thanks for tip Cameron. Do you know if installing Ubuntu on a USB-connected hard drive would allow me to boot a computer with that hard drive installed inside the computer? Where would the boot table be written? How do I configure that for sure?

Another failed attempt this evening : I booted another computer on the LiveCD, and installed Ubuntu on the USB hard drive. I was very concerned about any changes I would do to the used computer (I didn't want to install Grub on that borrowed computer), so that may be the mistake.

I did uncheck "install boot loader" from the "Advanced" tab at the end of the Ubuntu config (where you have to confirm all your setup choices, name and such). Did that do the bad?

The error I get is "No boot sector on hard drive" when I try to boot...

The only solution I can think of now is to find a computer that does boot on CD and that can take my IDE hard drive, and install Ubuntu on it... Not really what I hoped for ;)

But just to be sure : is it impossible to find all the files one would have on a fresh hard drive with only Ubuntu installed? Something like a disk image of what one finds when he reboots after install? I will definitively make an image of my drive once I managed to get a working OS on it!

---

### Post by Zimmer on 2010-03-07
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Several links here to ways of installing without CD drive, I think, particularly this:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2010-03-07
I stuck an old laptop drive into an external enclosure and it would boot on every computer I tried it on, not like Windows.

---

### Post by nostra16 on 2010-03-08
Thanks for the links Zimmer.

Unfortunately the laptop does not boot on USB (it's a 7-year old Packard Bell EasyNote), and the other methods (InstallFromCDImage and InstallOnExternalDrive) did not do the trick for me.

Does anyone know if it's possible to install on external hard drive AND install the GRUB on the external drive as well, thus making no change at all on the internal drive of the laptop used to make this install?

---

### Post by Zimmer on 2010-03-08
> **nostra16 said:**
> Thanks for the links Zimmer.

Unfortunately the laptop does not boot on USB (it's a 7-year old Packard Bell EasyNote), and the other methods (InstallFromCDImage and InstallOnExternalDrive) did not do the trick for me.

Does anyone know if it's possible to install on external hard drive AND install the GRUB on the external drive as well, thus making no change at all on the internal drive of the laptop used to make this install?
Logically it should do what you tell it to.. :) ie, if you are installing GRUB , GRUB asks where to go , and if you tell it the MBR of the disk you are installing to then that is where it should end up , not the MBR of any other attached disk..
EDIT: CAUTION!
BUT, further reading of the way the Ubuntu installer treats the GRUB installation makes me think it will ask if you want to install GRUB to the MBR of your FIRST disk (which will not be the external one!!! you will need to find out how to install the GRUB bit to the MBR of the external disk.. I suppose disconnecting the internal HDD before you started would be AN option....)

The lack of external boot options seriously limits your ability to recover any errors re grub or any other system for that matter. 

On the positive side, when my wife's system 's Motherboard died last year (and she wanted her XP install ) I bought a laptop and swapped the HD from her system into my SFF machine, and put MY old HD into a usb enclosure..and yep, it boots the old system via usb to the laptop.. no mods required , and the XP system disk behaved in its new home in the SFF...   

I would be attempting to use a Computer with a CD drive (maybe use the Alternate Ubuntu disk) and install to the new drive attached via USB and be certain that when I installed grub it was to the EXTERNAL drive MBR (it is possible to back up an MBR in case you erase the one on the host computer...
[http://members.iinet.net.au/~herman546/p13.html#mbr_dd](http://members.iinet.net.au/~herman546/p13.html#mbr_dd)  )
 then put the drive into the laptop (and cross fingers..)

---

### Post by JayLFC on 2010-03-08
I have been in a similar situation before, I downloaded VMware Workstation, gave it access to the full physical disk, mounted the iso and just installed. Then put the drive back into the laptop and it was good to go.

---

### Post by nostra16 on 2010-03-08
Thanks a lot for the ideas Zimmer. I will deferentially try that tomorrow, with the internal drive disconnected, so no harm can be done. That out to do it...

JayLFC, I haven't hear about the VMWare program. I will check that out (regardless of the outcome with Zimmers idea, so I know a few ways of solving the problem. It can always help ;o)

Thanks a lot for your ideas!

---

### Post by lavinog on 2010-03-08
Any reason why it wont boot to cd?
Seems like that should be a fundamental feature.
Have you checked the boot order in BIOS?...many hp/compaqs offer a way to choose what to boot by pressing esc or f12 during the boot logo.

I did come across a link that shows how to put a live cd on a hardrive partition so you can boot off of the hardrive to install ubuntu on itself.
edit: found link from above post:[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by aceracer24 on 2010-03-08
> **lavinog said:**
> Any reason why it wont boot to cd?
Seems like that should be a fundamental feature.
Have you checked the boot order in BIOS?...many hp/compaqs offer a way to choose what to boot by pressing esc or f12 during the boot logo.

I did come across a link that shows how to put a live cd on a hardrive partition so you can boot off of the hardrive to install ubuntu on itself.
edit: found link from above post:[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

My sons computer is giving me fits of rage as well due to the computer not letting the cd boot. I know for a fact that the cd is bootable as I used it for my daughters PC. I know for a fact that the BIOS is set correctly to boot from the cd-rom before any other device. 

When the cd is put into the cd-rom, the light blinks sparatically for a very long time, like it can't read the disk. As the boot process continues, it makes it to the CD-rom and a message says "boot from cd-rom" but it doesn't ever come up with "press any key to continue to boot from cd-rom" and yes I have also tried just pushing buttons in case the message is just not seen. As I said, the light just sparatically flashes off and on rapidly. Finally it just fails and moves on to the hard drive. In windows the disk shows up as blank but also acts like it can't read the cd very well and takes a long time to pop up asking if I want to write something to the blank cd...... 

To make matters worse, this motherboard supposedly supports booting from a USB but no matter what I can not get it to see the USB flash drive. I have ready every how-to specific to my motherboard (Asus A7N8X Deluxe). On a side note, I had problems installing Vista on this computer as well previously.

---

### Post by lavinog on 2010-03-08
> **aceracer24 said:**
> My sons computer is giving me fits of rage as well due to the computer not letting the cd boot. I know for a fact that the cd is bootable as I used it for my daughters PC. I know for a fact that the BIOS is set correctly to boot from the cd-rom before any other device. 

When the cd is put into the cd-rom, the light blinks sparatically for a very long time, like it can't read the disk. As the boot process continues, it makes it to the CD-rom and a message says "boot from cd-rom" but it doesn't ever come up with "press any key to continue to boot from cd-rom" and yes I have also tried just pushing buttons in case the message is just not seen. As I said, the light just sparatically flashes off and on rapidly. Finally it just fails and moves on to the hard drive. In windows the disk shows up as blank but also acts like it can't read the cd very well and takes a long time to pop up asking if I want to write something to the blank cd...... 

To make matters worse, this motherboard supposedly supports booting from a USB but no matter what I can not get it to see the USB flash drive. I have ready every how-to specific to my motherboard (Asus A7N8X Deluxe). On a side note, I had problems installing Vista on this computer as well previously.

Your issue sounds like the cd drive is failing.  I typically do not see cd/dvd drives lasting much more than 3 years.  Even if it seems like it works, it is still a mechanical device with limited tolerances.  You can usually find new drives for about $20 on newegg.com

You could also try a cd cleaner (it's a disk with a brush on the bottom)...results may vary.

---

### Post by aceracer24 on 2010-03-09
> **lavinog said:**
> Your issue sounds like the cd drive is failing.  I typically do not see cd/dvd drives lasting much more than 3 years.  Even if it seems like it works, it is still a mechanical device with limited tolerances.  You can usually find new drives for about $20 on newegg.com

You could also try a cd cleaner (it's a disk with a brush on the bottom)...results may vary.

This cd-rom really isn't that old but it is on my sons computer and he has a way of destroying things that most people can't. I tried attaching my sata cd-rom and that worked but the Ubuntu install errored out sometime during the partitioning phase and I didn't have time to try it again.

---


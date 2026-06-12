---
title: "Booting Problems - Multiple HDD's - &quot;Grub Loading Stage2&quot; reboot loop"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by KarlOng on 2006-08-21
I have the following system:
A8N32-SLI Deluxe + AMD64x2 4400+

I have 4 hard drives:
Primary IDE => 120GB Seagate
Secondary IDE => 30GB Maxtor
Primary SATA => 74GB WD Raptor
Secondary SATA => 320GB WD

I'm trying to install onto the 30GB Maxtor.  My XP OS is on the Raptor, all my files are on the 320GB WD, and I use the Seagate as a backup drive.

I've tried installing Ubuntu 6.06 (64bit edition) multiple times before only to give up in frustration.  The install CD (mailed by Ubuntu - official CD) hangs most of the time.

I've finally disabled all my drives except the Maxtor via BIOS settings, and have relatively easily installed Ubuntu on it.  I installed by booting into the Live CD, and clicking on the install Icon.  After reformatting and installing onto the Maxtor, I follow the onscreen instructions and reboot.

I end up going into a reboot loop, with Ubuntu displaying "Grub Loading Stage2" before it goes dead and reboots.

I just want to get Ubuntu to boot properly.  I don't even want to mess around with bootloaders and Grub on my MBR right now.  During boot, I can press F8 and my BIOS will ask me which device to boot from.  I just want the Maxtor to boot up when I select it.  Does anyone know what's wrong?  I'll need step by step instructions as I'm a Linux newbie.

Thanks very much in advance.

---

### Post by amohanty on 2006-08-21
First a couple of things:
1. Try disabling all the HDDs except the maxtor.
2. *Then* install ubuntu on it.
3. Let grub install in the MBR. Now to get things straight, the MBR is not unique to a computer, its unique to a HDD (usually). Usually its the first sector on a HDD, so if you install it on the MBR, it will install onto the MBR of the **Maxtor drive**.   Now I cannot say for sure if it will work since the drive is on the secondary, but in theory it shoudl be fine.
4. Now try and reboot, with only the maxtor enabled and see if it works.

HTH
AM

---

### Post by KarlOng on 2006-08-21
Thanks - When I installed, I disabled all the drives except for the Maxtor.  The Ubuntu install did not give me an option of which drive to install GRUB on.  Basically, I was prompted to choose my name and password, my time zone, then was given a list of 4 drives to install on (Ubuntu seems to still detect the 4 drives even when they are disabled in BIOS).  I chose the Maxtor.  There were no other prompts after that until the CD was ejected and I was asked to reboot.  Ubuntu did not detect that WindowsXP was installed on another drive and I was not asked if I wanted to install the bootloader on the MBR of my XP disk.

My only other hardware option is to physically disconnect all my other drives, but Ubuntu may fail again once I reconnect them.

Any software solutions?

Boot into Live CD, mount the Maxtor, edit the menu.lst?
Can you tell me how to edit Grub to refer to the Maxtor?
Is the slave on my primary IDE (hd1,0)?

Thanks again.

---

### Post by amohanty on 2006-08-21
Ok:

Boot into live cd.
Mount /boot or / (if you only have one partition)
Post the contents of: **/boot/grub/devices.map**

AM

---

### Post by KarlOng on 2006-08-21
Very strange.  Installed successfully and booted with the Live CD again to browse my system.  I can go into the /Boot directory, but there is no Grub subfolder.  6.06 64bit installation must have bypassed the Grub installation.

Can you tell me how to get into the "Rescue CD" mode of 6.06 so that I can manually install Grub or Lilo?

Thanks

---

### Post by confused57 on 2006-08-21
Here's a "howto" for installing grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Read the reply by 5-HT for selecting which drive & partition to install grub.

The Dapper alternate cd gives you the option of where to install grub, however, the Desktop Live CD doesn't.
Here's an excellent tutorial for downloading and burning an iso:
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

---

### Post by KarlOng on 2006-08-22
Thanks so very much for that first link.  It got me past my /grub directory being missing.  And the instructions were pretty good, hard to get more step-by-step than that.

My Live CD keeps stalling on "Mounting root file system..." and I just keep rebooting and rebooting until it finally takes for no reason.

So after I ripped out all my HDD's except for the Maxtor, and followed the instructions for loading the /grub manually from the Live CD - now when I reboot, I'm stuck on "Mounting root file system..." again.

To reiterate, my CD is no longer in the drive and I'm booting off the HDD now.  Why is it still stalling on "Mounting root file system"?

Is it due to USB devices?  I have a USB mouse, keyboard, camera, and my monitor has built-in media card reader that uses USB (as well as a USB hub - it's a Dell)

Thanks

---

### Post by KarlOng on 2006-08-22
I think it was caused by USB devices.  I unplugged all my USB devices, and my mouse, used a PS/2 adapter for my USB keyboard, and it finally got past the "Mounting root file system..." stall.

I'm now in Ubuntu and installing the updates.  Hopefully when I reinstall my HDD's, I won't get any problems.

Thanks for all the help, you guys are great.  If you can help me (and other people) get past the USB issue, that would be fantastic.

---


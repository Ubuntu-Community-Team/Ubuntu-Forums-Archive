---
title: "Not happy with Ubuntu, Grub problems?."
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by gorillamotors on 2010-07-23
I've tried installing Ubuntu for the last 2 days v8, 9, and 10 in 32 bit, 8, 9, and 10 in 32 bit using alternate disk, 8, 9, and 10 in 64 bit, and 8, 9, and 10 in 64 bit using the alternate disk. It finishes installation but NONE will boot up. ZERO of them. Just keeps getting a flashing curser or black and white lines across my monitor.
 
My system is an ASUS Rampage 3 Extreme, 24GB Corsair Dominator RAM, Intel 980X chip, 6TB hard disks, BFG 7800GT OC video card, 24" Sceptre monitor.
 
I thought I would give linux a try BUT!!!! I never have had this problem with any version of Windows. I guess I will stick with windows.
 
Jim

---

### Post by CharlesA on 2010-07-23
Sounds like a rant, rather then a request for help.

Does recovery mode display any errors?

---

### Post by gorillamotors on 2010-07-23
Nothing comes up at all. Nothing works.

---

### Post by CharlesA on 2010-07-23
Does the same thing happen when you boot off a livecd?

---

### Post by uRock on 2010-07-23
How big are the partitions you are setting up. And what format, ie, EXT2, EXT3, EXT4?

---

### Post by gorillamotors on 2010-07-23
Yes

---

### Post by Rubi1200 on 2010-07-23
Sorry to ask such an obvious question, but did you remove the installation CD when you finished? (It happens!)

Next question: how many HDDs do you have installed and where did you try and install the bootloader?

---

### Post by Rubi1200 on 2010-07-23
> **gorillamotors said:**
> Yes

Yes to what? The question about the LiveCD?

Sounds like it might be a graphics issue more than anything else.

---

### Post by kaldor on 2010-07-23
I guess Linux sucks because one relatively glitchy distro doesn't work as expected eh? ;)

Really though, maybe you should post your problems somewhere. Sounds like a hardware problem.

Try another distro (check my sig) and see if they have the same issues.

---

### Post by QIII on 2010-07-23
The importance of the LiveCD is whether or not you can run a live session with it.

Can you do that?

What you have is almost certainly a driver or hardware issue with your graphics card.  It is not a Linux issue per se.  It is entirely possible that NVIDIA, as hard as they try, has not produced a unit that is entirely compatible with Linux or with a particular distribution.  Remember that OEMs make their hardware compatible with OSs, not the other way around.  NVIDIA is a great company and has been providing support for Linux for years.  But you can imagine the difficulty of trying to make sure that their hardware works every time with every combination of Linux distributions.  This is not a homogeneous environment where OEMs have a strict standard they have to follow to get approval to call their products compatible with Linux.  Also, bear in mind that Windows does not support your hardware.  Microsoft makes no effort to accommodate your hardware.  It is incumbent on the OEM to design hardware and drivers to work with Windows.  The OEM manufacturers make the drivers available to Microsoft for inclusion in their driver base.  Microsoft does not write the drivers.   If you look at the box your card came in, it will not say "Supported by Windows."  It may say "Designed for Windows."

This may be an upstream question to the NVIDIA community.  I am absolutely certain NVIDIA will want to hear that you are having problems.  They are committed to Linux, even if they aren't a member of the Linux Foundation.

Clearly some of us are able to use Ubuntu.  If you want to stick with Windows, that is the beauty of choice.  Use what works for you.  That's the point.  Just don't assume that Linux doesn't work based on a sample size of one machine.

---

### Post by DethFiesta on 2010-07-23
I am having this very same problem!

I just installed Ubuntu 10.04 from a Live USB.  Booting to the LiveUSB worked fine, no graphics issues, all 4 attached HDDs were recognized and mounted without issue.

I formated one of the HDDs, a 2TB HDD in EXT4 format, then chose to start the installation, where I chose "erase and use whole disk" on that same HDD.  Installation appeared to have been successful.  

Upon rebooting after install I removed the USB and entered BIOS, where I made the disk I installed Ubuntu the first boot device.  Upon leaving BIOS the machine reboots.  I gets through post and then....just a blank cursor.  I left it for minutes and nothing happened.  I reboot and just get the same.

I have 4 HDDs attached to this system: all are EXT4.  3 are 1.5 TB and have existing data from an different Ubuntu 10.04 machine.   The other 1 is 2 TB and is blank except for what the Ubuntu installer has placed on it.

My machine:

ASUS M2N68-AM PLUS 
AMD Sempron 140 single core 2.7 GHz
2 GB DDR2 800
4 HDD
No optical drive

User reviews on Newegg indicate that other users have successfully installed Ubuntu 10.04. 9.10 and 9.04 on this Mobo.  One of the main reasons I bought it.

Interesting Side Note: I bought this Mobo and Proc because my previous machine was an Intel Atom running Ubuntu 10.04 with these same HDDs but booting from an Intel SSD.  After a month or so of use, I hit the reboot button and it never came back...just this mysterious blinking cursor.  Couldn't even boot to Live environment from the USB. 

What is going on here?  I love Ubuntu and am dying without it! Please help if you can! I'm happy to provide any info.

-DF

---

### Post by amsterdamharu on 2010-07-24
@DethFiesta
Looks like a bios setting or grub problem.
If you can boot off a live cd/usb can you post the output of the boot info script?:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
You might try re-installing grub2 from a liveCD:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

@gorillamotors
Do you get a grub menu? If so then you should be able to choose a recovery mode. In that mode there used to be an option to fix X.
Another thing you can try is to edit the /boot/grub/grub.cfg using the liveCD and add xforcevesa acpi=off at the end of the line:
linux    /boot/vmlinuz-.....
To edit that file you need to:
Mount the partition that ubuntu is on or the partition that boot files are on (depending on your installation). Open the filebrowser from the liveCD. On the left side there should be a panel called places, it usually has your harddisks partitions, they are called ".. GB Filesystem". Just click on that and you'll see the content of that partition on the right. Look for /boot/grub/grub.cfg
To edit this file you need to be root, press alt + F2 => type "gksu nautilus", this brings up the filebrowser as root (super user) so be careful. In the left pane there are some items that have random numbers and letters as a name, click on those until you see the boot directory in your right pane. Then go to /boot/grub/grub.cfg and right click this and choose "open with gedit"

---


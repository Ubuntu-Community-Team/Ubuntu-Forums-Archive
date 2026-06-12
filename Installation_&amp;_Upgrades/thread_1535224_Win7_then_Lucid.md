---
title: "Win7 then Lucid???"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2010-07-20
Hello, brand new computer, AMD64 Phenom-II hexacore, Radian Graphic card. I have to tiptoe around OEM Win7 and a hardware warranty (and keep my spouse happy, can't look like an idiot).

The LiveCD 10.04 Lucid-64 Desktop does boot. Checking System->Administration->System Monitor [Resources] and whoa! That shows 6 CPU icons with 4 cores showing a load from 1% to 4.5%. So, I gotta have Lucid, just to know when the cores are working.

My question:  Is there anything different about installation with Win7 already installed? My online research came back with 'you need the Original MS install discs if things don't work out' and / or 'after Ubuntu installs go back and repair the Windows file system.'

Any experiences like this? Can I do a normal Ubuntu install and come up with a dual boot?

---

### Post by lechien73 on 2010-07-20
You may have to restore the Windows 7 bootloader after the installation, instructions are provided at this link:

[http://uri.tl/8](http://uri.tl/8)

You will have to resize your Windows 7 partition if you want to have Ubuntu running on the same hard disk. This link should help you with any resizing issues:

[http://uri.tl/b](http://uri.tl/b)

Hope this helps. For what it's worth, when I first installed Ubuntu 9.04 on this laptop, I resized my Vista partition using GParted Live and had no problems.

Enjoy :)

---

### Post by Mark Phelps on 2010-07-21
> **Unterseeboot_234 said:**
> ... My question:  Is there anything different about installation with Win7 already installed? 
Yes ... two things:

1) Shrinkage -- with Win7 preinstalled, you should NOT allow the Ubuntu installer to shrink the Win7 OS partition.  Doing so runs the risk of corrupting your Win7 install and rendering it unbootable.  Instead, use the Win7 Disk Management utility to do the shrinkage.  Leave the resulting free space as unallocated.

2) Repair -- Use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in handy later should you need to repair or restore the Win7 boot loader.

---

### Post by spydeyrch on 2010-07-21
One other thing, if you want to make it simple for the future, is get a second hard disk for ubuntu. It doesn't have to be big in size. Anything from 250 - 500 GB is what I use.

The reason why I say get a second HDD is because you can install ubuntu on it without it effecting your win 7 drive's MBR and you won't need to repair your win7 drive at all. You won't have to shrink your win7 partition and the two can play nicely together.

It might be a little complicated for some people to initially setup this way, but the end result, in my opinion, is better. Better to get the complicated things out of the way now and have it easy later on than do it easy now and then have complicated problems later on.

Just my two thoughts. I have my system setup this way with a triple-boot: Win7 Pro x64, Mint9 x64, and Ubuntu 10.04 x64.  If at anytime one of the drives fails, even if it is the primary drive, I just switch the primary drive to one of the others and viola! I am up and booting again. ;)

-------

To answer your question, I think that Mark Phelps stated it  perfectly and clearly and lechien73 gave you some good links in case you need/want to go that route.

-------

Let me know if you would like more details about setting up a dual drive system. It is really quite easy. Oh, and I am assuming that this is a desktop and not a laptop.

-Spydey :KS

---

### Post by hardyn on 2010-07-21
spydey:

then you are configuring the boot drive on startup? (eg. pressing esc. then choosing hdd1?)

if not you are still placing grub on hdd0 and will be affecting the MBR of the windows drive.  Just curious.

---

### Post by hardyn on 2010-07-21
> **Unterseeboot_234 said:**
> Hello, brand new computer, AMD64 Phenom-II hexacore, Radian Graphic card. I have to tiptoe around OEM Win7 

Are we still having to deal with hardware manufacturers not honoring warranty on OSs other than windows?

---

### Post by spydeyrch on 2010-07-21
> **hardyn said:**
> spydey:

then you are configuring the boot drive on startup? (eg. pressing esc. then choosing hdd1?)

if not you are still placing grub on hdd0 and will be affecting the MBR of the windows drive.  Just curious.

No, I am not pressing the boot menu key (F8 in my case) to choose which drive to boot from. Although I did for a while. So I decided to try a little experiment and see what would happen if I used separate drives. And it worked!

This is how I did it. I will go step by step using the OP's setup, assuming it is a desktop and not a laptop, as an example. For my personal setup, I have one extra HDD because of one extra OS. These are going to be very basic steps so if more detail is wanted/needed, just let me know.

Key:
Windows HDD = HDD1
Ubuntu HDD = HDD2
Disconnect HDD = disconnect power or/and data from HDD.

------

1.) Power off the machine. Disconnect the power cable or flip the switch to the 0 (zero) position (off) if your PSU has a power switch on it.

2.) Disconnect HDD1

3.) Connect HDD2

4.) Install Ubuntu 10.04 to HDD2. Run any updates etc as needed/wanted. Install any programs as wanted/needed.

5.) Power off the machine. Disconnec the power cable or flip the switch to the 0 (zero) position (off) if your PSU has a power switch on it.

6.) Connect HDD1.

7.) Power on the machine and enter into the BIOS setup.

8.) via the appropriate options in the BIOS setup, make sure that HDD2 is your primary boot HDD. You can still have any ODD and/or USB drives be first, second, third, etc., in your boot sequence as long as the HDD that you boot from in that sequence is HDD2 (the one with ubuntu installed on it). Once this is accomplished, make sure you save the settings.

9.) Reboot the machine.

10.) Your GRUB boot menu should eventually come up. You should only see the typical options in GRUB and not (with emphasis) see your Win7 OS ...... yet. Select the top option of booting into ubuntu.

11.) Once you have logged into your desktop, open up a terminal and type in the following:

```

sudo update-grub2

```when it asks for your password, it is your user account password. As you type in your password, you won't see any characters show up. They are masked. So you need to make sure that you type in correctly your password.

This then will update your GRUB boot menu and add Win7 to it without messing up the MBR (at least in the several times that I have done it, it hasn't messed up my MBR on my Win7 drive)

12.) Once done, reboot your machine. Once your GRUB menu comes up, make sure that Win7 is in the list and select it. You will typically only have around 10 seconds to select an option.

13.) Win 7 should come up just fine. :)

14.) Now reboot again and select Ubuntu. It should come up just fine.

Congrats, you are done.

------------

What this allows you to do is keep each OS's own boot menu on its drive and not mess with the other drives. If everything goes as planned, you should have two OSes on one system and if one of your drives fails, you can still boot into the other one. For example, a few weeks ago my Mint8 (8 at the time but now 9) drive wigged out on my while I was installing Mint9. Luckily I had done the above and so even though I didn't have my primary drive, the mint one, in a bootable state at that moment, I just connect my Win7 drive and viola! I was up and booting win7 without a dependency on GRUB to do so. The Win7 boot menu was still intact. I also did it with my ubuntu drive. So no mater what drive is taken out and moved and added, I will always have a drive that is bootable (if not corrupt, meaning in a normal state).

One quick note, if your drives/connections are SATA and you change the order of the physical connections, you will need to update your BIOS to select the correct HDD to boot to GRUB. If you select the primary to be Win7, you won't be able to select Ubuntu to boot into. But if you have your primary drive be the HDD with GRUB, then you can boot both Ubuntu and Win7. ;)

Also, if the physical connection order changes, you will need to run that code from above:

```

sudo update-grub2

```in order to update GRUB to point to the correct location of your Win7 drive.

Hopefully that helps and if for some strange reason your win7 drive's boot menu/MBR does get messed up, you have those links from the previous posts to help fix it. :D

Let me know if you have any questions or need more detail.  I have done this several times and haven't ever had any problems as of yet.

-Spydey :KS

---

### Post by Unterseeboot_234 on 2010-07-24
OK, I have been sweating this one. I was worried about the warranty of new hardware. So I did get me a new hard drive. The new hard drives use S-ATA cables. Makes snapping in a hard drive about like an external USB plug-in. Very easy.

I disconnected the cables from SATA-a with the Win7 to power and I/O SATA-b. I let Ubuntu LiveCD do an automatic install. Made sure that was working, with all the updates. Shutdown. Connect SATA-a and make sure Win7 isn't trying to wimp out and run. OK. Shutdown. Connected both drives. 

Only Win7 boots. Win7 does not see the 2nd drive. I can reboot, go into BIOS and point to the drive I want. Checking these Ubuntu forums, I sudo update-grub while running Ubuntu desktop. Reboot and I can select boot into Win7 or Ubuntu 10.04.

I think I will have to edit grub.conf because the wife wants Win7 to autoload in the morning and go seek her company's web site.

There is some tweaking to do in Ubuntu, but really this is the easiest and least-worry method to keep OEM Win7.

A word about your OEM Windoze... Dell Computers will deliver a Linux box, but they are about the only mass manufacturer that will do so. I like a German computer mfg. company because of their extreme quality. Terra IT will be lenient about adding the 2nd hard drive to my new box. I would be extract my 2nd drive to ship a non-functioning computer back for warranty. If I blow WIN, ... no. Terra IT has to buy a Genuine Bill OEM sticker with a serial. Terra IT would only guarantee their product that ran OEM SN xxx..

OK. I wasted 2 days trying to network Ubuntu 9.10 to Win7. I learned Win7 blames the public for not networking. The public is learning they cannot plug-n-play with Win7 anymore. XP and Vista cannot network with Win7

Win7 has changed the metaphor for 'folder' into 'library'. Win7 has two shells, a moat, and two more shells before you can see the file system AND you can't cross that moat via a network.

I'll leave this thread open. I don't know whether to make a FAT32 partition on the Win7 SATA or the Ubuntu SATA. If I FAT32 on the Ubuntu SATA, while Win7 see it??? After I solve that, I'll change this thread to SOLVED.

---

### Post by Mark Phelps on 2010-07-24
> **Unterseeboot_234 said:**
>  XP and Vista cannot network with Win7
Not true!  I have XP machines that network with Win7 machines just fine.  Don't generalize your single situation to describe everyone else!

> Win7 has changed the metaphor for 'folder' into 'library'.
Again, not true. Libraries provide the ability to include folders from different machines into a single folder. That allows you to have both local folders, and folders from networked machines, all contained in a single "library". I know it works because I have local Win7 folders and shared folders from an XP machine all contained in individual libraries. The MS Library is an extension of the folder concept, not a replacement. 

>  AND you can't cross that moat via a network.
Again ... not true!

What Win7 DID do, is to create something called Homegroups.  And it that case, you are correct -- Homegroups do NOT work with anything else, including XP and Vista.

---

### Post by d3v1150m471c on 2010-07-24
just slap ubuntu on an external until your warranty runs out. yes, it will boot/run from a usb external.

---

### Post by Unterseeboot_234 on 2010-07-25
Anyway, I am quoting right off Windows 7 Forum Answers. Win7 does NOT share volumes (partitions). Which is fine. Stay that way. What I want is a location to copy files FROM Win7 and see those files in any flavor whatsoever of Linux (I prefer Ubuntu).

What was a hack four months ago that worked in Win7 networking does NOT work today and this affects some early-bird devotees of Win7 (RC1) that allowed an upgrade. Some upgraded RC1 is equivalent to OEM store-bought, but not all versions of Win7 are equal.

edit: =====
I was using a Microsoft Knowledge article showing Ubuntu 7.10 <==> Win7 RC1. That does not work. This does work

**[File Share Wizard -- win 7]("http://www.7tutorials.com/share-libraries-or-folders-using-sharing-wizard")**

There is links also that show you MUST edit the samba config file to join the Workgroup defined-name on the Win7 box

**[edit Samba .config]("http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows")**
reboot or restart samba, make sure you have shared with all the correct options on Win7.

Works good. Used ubuntu on both my boxes, and used dvbackup to firewire the Win7 install onto a dv-tape. I'm into tweaking the software(s) now for my new dual-boot AMD-64-Phenom x6.

Compare the AMD64 Athlon (single core) running Ubuntu 9.10 with the AMD64 Phenom running Ubuntu 10.04??? The Athlon is faster slamming through various tasks, reboots, and configures. The Phenom downloads files off the web at a consistent rate, 10-16bps faster is the only noticeable difference. A reboot on the Phenom is costly because Linux configs a kernel for each of the 6 cores, Win7 does not. I will have to render some video on the Phenom to see if I gain speed (and for that, I need software that I build from source).

Win7 DOES change the folder metaphor. From a programming viewpoint, this change will take some comprehension.

---


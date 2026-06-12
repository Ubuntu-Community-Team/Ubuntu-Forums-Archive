---
title: "Getting “Unable to find a medium containing a live file system” when installing 10.10"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by pixel4e on 2011-02-22
I got this error while trying to install ubuntu 10.10 from a bootable USB stick on to Sony Vaio P series laptop. The disk boots into the language and installation type screen. After that it goes through the splash and pulls up this error:

> BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

After getting this error the installation fails to start.

I have used the same USB stick on some other laptops and the installation started as usual. Any help will be appreciated.

My installation is i386 and my machine is Vaio P VGN-P610.

I've tried every possible thing:

Bios: [enable boot external]

Boot order: [external] [hard drive] [network boot]

Tried 2 different USB drives

Tried 2 different external CD drives

Tried 6 different downloads of both the desktop and netbook remix.

All downloads were checked with MD5SUM.

Ubuntu Desktop 9.10 installs properly in every version and from every source.

I only have two USB ports on the Vaio and I've tried both of them. Alternate install would work if I could connect to the net over wireless (no ethernet).

Getting reaaaally frustrated.:confused:

---

### Post by pixel4e on 2011-02-22
Does anybody have any ideas?

---

### Post by mobabur94 on 2011-02-22
i had the same problem. i didnt really fix it, i just installed onto a partition through wubi in xp. then i converted the wubi install to a full install on another partition. after that i booted into xp, uninstalled wubi and formatted the wubi partition. since then i cant do anything at all. i get a no partition found error and tgen something to do with grub rescue when i try to boot. i tried booting on a live cd but my hard drive doesnt get detected just like at the start. i get a no filesystem found error on most of my live cds but others just wont even boot. windows 7 and xp cds dont boot either. im using my ipod touch right now and i hate my life and my fingers are tired

i think linux hates my hard drive and now so does windows. i think the reason windows setup doesnt boot is because i have three partitions that arent all ntfs: main xp ntfs, wubi ntfs, and full ubuntu ext4. im not sure though. im thinking of putting it in my bros comp and formatting it completely to just one partition. maybe then ubuntu will work but i doubt it.

---

### Post by Tybion on 2011-09-07
I was getting this exact message when trying to run the installation from a hard disk partition.  The problem was that I had not copied the hidden '.disk' folder to the hard drive partition.  After I copied the .disk folder and contents, the problem was immediately fixed.

---

### Post by Hakunka-Matata on 2011-09-07
> **pixel4e said:**
> I got this error while trying to install ubuntu 10.10 from a bootable USB stick on to Sony Vaio P series laptop. The disk boots into the language and installation type screen. After that it goes through the splash and pulls up this error:



After getting this error the installation fails to start.

I have used the same USB stick on some other laptops and the installation started as usual. Any help will be appreciated.

My installation is i386 and my machine is Vaio P VGN-P610.

I've tried every possible thing:

Bios: [enable boot external]

[COLOR=Red]Boot order: [external] [hard drive] [network boot][/COLOR]

Tried 2 different USB drives

Tried 2 different external CD drives

Tried 6 different downloads of both the desktop and netbook remix.

All downloads were checked with MD5SUM.

Ubuntu Desktop 9.10 installs properly in every version and from every source.

I only have two USB ports on the Vaio and I've tried both of them. Alternate install would work if I could connect to the net over wireless (no ethernet).

Getting reaaaally frustrated.:confused:
Are you sure you want that mode?  Usually a USBstick shows up as a hard drive,
does your BIOS have a section for selecting ***which ***hard drive, look for USB under hard drives.
**EDIT:  **Also, most BIOS show a "**Boot Menu or  BBS" choice, to be invoked with some key, or key combination** in the very first section of text that appears when you are starting the computer, mine says **"F8 for BBS menu"** that will show you all the drives found that have an operating system on them, and can be booted from.

---

### Post by didadan on 2011-09-18
Hey, I just resolved this issue on my new machine. Goto SATA Settings in your Bios and use AHCI instead of IDE.
Hope this works for you, too.

---

### Post by psrdotcom on 2011-09-18
I support the reply of Didadun .. I think it might resolve the issue. Because, the issue we faced with Windows XP on i3 processor

---

### Post by brad.fairbanks on 2011-09-20
didadan wins....worked for me. Thanks!!!

---

### Post by poojasaraff on 2011-09-27
For me the SATA is set to AHCI only however I am still facing the same issue. 
I am try to boot from USB pen drive and want to install Ultimate Edition 2.8/2.9. busybox gives the error.
Some one help.
Thank you.

---

### Post by jfgencarnacao on 2011-10-11
I am having the same problem and my SATA is set to AHCI.  I'm trying to install Ubuntu 11.04 or even 11.10 Beta 2 on a Intel I3 computer with a SATA3 HDD

---


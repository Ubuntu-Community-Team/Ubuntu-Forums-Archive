---
title: "Install Appears to Work, Then GRUB Error 15 Occurs (Complete Details Inside)"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by svet-am on 2006-06-19
First, let me give the specs of my machine:
```

CPU: AMD Athlon64 3400+ (2500 MHz)
Mainboard: ABit KV8-Pro
Memory: 1024MB (512MB x 2) Crucial Ballistix
BIOS: Latest (Modbin6 Mod to disable onboard SATA controller as needed to prevent hardware detection errors)
SATA Controller: Promise SATAII150 TX4
Audio: Creative Audigy1 Gamer
Video: eVGA nVidia GeForce 6800GT

**DISCS**
SATA0: Western Digital 1200JD (120GB)
SATA1: Western Digital 800JD (80GB)
SATA2: Plextor 712SA

HDA: LG ATAPI DVD-ROM
HDC: Iomega ATAPI ZIP100

```

Some notes about the hardware.  you'll notice that the BIOS has been modded.  This is for a very good reason.  Out of the box, ABit does not allow you to totally disable the onboard SATA controller.  They allow you to disable the onboard SATA RAID ROM, but not the SATA controller proper.  While this works okay with Windows, this throws damn near every Linux hardware detection agent for a loop.  Through many sleepless nights, I discovered that the only way to fix the error is to mod the BIOS to enable the appropriate menu selection and then disable the SATA controller entirely.  Now, Linux hardware detection agents see *just* my Promise controller and don't get confused.

**PROBLEM**
I'm in the process of migrating every PC in our house to Dapper.  I've already done a complete install on my wife's computer and that is where I am typing this message.

On my PC, the Dapper LiveCD boots and sees my hardware just fine, with one small exception.  When it comes time during the install process to set up partitions, it somehow see my SATA1 device (the 800JD) as /dev/sda and it sees my SATA0 device (the 1200JD) as /dev/sdb.  While this is screwy, I decided to 'trust' Ubuntu and go with it.  Beyond this, the installer completes just fine.  However, upon reboot, I get 'INVALID SYSTEM DISK' from my BIOS.

Realizing that it's probably related to the error in detection I saw, I manually swap the cables for the 1200JD and the 800JD.  This time, the Ubuntu installers sees them properly (ie, 1200JD as /dev/sda and 800JD as /dev/sdb).  Feeling more confident, I proceed with the installer and it runs just fine.  However, this time upon reboot I get the dreaded "ERROR 15" GRUB error.

I again rebooted into the LiveCD, mounted the 1200JD and then started poking around in the filesystem.  Ubuntu properly created the filesystem, so I see that that's not the problem.  I head on over to /grub/menu.lst and look at it.  While I am currently incapable of copy-pasting that into here, it was created properly.  That is, the menu entry was pointing to /dev/sda/..../

My hypothesis is that GRUB is failing on the root(hd0,0) command.  I am not totally sure what this command actually does, so could someone please shed some light on it?

Also, does anyone have any insight into what I can try?  I'm 99.5% sure that the problem rests with GRUB and the GRUB configuration since I can mount the filesystems and they are just fine.

many thanks in advance!

---

### Post by svet-am on 2006-06-19
in order to determine if it was a "Linux" problem or an "Ubuntu" problem, I just installed a Quick'n'Dirty install of Fedora Core 5 and it installed and is running just fine.  However, I'd still prefer to be running Dapper on this box.

---


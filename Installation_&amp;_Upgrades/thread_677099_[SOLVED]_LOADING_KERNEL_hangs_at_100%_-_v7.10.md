---
title: "[SOLVED] LOADING KERNEL hangs at 100% - v7.10"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by glenvillecomputers on 2008-01-24
[COLOR="RoyalBlue"]CPU - Athlon 64 X2 4200 Dual Core @ 2.2GHz (stock clock)
MEM - 2GB DDR400
HD  - 74GB WD Raptor (SATA) 
MB  - DFI LanParty UT RDX200 (PCIe)
GPU - Radeon X850XT (stock clock)
LAN - Onboard x2
OS  - Windows XP Pro SP2

Partitions  - [53GB NTFS] and [16GB Unallocated]
BIOS - Defaul Settings[/COLOR]

When I try to boot the Ubuntu 7.10 Live CD, it gets to 100% at the kernel loading screen.  After a few seconds, I hear my CD-ROM Drive spin down, and its access light stops blinking. Only once, randomly, during a series of identical installation attempts did it boot into linux (the subsequent install nearly fubard my MBR, which I finished repairing last night ). 

I've been using linux distros for about two years, so I can find my way around the command line when i need to. I've tried solutions from a number of other posts with no results. I have the same problem trying to boot into safe graphics mode as well. 

all_generic_ide didn't work, so it may not be an issue with the sata drive.

some other things i've tried: 

acpi=ht
noapic nolapic

I've installed successfully using the same Live CD on four other computers here, including a mix of ati & nvidia gpus, and IDE & sata drives. 

After a few weeks of searching and trying, I'm ready to hit the forums ^_^ Any help or redirects are much appreciated. Thank you.

---

### Post by Rocket2DMn on 2008-01-24
Sounds like your computer just doesn't like the LiveCD (this can be rather common).  You can use the alternate install CD which doesn't have a live session and just has a text-based installer, but works very well.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for alternate cd.

---

### Post by glenvillecomputers on 2008-01-24
Using the Alternate CD produces an identical result, with the system loading the Kernel to 100% and hanging. As far as the CD goes, it checked fine when I scanned for errors, and the MD5 checks ok for the d/l ISO also. I think it's a hardware issue between my system and ubuntu. I ran a memory scan that produced no errors. It could be the sata drive, but that would have been avoided using all_generic_ide. I want to say it could be the dual-core processor or ACPI. I've found similar threads but they were no help so far. Also, using Ubuntu 6.10 produces the same error.

---

### Post by Rocket2DMn on 2008-01-24
So when you use the alternate CD, were you ever able to actually do the install or did it freeze up before you were able to do that?  Also, have you checked for BIOS updates?  These would be available from your computer's manufacturer's website, or if it's a custom computer, from the motherboard's manufacturer's website.

---

### Post by glenvillecomputers on 2008-01-24
It froze before I was able to do an install. The Kernel loading screen is the first thing that executes when you choose an option from the initial boot up menu (install, oem, defects, etc).  I'm also using the latest BIOS updates from DFI. That it worked once before, randomly (see above), is confusing me even more. I've ran burn-in stress tests in windows to test the system hardware, and nothing throws up an error. I haven't tried swapping out the CD-ROM yet, but that's next on my list.

---

### Post by Rocket2DMn on 2008-01-24
Checking the disc for errors doesn't tend to work very well.  It seems to me that the next step is to re-burn the disc (since we know the md5sum is ok), but make sure you do it at a slow speed, like 4x, to help prevent write errors.  Use quality media if possible.
If this doesn't work, using a different CD drive might help, though I'd be skeptical.
Would you happen to have multiple video cards, like a PCIe or AGP one alongside an integrated card?

---

### Post by glenvillecomputers on 2008-01-24
I'm going to try burning at a slower speed, and if that doesn't work, swap for a different CD-ROM drive. However, the fact that the same CD worked fine in four other computers makes me think that's not the issue (or bad media quality). What step happens during the installation immediately after the Kernel is loaded? Does it start examining the disk drives? That's were the problem seems to be, so understanding that would tell me what's tripping up the installation. Or maybe there's a 'verbose mode' that will let me see what's happening during kernel load.

---

### Post by glenvillecomputers on 2008-01-25
Burning at the lowest speed (8x) and swapping the CD-ROM drive both produced the same hang at 100%. It doesn't seem to be a media or CD drive issue. Also, this motherboard has no onboard video, the only video card being the PCIe x850xt. Having the same error with the Live and Alternate CDs points to computer hardware.

---

### Post by Rocket2DMn on 2008-01-25
Well it sounds like this is not going to work with a cd.  Although it doesn't SEEM to be a cd problem, there are other options to load linux, like doing a network install.  This link gives you a few options - [https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
My first suggestions would be to try with a USB flash drive - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) - just take note of the Comments section near the top, the user was able to follow the directions for Feisty for Gutsy with only a minor change which you may not even need.
It's worth a shot since you've already tried all this other stuff.  If this doesn't work, there must be some serious incompatibility with your hardware, but unfortunately we can't even look at any logs.  Should this be the case, you may need to 1) use another distro, 2) use an older version, or 3) wait for Hardy Heron to be release (due in April).

I gotta run to campus to drop some stuff off, but I'll check back with you when I return.  Better luck this time!

---

### Post by glenvillecomputers on 2008-01-28
The link has a number of installation methods that I'll be trying. However, don't all installations reach a point where the linux kernel must be loaded so the installation options can be chosen, or once installed, so the linux OS can be run? The flash drive installation didn't work. It loads the same processes as a LiveCD, only from a different source, so it encountered the same problem. SmartBoot and installation via floppy doesn't work for me because I have no floppy drives/cables here. Haven't used them for years, really. Installation through Windows will be my next attempt. Even once installed, I believe I'll still need to pass an additional  argument/arguments through GRUB during boot up since there's some h/w fix that will need to be applied to load the kernel. Is there a more specific thread I can move this too?

---

### Post by Rocket2DMn on 2008-01-28
OK, well if the kernel will just never load, you may need to try an older version or wait to try with Hardy in April (unless you want to download the testing version right now).  Are you using the 32 bit version of Ubuntu or the 64 bit?

---

### Post by glenvillecomputers on 2008-01-29
I managed to get Ubuntu running using the UNetbootin installer. Never figured out the problem with it installing via the other methods. Maybe still  HD/CDROM related ? I'm marking this as solved anyways. Thank you for your help along the way!

---

### Post by Rob-e on 2008-04-07
i just had this problem also, it would load the kernel very slowly, like 3% every second, then stop at 100%
i put in a known working cd drive and it worked like a charm

i actually have 2 more identical computers i will see if they do the same thing, if they do then it may be an issue with that model of cd drive otherwise it would just be that one bad drive

---


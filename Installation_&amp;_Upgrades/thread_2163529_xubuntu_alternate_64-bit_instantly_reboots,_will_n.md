---
title: "xubuntu alternate 64-bit instantly reboots, will not install"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2013-07-18
I select the language, and select "Install Xubuntu". The system instantly reboots and brings me back to the menu. 

Any ideas? It's hard to google for this issue, because there's not much to describe.

---

### Post by Bashing-om on 2013-07-18
BetterSense;

An excess of 4 primary partitions on the disk to be install on (msdos partition scheme) ?
Greater than 3TB disk to be installed on ?
Dual booting where Windows is using all the available partitions ?
UEFI ?
SSRT ?
Intel smart response ?
SSD -> raid a factor ?
cpu not pae and sse2 enabled ?
And I am sure many other possibilities.

So what are your hardware specs and your current partitioning ?

[INDENT][INDENT]hey gotta start somewhere
[/INDENT][/INDENT]

---

### Post by BetterSense on 2013-07-18
New 1TB hard drive

Old Pentium 4 system

No raid

System was working yesterday until the hard drive started clicking. So the hardware should really be fine.

UPDATE: I have been able to get as far as the "choose a password" before the system reboots. It just reboots, instead of going to the next step in the installer, and I'm back to the "choose your language" screen.
UPDATE UPDATE: I'm just sitting here re-trying it over and over, and about 15 times now it just insta-boots after I select "install Xubuntu"

Also, how did the system auto-populate my old hostname? The new hard drive is totally blank...

---

### Post by BetterSense on 2013-07-18
Update:

I tried a USB drive, made by unetbootin, and it does the auto-reboot thing, even when I choose something like "check memory for defects".

When I choose "test memory" I get an error saying " Cannot load a ramdisk with an old kernel image".

---

### Post by Bashing-om on 2013-07-18
BetterSense;

All I can think of presently is to try and format/partition the new drive with GParted.
Then see what GParted has to say about that disk.

And yes I have had experiences with a new install to an alternate disk that if that old disk is available, the new install is populated with the older install. That a time or too did save my bacon a time or two in my formative years.

[INDENT][INDENT]hey it's a thought
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-07-18
I am not sure from your description if you have tried running Xubuntu as a live system or have gone straight to the "Install Xubuntu" option, but it may be worth trying the "Try Xubuntu without installing" option.

You may again be thrown straight back to the reboot, but if so it could suggest that the ISO file you used is corrupt, or the DVD/CD you burned is a bad burn.  You should check the iso file with the listed md5sums shown at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") .  All instructions on doing so are at the site linked, or on other sites linked to from that one.

---

### Post by BetterSense on 2013-07-18
The alternate CD has no "try without installing".

I tried the Xubuntu alternate both CD and flash drive.

I tried a LinuxMint also, and got instant reboot.

I tried Ubuntu 12.04 and got to disk partitioning before reboot

It almost seems like I have a hardware problem. However, the system was doing fine yesterday. Is there anything specific that can cause this type of issue? Anything I can check to help troubleshoot?

---

### Post by Bashing-om on 2013-07-18
BetterSense;
Pops to mind... best I recall the p4 boards were IDE interface for the hard drives;
The new 1.5 TB drive is sata is it not ?
Recon there is a problem in the IDE/Sata adapter ?
If this is the case, I would do some googleing to see what problems such an adapter has presented.

[INDENT][INDENT]there are solutions
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-07-19
> **BetterSense said:**
> 
System was working yesterday until the hard drive started clicking. So the hardware should really be fine.

A clicking hard drive is far from fine. Actually it might be a sign of severe damage.

If you remove the hard drive can you do a live boot?

---


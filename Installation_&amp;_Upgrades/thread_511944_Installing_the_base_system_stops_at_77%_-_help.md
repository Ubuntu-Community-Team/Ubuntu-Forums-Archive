---
title: "Installing the base system stops at 77% - help?"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by yaddoshi on 2007-07-28
I am running a Medion Akoya notebook, also known as the MSI S260:
Pentium M 1.6GHz CPU
Samsung 512MB RAM
i915 motherboard
Samsung ATA6 60GB HDD
Samsung DVD/CDRW combo optical drive
intel 802.11b/g wireless adapter

I've been running Feisty 7.04 after I performed a distribution upgrade on Edgy 6.10 for a while, and I decided to once and for all destroy the Windows XP partition and convert my laptop entirely to Ubuntu, while simultaneously trying out the latest Alpha release.  I haven't had this much difficulty since I tried Breezy.  Unfortunately the tricks I used to get Breezy to work aren't helping me today.

I downloaded the 7.10 Tribe 3 Live Desktop ISO and burned a CD, tried to run the CD and it froze while loading.  I let it sit for a real long time after reading that this is a common issue, and to be patient.  I tried rebooting three times, no luck.  The recommendation was to try the Alternate CD if the Desktop CD doesn't work, so I switched to that next.

The Alternate CD works fine until it reaches 77% of the "Installing the base system" phase, with "Gathering information for installation report..." as the description underneath the progress bar.  I also went to cdimage.ubuntu.com and got the latest Daily Release for 7/28/07 - it started generating corrupted file errors during the install, so I chucked that, downloaded the release for 7/27/07 - it does the exact same thing as the Tribe 3 CD.

Thinking I could just install Feisty and then run a distribution upgrade, I grabbed a previously made 7.04 Feisty Alternate CD and ran it, and experienced the exact same problem.  I also ran the 7.04 Feisty Desktop CD and it died in the middle of loading, dropping to a terminal prompt displaying the following:
```
 BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) 
```

Just to be on the safe side I booted my old trusty DOS boot disk, ran FDISK, deleted all partitions, ran FDISK /mbr to clear the master boot record, created a new FAT32 partition for the entire drive, performed a slow format with no errors, deleted the partition and tried to load the Gutsy 7.10 Tribe 3 7/27/07 Alternate CD again.  This time I also edited the command line and added "linux noapic" to the end of the string (this fixed my install issues with Breezy).  Same problem - stopped at 77% "Gathering information for installation report..."

I've searched through the forums and can't find anything remotely like what I'm experiencing, so I'm hoping someone else can help me out.

One last thing, I've noticed each time I try to use the Gutsy 7.10 alternate CD, I get an error message for a brief moment right after the initial Loading Kernel screen goes away.
```
BIOS BUG: MCFG area at e0000000 is not E820 reserved
Not using MMCONFIG
```

My current plan of action is to install Edgy 6.10, immediately dist-upgrade to 7.04 and then again to 7.10 (I really didn't want to do that, I would rather just have a clean install of the latest version).

If anyone has any ideas that I haven't tried, please let me know here.  Thanks!

- Mat

UPDATE:  I have also tried using acpi=off and pci=noacpi with the same result.  In case anyone was wondering the CDs are fine, I used both Feisty CDs successfully on another computer without any issues whatsoever.  Because the problem is identical it is clearly not a "bad CD" problem - and it is unlikely the optical drive is the culprit or I would be seeing the freeze at different points during the install.

---

### Post by yaddoshi on 2007-07-29
Turns out my laptop just plain doesn't like the CDs I made from the Tribe3 ISO, although they work fine on my other computers.  It won't even mount them, although it did mount the Feisty alternate CD.  So basically this is what I did to get Gutsy installed:

1) downloaded and ran Edgy 6.10 Desktop DVD from cdimage.ubuntu.com (under releases) 
2) used the live installer to make a clean installation of Edgy
3) inserted the Feisty 7.04 Alternate CD I had tried earlier and ran a distribution-upgrade.
4) attempted to insert the Gutsy 7.10 Tribe 3 Alternate CD and it repeatedly failed to mount
5) burned a new CD with the same problem
6) followed the directions [here]("http://www.ubuntu.com/testing/tribe3") under "Upgrading from feisty"
7) Success - posting from Gutsy - and by the way, this particular kernel is running MUCH better than Feisty's on my laptop

I'm glad I made the switch.  If this turned out to be unusable I was going to downgrade to Edgy - Feisty has way too many speed and hang issues on my laptop, although it runs great on my daughter's PC.  Yes I understand this is an Alpha release and there are no guarantees the current configuration will remain the same.  I'm content to do daily updates, etc until the official release, at which time I will most likely download it and do a clean install - provided I don't have the same CD issues of course.

---


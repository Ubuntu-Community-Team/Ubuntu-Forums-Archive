---
title: "Machine won't boot from ISO or USB ..."
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2013-12-19
Hi all, 

I'd generally spend a couple of days digging around for a solution to this before posting, but haven't got a couple of days to spare pm this one.

At mother-in-laws machine which is 750Kms away from where I live. Get to this computer once or twice a year. I built it for her four or five years ago and originally it was running 8.04, then upgraded to 10.04 and all good. Sticking with the LTS, while I'm here the intention was to clean install 12.04 LTS (Xubuntu) and the machine should happily purr away without issue as it has done for pretty much the last four or five years.

I thought this would be straight forward. Cleaned up personal files and ready to go. Boot, go to BIOS and change to boot from optical drive, put in DVD, F10 to save and exit, reboots but goes straight to grub menu. Ignores DVD.

After boot and before the menu, though, the DVD light flickers on (more than usual) and gives the impression it is going to boot, but then nothing. To the menu as per a regular hard drive boot.

So, reluctantly, it's Plan B. I make a USB installer with Unetbootin. Set the BIOS to boot from 'Removable Device'. F10 to save and exit. Straight to menu, disregards the USB altogether. I try in various slots but no different. 

So, bottom line: as per the title; machine won't boot to installation media, either DVD or USB. I'm stumped and haven't got time to be! Hoping someone can help me out as I only have a few days (a couple actually) to get across this. Once booted, the rest should be plain sailing, but stumbling at the first hurdle for the moment.

Tnx in advance. ;)

PS: I will continue to dig for clues and update on progress, if any. My digits and eyes are crossed for success!

PPS: One of the issues with this machine is, after this many years, it has a separate /boot partition (not sure why I did this, but was learning) which is totally loaded. No room left. There is no connection? I'm thinking not ...

PPPS: When the machine is actually booted, I cannot mount the cdrom, but the USB dongle shows up and mounts fine. That shows up fine in BIOS also. Find attached the message I get when I try to mount the optical drive. It has a line in fstab but I'm thinking that even though the CD lights are blinking, there is something wrong with the hardware itself rather than this being a software problem. BIOS is set but won't boot from it, Ubuntu can't mount it. Makes sense it's a hardware issue there. So onward and upward with the USB, hopefully.

---

### Post by Bucky Ball on 2013-12-19
I had a thought. There are two five hundred gb hard drives in the machine. One has the 10.04 /, /home and /swap, the other I've emptied as I wanted to change the partitioning on it and update it to EXT4 instead of 3.

I'm wondering ... is there any way I could mount the Xubuntu 12.04 ISO in the running install (let's call that disk1) and install Xubuntu to the second drive (disk2) using the mounted ISO on disk1??? 

Where's my spade, more digging to be done!

* Unearthed Furius ISO Mount. I can see that I can mount the ISO using that. Can I also install Xubuntu to the other drive while the ISO is mounted with it???

One of my major issues here is that I can't conduct an experiment which may lead to a week of resolving.

---

### Post by oldfred on 2013-12-19
I have nVidia and the really old installs had lots of fun trying to configure nVidia and xorg. But I think it was 10.10 just installed without issue. 
Then they modified kernel and since then have had to use nomodeset on every boot of flash drive, CD or ISO direct boot that I do to install. And then on first boot or any boot until I get nVidia drivers installed.

What video card/chip do you have?

I do boot ISO directly with grub from another hard drive. From drs305 originally.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I keep my current, future and many repair type ISO in both another folder in a data partition on my hard drive and on several flash drives so I can boot or repair my system it need be.

---

### Post by sudodus on 2013-12-19
You can boot from a HDD as if it were a pendrive (and vice versa). You can clone the iso file with ***dd*** (or use my script ***mkusb*** to decrease the risk of overwriting the wrong disk). This method works almost always, and it is very straight-forward.

And *oldfred*'s tip about booting iso files from grub2 works well too (of course, otherwise he wouldn't have suggested it).

Did you remember to check the md5sum of the iso file?

---

### Post by Bucky Ball on 2013-12-19
Thanks for the replies and ideas. The ISO runs faultlessly in Vbox so there's nothing wrong with md5sum on the downloaded ISO I guess. I'll check that on the USB.

oldfred, not sure if graphics has anything to do with this (yet) as I'm not even getting to the point of a disk or USB being recognised and therefore not getting to a menu or anywhere I could insert nomodset (or would try). 

Apparently the optical drive was working fine and then things changed so firstly I'm going to physically make sure the thing is still plugged up correctly. Was also thinking of trying to create a bootable USB via 'Startup Disk Creator' and seeing if that makes a difference to the Unetbootin result as at least I know the USB dongle is being recognised by the BIOS and current 10.04 install, even though it is not booting from it. That points to something wrong with the way the USB dongle is set up by Unetbootin.

Failing all this, I will reluctantly, but with some enthusiasm, delve into the depths of installing the ISO from hard drive. This, I'd rather not be doing as I am going to need to install onto the empty drive (disk2) running the ISO from the current install on disk1. Disk1 currently contains ALL personal data from the last five years and there is NO backup of that and nothing to back it up to (not my box, remember?). Note to self: Next time, bring external hard drive!

In other words, I can't accidentally overwrite that data! I'm pretty confident, but launching into that without a backup is not something I would ordinarily contemplate.

Anyhow, all this once I've woken up a bit more and have my head on straight(ish). Thanks again. ;)

---

### Post by Bucky Ball on 2013-12-19
Problem solved. As I began to wake up, I remembered something I had read last night about putting the USB dongle in AFTER you were booted into the BIOS. That didn't make a lot of difference, but what did was when I went to the BIOS 'Advanced>USB Mass Storage Device Config>Emulation Type ... I then changed that to 'Forced FDD' and voila, it booted. I tried a couple of other things, like setting emulation type to CD or Hard Drive, but neither worked. Go figure.

Anyway, I am typing this from 'Try Xubuntu', everything is backed up from the old install onto two EXT4 partitions I have created on disk2, so wish me luck. I'm ready to roll! 

Thanks for your replies. I'll look into why the optical drive isn't working once 12.04 is installed, done and dusted, contingent on if I have the time before driving 750Kms home again. ;)

---


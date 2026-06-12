---
title: "Partition table deleted while trying to install on a MacBook"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by dmellis on 2007-12-23
Hi all,

I have a MacBook Core Duo that I'm trying to install Ubuntu Gutsy Gibbon (7.10) on.  In the process of doing so, I seem to have lost all partition information for my hard drive.  I'm hoping someone can explain what may have happened and how I can fix the problem.  Details follow.

The hard drive in my MacBook is a replacement.  My original drive was partitioned with BootCamp and had refit and Ubuntu installed on a secondary partition.  When I bought the current hard drive, I partitioned it with Disk Utility into a HFS partition for Mac OS X and a Linux partition on which I planned to re-install Linux.  I copied my original drive to the new one with Carbon Copy Cloner (I think that's the correct name), which transferred the Mac partition but not the Linux one.  Then I swapped the drives in the computer, and could boot Mac OS X off the new drive with refit.  

Then I tried to install Ubuntu on the second partition on my new hard drive.  I burned the live / install CD, booted into it (from refit) and started the install process.  I did a manual partition, deleting the small partition I had created in Disk Utility when I bought the new drive, and creating a new Linux partition (ext3) and swap partition in the space freed.  I also a had a few zero-byte partitions, whose meaning I don't understand.  The new ext3 partition ended up as sda9, while the Mac partition was I believe sda3 or 4.  

Near the end of the install process, I got an dialog saying that there was an error installing Grub and that this was a fatal error.  Remembering this message from the last time I installed Linux on this computer (on the old hard drive), I followed the instructions here: [http://bin-false.org/?p=17](http://bin-false.org/?p=17) : mount /dev/sda9, mounting /dev and /proc in it, chrooting to it, installing lilo, etc.  I got an error that linux-686-smp couldn't be installed, but everything else appeared to work.  

When I rebooted, however, I was greeting with a flashing folder with a question mark inside.  It was an unshaded folder, with a question mark of about a half inch or an inch high, which makes think it was coming from refit, not the normal Mac boot process (bios?).  In any case, when I booted back from the live cd (by holding down c on boot), I had only /dev/sda not /dev/sda9, or any other partitions.  Running parted confirmed that my partition table was empty.  

Any idea what happened?

What's the correct way in which my boot records / process should be structured?  It my Bios calling refit which calls grub which calls lilo?  Lilo instead of Grub?  When I boot Mac OS X, does lilo or grub get involved at all or does refit call Mac OS X directly?  

If I run testdisk, it sees my partitions, and tells me to restore them with pdisk, since it apparently doesn't support writing a Mac boot record.  Does that seem like good advice?  

If I manage to restore my partitions and want to install Ubuntu, how should I go about it?  What might have caused the grub installation failure?  

Thank you for any help you can offer.  I'm trying to fix this calmly, but it's always nerve-wracking to have your entire hard drive appear to vanish in an instant.

---

### Post by WaySensei on 2008-04-21
I'm in this for an answer. I recently deleted my Ubuntu partition to free up more space for Mac OS X, and also deleted the /efi and the /libary/startupitems/ folders related to refit. However, I get a flashing folder with a question mark at startup. I can still boot into the OS by holding option at boot, and selecting Macintosh HD, which makes me think refit is still there, somehow. Anyone know how to solve this?

---

### Post by dr johnson on 2008-04-21
Have you still got your OSX disc? If so, I think you may be able to boot from it, select the <i>disk utility</i> program (instead of going into the whole install procedure), and fix the HD's existing partition table from there. This worked for me in OS10.4, ppc ibook.

---


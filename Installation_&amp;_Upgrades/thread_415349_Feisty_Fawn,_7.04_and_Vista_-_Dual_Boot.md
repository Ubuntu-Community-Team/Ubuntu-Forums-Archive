---
title: "Feisty Fawn, 7.04 and Vista - Dual Boot"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by az on 2007-04-20
Two major issues for users who run Windows Vista and who want to install Ubuntu were brought on by changes made by Microsoft.  The first was a change in the NTFS filesystem and the second was a change in the microsoft bootloader.

Both of these issues were dealt with, but I would like to know what users' of Vista experience has been so far, using the final version of 7.04

The patch to fix the problem with partitioning NTFS filesystems created by vista was uploaded only a few days before release ([https://bugs.launchpad.net/ubuntu/+source/linux-ntfs/+bug/86231)](https://bugs.launchpad.net/ubuntu/+source/linux-ntfs/+bug/86231)).  The problem with the windows bootloader seems to not be consistent if we only rely on forum threads.

So, you should be able to install Ubuntu on a computer with Vista on it, without relying on the Vista partitioning tool, nor having to tweak your grub configuration (rootnoverify).   But is this the case for you?

---

### Post by at0mic on 2007-04-20
im going to live dangerously and install ubuntu on a secondary ide drive tonight. I wonder if it would be smooth sailing if it was done like this? Grub should be able to handle it

---

### Post by reiki on 2007-04-20
I have 3 hard drives in my system. 1 IDE and 2 SATA. Sata#1 is the first boot drive in BIOS (and where grub resides). Sata#1 has Feisty on it. Sata#2 has Edgy. The IDE drive has both WinXP and Vista (although Vista will be leaving as I find it to be a totally worthless piece of trash). During the installation of Feisty, GRUB found both Edgy and the Windows Boot Loader. It couldn't (or didn't) tell me how many operating systems were on that IDE drive. It just found the loader. That's fine. Grub chainloads the windows bootloader from the IDE drive when I choose that option in the grub menu and from THERE I get to choose whether I want XP or Vista. 

I think the original intent of the first post here was talking about dual booting when both are on the same drive, however I feel like I have saved myself a TON of trouble by isolating the windows operating systems on a separate drive. 

Drives are cheap. Do yourself a favor and don't do this all on one drive. Sure it can be done, but multiple drives just seem easier. (sorry, laptop folks... I know this won't necessarily work for you)

---

### Post by az on 2007-04-20
I have seen more than one way to fix the bootloader.  One of them is here:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

The other is detailed here:

[http://www.linuxquestions.org/questions/showthread.php?t=543956](http://www.linuxquestions.org/questions/showthread.php?t=543956)

If you needed to tweak your grub, please mention what you did...

---

### Post by comzip99 on 2007-04-20
I had no problems. GRUB automatically found my vista partition with no trouble! :)

---

### Post by az on 2007-04-22
> **reiki said:**
> 
I think the original intent of the first post here was talking about dual booting when both are on the same drive, 

Yes, because a lot of people seem to be saying they want to avoid only using one drive.

It is supposed to be as reliable either way.

---

### Post by dd501 on 2007-04-24
I'm dual booting Vista and 7.04 on a HP dv2275 notebook.

The biggest problem (of course!) was reducing the partition used by the pre-installed Vista.
The problem is made harder because (as seems common these days) you don't actually get any install CDs.

I tried using the inbuilt Vista partition software but it would only give me 5 of the 120GB drive.

I tried reducing the vista partition with the gparted version on the live cd (0.2.5 i think) but vista would then no longer boot - it would just hang on the Microsoft Corporation screen with that bar above it moving back and forth. (The later version of gparted might work better but I didn't need to try it in the end.)

The Vista Recovery Disk then wouldn't work either.
After reformatting the Vista partition as ntfs the recovery disks did work.
This of course causes the whole drive to get wiped - partitions I created disappear.
I was about to give up and not bother with Windows anymore.

However after a couple of reinstalls from the recovery disk suddenly the windows partition software allowed me to take about 50GB from the Vista partition. Brilliant!
I then messed around with the windows paging files and the restore points (as it suggests) and I was able to take about another 30GB. So this meant things were pretty much ideal as Vista was now on a 24GB partition (it already uses about 14GB! Though I haven't removed any software yet).

I then used gparted to divide up the rest of the drive into: shared files fat32, swap and ext3. Then installed Ubuntu. The first time I booted 7.04 it errored and rebooted. Since then it's been fine. And Vista booted fine also. Hopefully i'm not speaking too soon!

Just thought I'd share this in case anyone finds it useful.

In hindsight I wish I had bought from a company where you still get Vista install disks. Assuming that, like XP, you get the option to install into a partition. With recovery only disks it will not be very easy to reinstall into the partition it is currently if something goes wrong.

---

### Post by smac4president on 2007-04-26
I had two Vista partitions.  Shrank the one with only data and no Vista using the windows disk manager.  Guided install to largest free partition.  Grub picked it up automatically.  No problems at all.

I consider myself lucky but did a bit of research beforehand to fortify my resolve.

---


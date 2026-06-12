---
title: "First Re-install of OS; 10.04 LTS to 12.04 LTS upgrade bombed"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by agnewton on 2013-05-16
This is my first "clean" install where I want to preserve my user data and only reinstall the OS.

My upgrade from 10.04 LTS to 12.04 LTS did not go smoothly.  I use my ubuntu box for work/ research and have built a lot of programs from source and replaced other apps from the standard ubuntu repositories with newer versions while in 10.04 LTS.  In 12.04 LTS, the x-sessions-errors log is pretty active and the machine and gui slow down progressively the longer I use it.  One program even crashes the OS every time if it isn't the first app opened.  I've tried to fix things by reinstalling drivers, alternative desktops, running 2-D ubuntu ... all with no luck.

I have looked through the forums and done a "dry-run" of the clean install of the OS- up to the "INSTALL NOW" button- before turning back.  I see that there are three installation types.  One installs alongside the current OS and preserves the users /home directory and a third in the "Something Else" category.  I believe that the "Something Else" category is what I need.

I have separate partitions for swap, /, /home, /usr/local, and /opt (all ext4).  I have one final partition (/dev/sda6) formatted as ntfs.  I understand that I can choose which partitions to format during the installation and I would obviously not want to format /home, /usr/local, or /opt (or the ntfs partition) to preserve my built from scratch apps and other user data.  My question is how does the clean install know that these "preserved" ext4 partitions should be integrated into the "new" install?  The disk/ partition table does not identify these partitions by directory (/home, /usr/local, or /opt) only by /dev/sda* (the "Mount point" field is blank in the partition table).  Will I have to somehow link them to the OS later?  Is the new install going to create redundant /home, /usr/local, and /opt directories?  Will all this be obvious once I click "INSTALL NOW"?

My final question is where to install the boot loader?  I don't recall having the choice in my original installation.  My search of the forum suggests that I should install the bootloader on /dev/sda (and not any of the sub-partitions).  I only have one OS.

Thank you in advance.

Aric

---

### Post by dino99 on 2013-05-16
a few comments:
- 12.04 is way different than 10.04 ; so a fresh clean install is the best choice
- even if 12.04 is a LTS, a bunch of users prefer to install 13.04 for its quality (even if the main fixes are backported into 12.04)
- the canonical homemade installer, aka ubiquity, is not that app i can blindly trust : so better to follow the "manual" way, aka "something else" choice.
- if you opt for the custom server sub/partitions way, then use the server iso; the install process will take care of the existing partitions; otherwise its the ubuntu default install choice (do you really need that old fashion /opt partition ?)
- the bootloader is installed inside the MBR ( aka sdx) and the configuration is automatic (no need to worry about linking or else)
- ext4 is the best formatting choice

---

### Post by tgalati4 on 2013-05-16
If you have a dual-boot system, you would install the boot partition on the first disk (typically /dev/sda).  But you can also install the boot partition on other disks (sdb, sdc) as well as a backup.  Then modify your grub to point to this backup with some additional grub entries.  This allows you to perform some tricky boot schemes--like having 32-bit and 64-bit images side by side, having BSD formats (ufs, zfs) and others like reiserfs, etc.  So now you can upgrade /dev/sda without affecting /dev/sdb or /dev/sdc.  Sometimes having too many different operating systems will trip up an installer.

As far as your mount points for your partitions, in the partitioner, which you are dropped into when you select "Something Else" which is code for *I prefer to do it manually*.  As you highlight each partition, there is a drop-down list as to what it should be mounted to:  / (root), /home, /swap, etc.  Any mount not in the list can be specified as a custom entry.  You must go through this step carefully to make sure all of your partitions are identified this way before going to the next step.  You should not get redundant entries if you specify your mounts correctly.

Unfortunately, the create-your-own-partition map requires some experience and you may make mistakes.  By the third time you will understand how the process works and it will be much smoother.  Back up your important data first, and make sure that data is not on the machine you are working on. ** Failure to backup before partitioning or installing a new OS can result in data loss.**

---

### Post by zemega on 2013-05-16
You can install it on external hard disk first, and start tuning your custom made programs to run in 12.04. Then you can ditch 10.04. I would suggest 12.04 over 13.04 for you because you requires long term stable, which in case of 12.04 its until 2017. The best way I found to install into external is to disable the internal harddisk, load the live version (I use flash drive, not a CD), plug in the external and start installing.

---

### Post by agnewton on 2013-05-16
Thank you dino99 and tgalati4.  This was the background info I was seeking.  The choice of 12.04 is for the LTS part.  The computer's primary function is to crunch numbers (core i7 and NVidia GPU) and visualize output, so the server performance and other features aren't vital.  The other OS option I considered was CentOS (for its stability), but CentOS as a desktop is just so boring.

I will fill in the mount point directories in my partition table and give the reinstall a shot after my backup is complete.  I'll report back on my (hopeful) success.

thanks again.

---

### Post by agnewton on 2013-05-16
no luck on the 10.04 part.  It was replaced when the software installer executed the upgrade.  I seem to need to wipe out the broken 12.04 LTS and save my user data and from scratch apps.  I just don't want to wipe out any of the non-root (/) partitions.

---

### Post by agnewton on 2013-05-18
OK.  With my backups completed, I proceeded with a re-installation of the OS (/ partition).  Starting from a clean slate, I install the proprietary NVidia driver, blacklisted nouveau, and re-installed the program that was crashing the system.  This program (VMD) uses OpenGL for rendering and CUDA acceleration. 

The problems I wanted to solve remain (so it doesn't appear to be a Ubuntu issue per se).  The program does give me a warning about the X11 "Composite" extension possibly contributing to incorrect display.  Alternate desktops (Gnome 3 and Gnome classic) don't solve the problem either.  These alt desktops do get closer to providing a reason.  I get an ubuntu error message that the "Compbiz" application closes unexpectedly after launching the problematic program.  Ubuntu 2D produces the same application crash.

So it seems like if I need to use the program, I'll have to run a desktop with minimal of no effects.  I am going to give the lubuntu-desktop (lxde) a try and see if I can avoid the crash.

I'll report back before closing the thread.

---


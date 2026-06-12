---
title: "[SOLVED] Reinstall Ubuntu without losing a particular folder?"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by greybit on 2007-08-09
I'd like to reinstall Ubuntu 7.04 but I want to save a large chunk of data.  If I, say, put everything I want to save into a folder called Backup in the root directory, how can I keep this folder from being removed when I reinstall the OS?  Or perhaps there's a better way to do this?  I'd rather not copy all the data to disks but if that's the only solution I guess I'll have to.  Thanks for the help!

---

### Post by dabl on 2007-08-09
I can't fix what you have today, but if you're going to reinstall, this time make make a separate disk partition for your /home directory, so you don't have to go through this again!

:)

---

### Post by Eion on 2007-08-09
As a last resort you could burn it all to a CD or put it on a flashdrive.

---

### Post by greybit on 2007-08-09
Alright, I was afraid of that.  I'll burn the directory to some disks and for my new install I'll create a separate partition for my home directory.  Thanks for your help!

---

### Post by MrObvious on 2007-08-09
Can't the partition be resized and a new one made?

---

### Post by dabl on 2007-08-09
> **MrObvious said:**
> Can't the partition be resized and a new one made?

That's true -- if you don't mind doing a "two-step", you shrink your current / partition, and leave it untouched during your installation process, and then after booting your new OS, you mount the "partition formerly known as root", copy your data into your new /home folder, and you've got it.

Then in a subsequent re-partitioning adventure, you can delete the "partition formerly known as root" and add that space to your new /home partition.

Fair warning -- I did a similar maneuver last weekend on a 200GB drive, while preserving the OS and the data, and it took 4 hours for the re-partitioning/filesystem relocations to complete.

:)

---

### Post by MrObvious on 2007-08-09
What I propose is to use the Live CD, don't mount the drive, resize the current /, then make a new /home partition after rebooting that can hold all the data, then copy all the data needing backed up to the new /home, and then format / and reinstall Ubuntu. Problem solved.

---

### Post by dabl on 2007-08-09
Beautiful!

That should work great, assuming, of course, that the volume of data to be copied does not exceed 50% of the total disk drive capacity ... :lol:

Or, just call the existing "/" partition "/home" in the new installation, and delete all the non-data system stuff after the installation is finished and you're running it.

---

### Post by greybit on 2007-08-11
Thanks everyone for the help!  What I ended up doing was this:

I booted into the LiveCD where I mounted the root partition and removed everything but the folder Backup in the root partition.  I then used the program parted to resize this partition, leaving plenty of room for a new one.  I also removed the swap file and the extended partition with parted.  Then I rebooted and used the LiveCD to install Ubuntu to the newly available free space.  After installation I could easily mount the old partition and retrieve my data.  Wonderful!

Thanks again!

---


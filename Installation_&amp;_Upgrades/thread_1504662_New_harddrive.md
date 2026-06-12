---
title: "New harddrive"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by alexlaban on 2010-06-08
I feel that my old hdd is failing and have therefor bought a new harddrive. What would be the best way for me to replace the old drive without loosing any data. The new drive is larger then the old system drive.

---

### Post by dabl on 2010-06-08
Are you able to connect two drives to your computer?  If "yes", then the simplest approach would be:

1. Disconnect the power plug from the old drive, but leave it installed.
2. Connect the new drive electrically (power and data cables), boot a Live CD, and do your partitioning and install your operating system on your new drive.  Do whatever initial configuration and package installations you need to do to be able to work with the new system.
3. When the new OS is booting and running satisfactorily, shut down your computer, and reconnect the old drive's power plug, and power up the system.  Before it gets to the boot menu, press whatever key is needed to enter BIOS.
4. In BIOS, navigate to the "boot device sequence" screen, and look at the hard drives.  Set the new drive above the old drive, so it will be booted first.
5. Save the BIOS settings and proceed with booting (should boot into the new OS).
6. Your old drive and/or data partition won't be mounted, so you will need to use the mount command, with "sudo" prefix, to mount the partition where your data are located (exercise for the student -- see "man mount").
7. Once the data are available, use your favorite file management process/package to copy the data from the old drive to the new drive.
8. When the data are safely copied and verified, you can shut down, remove the old drive completely, and finish installing the new drive in the drive bay of your computer.

If your hard drives happen to be IDE/ATA interface, then there's a twist -- when you power up both drives, in BIOS you'll also need to go to the IDE channel and set the new drive as "Master" and the old drive as "Slave", in addition to setting the boot sequence, so the new drive will boot.

There are other approaches, of course -- you could boot a Live CD, with both hard drives connected to the computer, and then mount the applicable partitions on both hard drives, and then copy the data.  But you would still need to have a suitable formatted partition on your new hard drive to do it that way.

Hope this helps.

---

### Post by alexlaban on 2010-06-08
> **dabl said:**
> Are you able to connect two drives to your computer?  If "yes", then the simplest approach would be:

1. Disconnect the power plug from the old drive, but leave it installed.
2. Connect the new drive electrically (power and data cables), boot a Live CD, and do your partitioning and install your operating system.  Do whatever initial configuration and package installation you need to do to be able to work with the new system.
3. When the new OS is booting and running satisfactorily, shut down your computer, and reconnect the old drive's power plug, and power up the system.  Before it gets to the boot menu, press whatever key is needed to enter BIOS.
4. In BIOS, navigate to the "boot device sequence" screen, and look at the hard drives.  Set the new drive above the old drive, so it will be booted first.
5. Save the BIOS settings and proceed with booting (should boot into the new OS).
6. Your old drive and/or data partition won't be mounted, so you will need to use the mount command, with "sudo" prefix, to mount the partition where your data is (exercise for the student -- see "man mount").
7. Once the data are available, use your favorite file management process/package to copy the data from the old drive to the new drive.
8. When the data are safely copied and verified, you can shut down, remove the old drive completely, and finish installing the new drive in the drive bay of your computer.

There are other approaches, of course -- you could boot a Live CD, with both hard drives attached, and then mount the applicable partitions on both hard drives, and then copy the data.  But you would still need to have a suitable formatted partition on your new hard drive to do it that way.

Hope this helps.

Yeah I kinda knew that, it's mainly the verification part I'm wondering about. What's the best way to know everything is intact.

---

### Post by dabl on 2010-06-08
Quick and dirty is just open your file manager with a split window, and (for each directory) line up the files side by side.  They need to match.

Also, you can right-click in the "white space" in each directory, and check the properties.  For each directory with data that you copied (like music), the number of bytes needs to be identical.  If they are not, then you have a little search mission to find out what is different, and why.

---

### Post by Backharlow on 2010-06-08
Also, be aware that copying files with cp or mv or nautilus, etc. will work for non-system files just fine. However, copying your linux root partition by hand like that, while it will back up the data, will not actually create a bootable copy.
dabl is right about enabling the new drive, but before that at his step 2: > 2. Connect the new drive electrically (power and data cables), and do your partitioning and install your operating system. Do whatever initial configuration and package installation you need to do to be able to work with the new system.
If you want to start over with a new Ubuntu install, and maybe keep your home directory for the new one, then just installing to the new drive is fine, otherwise you need to actually clone your old OS partition, to the new one. For this you need either a separate OS to do this from, or a LiveCD. When I did this I used Clonezilla. This is a linux live cd specially designed for cloning (replicating) 1 drive or partition to another. Clonezilla was simple and worked really well. It is also fast because it doesn't copy individual files - but rather the raw disk image of the partition itself, and then makes the clone "bootable".
This is also a good example of why it is good to keep you /root and /home on different partitions. If you end up having to replicate or totally format and reinstall the OS, its a little ten-dig partition that can be wiped without effecting your user account (personal files).
I'm sure there are six other ways to backup your os, but again clonezilla is remarkably simple, and just does that one thing well. you can also use gparted later to expand the cloned os partition.

---

### Post by dabl on 2010-06-08
> **Backharlow said:**
> 

 However, copying your linux root partition by hand like that, while it will back up the data, will not actually create a bootable copy.



Right -- I would not advise trying to copy any of the OS.  I was referring only to the user's data, wherever it is located on the old drive.  Personally, I don't even mount /home separately -- I install the entire OS in its own partition.  I keep my data on separate partitions and symlink the data directories into the /home/user folder.  That keeps all the "settings" out of my data partitions, and lets me safely nuke the OS and install a new one with no concern about "settings" or data.

---

### Post by Backharlow on 2010-06-08
dabl: we are in agreement. I do the symbolic link for /home too. But he might want to clone the OS rather than wipe and reinstall. The original post didn't have much detail.

---

### Post by alexlaban on 2010-06-08
Well turns out the hdd is actually broken now. When I tried to boot the system it said something about broken harddrive press enter to continue and I did which took me to a screen saying GRUB in the upper right for a little while not being able to do anything and then the system crashes and reboots. I'm reinstalling on the other harddrive and will try to restore some files if possible, hopefully I will be able to save some files. Anyone know how one would copy MySQL databases with only access to the file system?

---

### Post by dabl on 2010-06-08
> **alexlaban said:**
> 

Anyone know how one would copy MySQL databases with only access to the file system?

Sorry, I do not know about that.

However, I will offer that just because a drive won't boot does not mean it won't let you copy data off of it.  Booting is a special category of performance, and when it is just sitting there spinning, it may be OK for copying off your data.  So, there's hope!

---

### Post by alexlaban on 2010-06-08
Yeah that's what I hope for however before I try I want to know how to manually copy the databases since I don't know how many tries the disk got left if any.

---

### Post by dabl on 2010-06-08
Google turned up this -- you'll have to adjust to fit your device/directory:

[http://support.adobe.com/devsup/devsup.nsf/docs/52353.htm](http://support.adobe.com/devsup/devsup.nsf/docs/52353.htm)

---

### Post by alexlaban on 2010-06-08
> **dabl said:**
> Google turned up this -- you'll have to adjust to fit your device/directory:

[http://support.adobe.com/devsup/devsup.nsf/docs/52353.htm](http://support.adobe.com/devsup/devsup.nsf/docs/52353.htm)

Thanks but what if I don't know the names of my databases? Or if the mysqldump binary is one of the broken files on that harddrive?

---

### Post by dabl on 2010-06-08
I shouldn't even opine on mysql questions -- I have no experience with it. 

However, one would think that if you installed mysql on your new system (on the new drive), then you'd have all the utilities and capabilities of mysql, right?  So, presumably you could mount the old drive, and use your running mysql environment to do whatever with the files on the other drive, including the conversion to a text file thing.  Just guessing, really, but it seems like a reasonable approach (until someone who actually knows what they're talking about shows up ....).

---


---
title: "Seperate /home Partition (advanced)"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by phibit on 2010-04-20
This is a question about setting up a separate /home directory, but I will preface it by explaining my current setup.

2x500GB RAID1 (mirror) : Ubuntu Karmic install and /home directory
1x200GB spare drive : empty

In upgrading to Lucid (which I am looking forward to), I would like to change my setup to be like this:

2x500GB RAID1 (mirror) : /home directory ONLY
1x200GB drive : / directory for Ubuntu installs and upgrades

My main concern is preserving my /home directory, and all the data inside. The approach I was thinking of is straightforward, but I'm not experienced enough to tell if it will work:

1. Boot into LiveCD, perform a standard Ubuntu Lucid install on the 200GB drive
2. Point the new install to my old /home directory on the RAID drives
3. Boot into my new installation on the 200GB, and delete everything on the RAID array except the /home directory (i.e. get rid of /var /opt /etc/.... Can you do that?)

Are there any concerns I am overlooking? I suspect that the installation process won't properly recognize the RAID array, and I don't want to much this up.

If you guys have any suggestions they'd be much appreciated. Thanks!

---

### Post by dabl on 2010-04-20
It's not clear from your description whether your current /home directory is on its own drive partition, or is embedded with the rest of the filesystem on a single partition.

Regardless, this part of your plan should work:

> **phibit said:**
> 

1. Boot into LiveCD, perform a standard Ubuntu Lucid install on the 200GB drive




This part will _not_ work if your current /home directory is on the same partition with the rest of your Linux filesystem:

> 

2. Point the new install to my old /home directory on the RAID drives
3. Boot into my new installation on the 200GB, and delete everything on the RAID array except the /home directory (i.e. get rid of /var /opt /etc/.... Can you do that?)


In other words, when /home is located on its own separate partition, then you could proceed as you planned, but if the entire Linux system including your /home directory is on a single partition, then you can't just go in and start deleting things and end up with a happy filesystem.

Thoughts:

- Even allowing for the occasional ISO download, you only need 10 or 15GB for the basic Linux filesystem.  200GB is way overkill.

- If your existing data is less than ~180GB, then potentially you could (a) partition your 200GB drive into a 20GB and a 180GB partition, copy your data into the 180GB partition, install Ubuntu into the 20GB partition, and then proceed to repartition/reformat the 500GB RAID set.

- There's no law that says your data has to physically be in the /home directory.  Mine lives on partitions with labels like "DOCS", "IMAGES" and "MUSIC" and then I symlink them into my /home folder.  That might be a way around your space challenge.

- You're facing a Grub2 maneuver -- hopefully you have a handle on that.

---

### Post by phibit on 2010-05-01
Thanks for the advice, I have taken it into account and decided on the following strategy:

1. Backup my existing /home directory onto another drive.

2. Repartition my RAID1 (2x500GB) array into THREE (3) Parts:
   - /dev/md0 : 20Gb segment dedicated to Linux distribution
   - /dev/md1 : 2Gb segment dedicated to swap space
   - /dev/md2 : 470Gb segment that will be my new /home

3. Create relevant files systems:
   - /dev/md0 : ext4 file system
   - /dev/md1 : swap space
   - /dev/md2 : ext4 file system (** side note: it would be nice if I could access this portion from Windows 7 , any ideas?)

4. Install Ubuntu Lucid on /dev/md0, specifying that /dev/md1 will be swap and /dev/md2 will be /home

5. Enjoy the resulting magic!


Some concerns of mine are:

1. Does it make sense to reconfigure my RAID1 array, and all the file systems, PRE-installation?

2. Will the Ubuntu Lucid installer properly recognize the RAID configurations?

3. Is 20GB enough space for a Linux Install, bearing in mind I will be installing a fair amount of programs?

Your wisdom would be appreciated, please let me know if there are some red flags in what I'm proposing.

Thanks!

---

### Post by phibit on 2010-05-01
Okay, for the record, the installation worked fine, that is the Lucid alternate cd detected all the RAID arrays correctly, I was able to mount md0 as /, md1 as swap and md2 as /home.

Now, there's another problem, which I guess I was warned about but was still unprepared for: GRUB isn't loading... like, at all. No "grub rescue>", nothing. Kind of looks like it doesn't recognize that the drive is even bootable, it just hangs there.

Any suggestions?

---

### Post by phibit on 2010-05-02
Alright, so I finally got this working. Here is a quick how-to.

Goal: RAID1 Setup with Ubuntu Lucid.
[LIST]
[*]/dev/md0 : ext4 mounted as /
[*]/dev/md1 : swap
[*]/dev/md2 : ext4 mounted as /home
[/LIST]

Instructions:

Note: the two drives I'm using are /dev/sda and /dev/sdb, but substitute your corresponding devices names.
[LIST=1]
[*]Format /dev/sda using fdisk, create 3 new partitions (using n). I used 20Gb for /, 4Gb for swap and the rest for /home. Write the changes with 'w'.
[*]use "# sfdisk -d /dev/sda | sfdisk /dev/sdb" to copy the partition tables exactly from sda to sdb.
[*]Use mdam to create the 3 RAID1 devices. Run "sudo apt-get install mdadm", then for each of the corresponding /dev/sda# and /dev/sdb#, run 'mdadm --create /dev/md# --level=1 --raid-devices=2 /dev/sda# /dev/sdb#'.
[*]Reboot into the Lucid Alternate CD, and follow the steps. It should recognize your RAID devices right away. Assign the proper mountpoints for each and install as normal.
[*]Voila. If all goes well you now have a nice clean RAID1 Ubuntu Lucid setup.
[/LIST]

Hope this helps.

---

### Post by phibit on 2010-05-04
See this thread:

[http://ubuntuforums.org/showthread.php?t=1469169](http://ubuntuforums.org/showthread.php?t=1469169)

For follow-up headaches.

---


---
title: "Installing on 1 TB HDD"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Savio2010 on 2011-03-22
This Thread is confusing me.
[http://ubuntuforums.org/showthread.php?t=1641511](http://ubuntuforums.org/showthread.php?t=1641511)

Has any one installed ubuntu 1010 or 1104 on a 1TB internal SATA HDD successfully. are there any problems in installing. I wish to upgrade my HDD.

Please Help.:roll:

---

### Post by Dutch70 on 2011-03-22
What exactly is confusing you about that thread? 
Do you have Ubuntu installed now? and...
Are you planning to replace your hdd, or just add a 2nd hdd?

---

### Post by deconstrained on 2011-03-22
As long as the motherboard's firmware supports it, installing is the same on any internal hard drive, regardless of size. If you're looking to *move* your current installation to a new/different hard drive, that's a different process.

Also, one reason why the thread may be confusing you is because it's about installing on an ***external*** harddrive, while you seem to be interested in installing Ubuntu on an internal hard drive. Installing on an internal hard drive is far less complicated, except for having to install the new hard drive into your computer (which requires a screwdriver and a grounded surface).

With few exceptions, in most cases **moving** an installation should be a fairly straightforward, albeit long process. However, it's only necessary if you want to move your root filesystem to the new hard drive (i.e. the system's files). Do you want to get rid of the old hard drive?

If not, it would be easiest to just make a single partition on the new hard drive and format it with your filesystem of choice, then move the contents of /home (which should include all your personal files) to it, keep the old hard drive, and modify /etc/fstab to reflect the changes. You could do this if you have an extra SATA port to spare for the new hard drive, and it would allow you to use the extra storage space.

---

### Post by Savio2010 on 2011-03-22
I am planning to upgrade my 80 GB IDE HDD to 1 TB Sata, when ubuntu 11.04 is released.

I am currently having

Pentium D 3.0 GHz Processor.
Biostar 945GZ Chipset Motherboard
512 DDR2 (533 FSB) RAM ................................1 GB + 512 after upgrade.
80 GB IDE HDD................................................1 TB after upgrade.


I'll be upgrading after 1104 is released, so it is going to be fresh installation.
Just the home folder and some other files from my 80 GB is going to migrated to the new 1 TB.

---

### Post by deconstrained on 2011-03-22
> **Savio2010 said:**
> Just the home folder and some other files from my 80 GB is going to migrated to the new 1 TB.
Great, that should be easy. Just make sure you use UUID's to identify the partition on the new hard drive in /etc/fstab and it'll work seamlessly. To make the transfer I recommend using rsync with the -a ("archive") option enabled, so that permissions, ownership and timestamps are preserved.

For example: 
1. Partition the new hard drive
2. Mount the new partition at /mnt/newHDD
3. (as root) rsync -avh --progress /home/ /mnt/newHDD/
4. find the UUID of the partition: use the "blkid" command (as root) to see which uuid corresponds to which partition (example: the uuid is 19cd242d-ef52-5e95-9375-f369fd694g46 and the filesystem type is ext4)
5. Add this new line to /etc/fstab (example)
UUID:19cd242d-ef52-5e95-9375-f369fd694g46 /home ext4 defaults,noatime 0 0
6. Unmount the partition and reboot.

---

### Post by Savio2010 on 2011-03-22
Thanks.

:guitar:

Now I am waiting for Ubuntu 11.04.

---


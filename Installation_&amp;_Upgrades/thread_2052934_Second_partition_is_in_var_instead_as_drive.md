---
title: "Second partition is in /var instead as drive"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by stefens on 2012-09-04
Hi folks,

I installed Ubunutu 12.04 Gnome-Shell Remix on my computer and I'm really satisfied with it! But I do have a problem concerning the second partition (for backups) of my hard drive.
During installation, I split up the drive in two halfs and set the first one as '/' (root) and the second one as '/var', bc I thought thats where all the other drives go. 
Unfortunately, I can't make use of the second partition as a sole backup drive, bc the /var folder is still in use and on the second partition.
How do I have to re-configure Linux to have the /var folder on my primary drive and the secondary drive as a backup partition only?

thx

---

### Post by darkod on 2012-09-04
If you look in /etc/fstab there should be entry like:
UUID=<string> /var etc.....

Boot with the cd in live mode (not from the hdd so that it doesn't mount / and /var), and mount your / and /var partitions at any temporary mount point. For example you can create /mnt/temproot and /mnt/tempvar and mount the partition there.

Then create a var folder inside the / partition (inside the temporary mount point), so that would be like /mnt/temproot/var.

Copy everything keeping ownership and permissions from the partition into the new folder, like:
sudo cp -ax /mnt/tempvar/ /mnt/temproot/var/

After that edit the fstab and comment out the /var line (put a # symbol in front). Don't forget that with the temporary mount of / the fstab will be something like /mnt/temproot/etc/fstab.

Reboot and that should be it. Without the /var entry in fstab active, it should use the var folder inside /. By keeping ownership and permissions during copying, it should work fine.

After you are sure it's working, you can format the second partition and use it as you wish.

---

### Post by stefens on 2012-09-04
It worked!
Thank you, though the correct usage of the copy command was
sudo cp -ax /mnt/tempvar/**.** /mnt/temproot/var

---

### Post by darkod on 2012-09-04
Didn't know about the dot. The other option was to enter the directory first, and then copy using a * to replace everything in the folder, like:
cd /mnt/tempvar
sudo cp -ax * /mnt/temproot/var/

Anyway, glad it worked. Please mark the thread as Solved using Thread Tools above the first post.

---


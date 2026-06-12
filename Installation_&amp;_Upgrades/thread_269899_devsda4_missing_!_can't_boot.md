---
title: "/dev/sda4 missing ! can't boot"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by danran on 2006-10-02
I have XUbuntu Dapper 6.06 installed on my PC.  I have dual-booting setup for Windows XP and XUbuntu.  The problem is I can't boot into Linux anymore.  It's giving me an error right after initrd loads that says: 

mount: Mounting /dev/sda4 on /root failed: No such device

It then brings me to a BusyBox cmd line.  The Windows XP boots up fine, so I know it's not a loose HDD cable or anything physical.  The last thing I was doing was trying to get Compiz/XGL working on XUbunutu.  I rebooted and it gave me these errors.  I tried manually mounting /dev/sda4 to /mnt and it gives me the error:

mount: Mounting /dev/sda4 on /mnt failed: Invalid argument

I have not modified my /etc/fstab since I installed XUbunutu.  I'm puzzled...

---

### Post by crokett on 2006-10-02
if you boot the live CD to rescue mode, can you mount the partition?

---

### Post by danran on 2006-10-02
Yes, I can mount /dev/sda4 from my Xubuntu install disc.

---

### Post by crokett on 2006-10-02
Hrmm... so /dev/sda4 is where Linux is actually installed? 

What partition is /boot?  or is that also /dev/sda4?

---

### Post by danran on 2006-10-02
My partitioning scheme is like this:

/dev/sda1 (fat16) dell utility partition
/dev/sda2 (ntfs) winxp
/dev/sda3 (extended)
/dev/sda5 (ntfs) data_backup
/dev/sda6 (linux swap)
/dev/sda4 (ext3) linux root install

---

### Post by crokett on 2006-10-02
Ok.. so first you said you tried manually mountiung it but it said invalid argument?  but you can mount it to the live CD?  So if the system can't mount your root file system, where were you trying to mount from that it failed with invalid argument?  and exactly what mount command did you use that it failed?

what does your /etc/fstab file look like?

---

### Post by danran on 2006-10-02
> **crokett said:**
> Ok.. so first you said you tried manually mountiung it but it said invalid argument?  but you can mount it to the live CD?  So if the system can't mount your root file system, where were you trying to mount from that it failed with invalid argument?  and exactly what mount command did you use that it failed?

what does your /etc/fstab file look like?

It failed with invalid argument when I tried mounting sda4 from the BusyBox built-in shell (that I was brought to after the partitions were tried to automatically be mounted at system boot-up).  The exact mount command i'm trying to use is 'mount /dev/sda4 /mnt2'  (I have to create /mnt2).  The exact error I get is:

>>>>>
[4294990.203000] cramfs: wrong magic
mount: Mounting /dev/sda4 on /mnt2 failed: Invalid argument
<<<<<

Here's my fstab:
>>>>>
proc  /proc  proc defaults 0 0
/dev/sda4  /  ext3  defaults,errors=remount -ro  0  1
/dev/sda6  none  swap  sw  0  0
/dev/hdc  /media/cdrom0  udf,iso9660  user,noauto  0  0
/dev/sda5  /media/NTFS_ARCHIVE  ntfs  defaults  0  0
<<<<<

---


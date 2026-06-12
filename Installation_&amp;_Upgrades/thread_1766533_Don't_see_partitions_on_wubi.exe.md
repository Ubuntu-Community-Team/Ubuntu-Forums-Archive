---
title: "Don't see partitions on wubi.exe"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by armk123 on 2011-05-24
I'm using Windows 7 32 bit, and want to install Ubuntu 9.04 Inside Windows via wubi.exe .

Using Acronis Disk Director Suite, I created a new ext3 partition to install Ubuntu on it, all goes fine but when I go to My Computer I don't see the partition, it may be normal as Windows doesn't show ext3/ext4 partitions.

The problem is I don't neither see the partition in the Ubuntu Installer, I only see the old partition which are FAT32 and NTFS but not the ext3 one to install on it.

Attached photos may explain better.

How can I choose the LINUX partition to install on?

Thank you.

---

### Post by aarsalankhalid on 2011-05-24
I might be absolutely wrong here...but I think for wubi installation, you don't need to format your drive to ext3. Just format it to NTFS and see if it works.

---

### Post by armk123 on 2011-05-24
> **aarsalankhalid said:**
> I might be absolutely wrong here...but I think for wubi installation, you don't need to format your drive to ext3. Just format it to NTFS and see if it works.
For more than a year ^_^ I've been trying to install ubuntu in C:\ partition which is NTFS, but it keeps giving me "No root file system" and somebody advised me to create ext3 partition for ubuntu.

---

### Post by aarsalankhalid on 2011-05-24
> **armk123 said:**
> For more than a year ^_^ I've been trying to install ubuntu in C:\ partition which is NTFS, but it keeps giving me "No root file system" and somebody advised me to create ext3 partition for ubuntu.

But you're trying to install ubuntu from inside of windows, right?

---

### Post by aarsalankhalid on 2011-05-24
As a test, I just installed ubuntu from live cd within windows 7. It detected my NTFS partition alright.

---

### Post by armk123 on 2011-05-25
> **aarsalankhalid said:**
> But you're trying to install ubuntu from inside of windows, right?
Does installing inside windows mean that I should install ubuntu in the same partition where windows is installed on? if not so, I will install it inside windows but in another partition.

Anyway, I just formatted ext3 partition to be NTFS, and now trying to install ubuntu in it.

I was getting this problem when I was trying to install in C:\ .

Thank you :)

---

### Post by armk123 on 2011-05-25
I tried to install in an NTS partition, all went file but when I restart I got the error above, No root file system.

---

### Post by armk123 on 2011-05-28
Where did my whole partitions go to??

[IMG]http://upload.traidnt.net/upfiles/xG440959.png[/IMG]

---


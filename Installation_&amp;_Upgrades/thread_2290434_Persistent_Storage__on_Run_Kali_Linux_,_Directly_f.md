---
title: "Persistent Storage ? on Run Kali Linux , Directly from Hard Disk in Ubuntu"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by indianosr on 2015-08-12
I followed a tutorial : [http://www.tecmint.com/run-linux-live-images-from-hard-disk-in-linux/](http://www.tecmint.com/run-linux-live-images-from-hard-disk-in-linux/)

I was successfully able to boot Kali by keeping the ISO's in the Ubuntu partitions. 

I need to know, how to make persistent storage or utilize Ubuntu's partition to store files/output from Kali ?

---

### Post by yancek on 2015-08-12
The Kali booted from an iso as explained in the tutorial is to boot it from a hard drive and it is a "read-only filesystem".   That means changes made will be lost on reboot, it's the nature of the system.  It is possible to create persistence although I'm not sure how it would work in your example.  Do you have only Kali or have you also used the other distros mentioned in the tutorial.

---

### Post by indianosr on 2015-08-13
I have Kali. In Fact I have Kali Linux 1.0 and 2.0 now.

---

### Post by yancek on 2015-08-13
Booting the iso of Kali from Grub2 will mean it is a read-only filesystem as I stated previously.  This means you can't save changes.  As I'm sure you know from visiting the Kali site, there are specific instructions for creating a persistent install on a flash drive.  I imagine this could be done on a hard drive also but would probably mess up whatevery you have including Ubuntu.  Never tried it myself.  If you want to save data from Kali, boot it up and then you have the option to create a mount point in Kali, mount the Ubuntu partition, and you could then use a data directory (name it something appropriate like Kali-data) on your Ubuntu partition.  Then you would need to mount the partition to have access to it.  You could also create a separte additional small partition just for data from within Ubuntu and mount that for your Kali-data.  Since you are doing this from a Live install, you would need to repeat this process each time you boot Kali, that is the two simple command to create the directory (mount point) and mount the partition.

---

### Post by ubfan1 on 2015-08-13
I could only get persistence to work on my hard disk when I had the persistence file on a FAT partition.  I assume a FAT partition labeled "casper-rw" would work too, but I wanted to use files so I could have several different ones.  Use "persistent persistent-path=/A" (or whatever directory instead of /A) to indicate which capser-rw file to use.  Using the "toram" takes an extra 15-20 seconds at boot, but does noticeably improve performance.

---

### Post by indianosr on 2015-09-03
Is there a way to install complete Kali tools on Ubunut?

---


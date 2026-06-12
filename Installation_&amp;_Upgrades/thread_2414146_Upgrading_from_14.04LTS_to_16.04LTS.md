---
title: "Upgrading from 14.04LTS to 16.04LTS"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by KieranFitzgerald on 2019-03-06
Trying to update but I am having problems getting started.  I selected upgrade from the software updater.  I get an out of disk space error, screen shot uploaded.  No further details provided.   I have an SSD with boot & system partitions.  home is on my HDD all appear to have space.
Last time I tried others suggested removing old Linux kernels which I have done but no change.

If I try to upgrade from the command line I get an internet connection error see second screen shot. Press OK still offers an upgrade but also give out of space error.

What do I do now?

---

### Post by Dennis N on 2019-03-06
I've encountered that warning. The update manager needs sufficient space to store all the downloaded files which can be a lot. If you make some room by temporarily moving enough data files to temporary storage or enlarge the root partition by a few GB, it should go through.

---

### Post by KieranFitzgerald on 2019-03-06
My root partition is on the ssd I am trying to increase the size but I have a Windows reserved partition in the way.   This has an error according to Gparted so I can't move it.  Windows works fine so no idea why it's reporting an error or how to fix it.   Can I relocate root to the hard disk?

Edit Gparted reports "unknown" file system for the reserved partition.

---

### Post by KieranFitzgerald on 2019-03-06
I managed to get 6GB more for root but still not big enough.

---

### Post by monkeybrain20122 on 2019-03-06
Just backup your data and do a clean install, much faster and safer.

---

### Post by Impavidus on 2019-03-07
You can relocate the root partition to the HDD, but you'll lose the advantages of having it on the SSD. Moving it will be more work than a fresh install, especially as you already have a /home partition. So try a fresh install.

---

### Post by KieranFitzgerald on 2019-03-07
I tried a clean install last night using the "something else" option. got message No root file system is defined!  How should I prepare my SSD (sda) and HDD (sdb) for the install?  sdc is for backup.

This my current partition scheme

```
kieran@Desktop:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABELNAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           111.8G            
&#9500;&#9472;sda1 vfat     487M /boot/efi  
&#9500;&#9472;sda2 ext4    25.7G /          
&#9500;&#9472;sda3 ext4    15.3G /usr       
&#9500;&#9472;sda4          128M            
&#9492;&#9472;sda5 ntfs    58.5G            
sdb           931.5G            
&#9500;&#9472;sdb1 ext4     3.7G /var       
&#9500;&#9472;sdb2 swap     4.7G [SWAP]     
&#9500;&#9472;sdb3 ext4   727.4G /home      
&#9492;&#9472;sdb4 ntfs   175.8G            
sdc           232.9G            
&#9492;&#9472;sdc1 ext4   232.9G            Data
sr0            1024M  
```

sda2 is /root (should I label it?)
Windows on the ntfs partitions

Want to keep Windows and home.

---

### Post by yancek on 2019-03-07
> got message No root file system is defined

In the installer window, when you select the partition for the " / " (root filesystem) you need to click the Change button below the main window and select the Mount point option " / " which is the first option from the drop down menu.  So in your case, if you want sda2 as the / partition, click sda2 in the main window, click Change and then select / for Mount point.

---

### Post by Impavidus on 2019-03-07
Select sda2, click "change", set the mountpoint to / and mark it for formatting. Select sdb3, click "change", set the mountpoint to /home and make sure it's not marked for formatting. I think the installer should recognise the efi and swap partitions automatically. Unless you have some special needs, there's no need for /var and /usr partitions.

---

### Post by KieranFitzgerald on 2019-03-08
16.04LTS installed and mostly working.  I can't boot Windows .  Ran boot repair from live session.  No change.

Report at [http://paste.ubuntu.com/p/zYPk8xDctp/](http://paste.ubuntu.com/p/zYPk8xDctp/)

---

### Post by KieranFitzgerald on 2019-03-09
Starting new thread

---


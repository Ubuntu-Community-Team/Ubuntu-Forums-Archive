---
title: "replace mint with ubuntu"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by steveredshaw on 2017-07-29
I have recently come across Ubuntu Studio and have dual-boot installed it with my existing Mint OS. Mint is on a 20GB boot partition, my files are on have the /home partition has been resized to accommodate Ubuntu Studio when I installed that - both those partitions are about 400GB.

Now I wish to replace Mint with Ubuntu Studio, installing it to the 20GB partition - I am confident about doing that.

Having done that, can I delete the previous Ubuntu Studio partition and resize the /home partition so I utilise all the hard disk again? If I do that will the grub menu be messed up - at the moment it shows options to boot Ubuntu Studio and Mint?

thanks.....

---

### Post by oldfred on 2017-07-29
Unless previous Studio happens to be the partition just after /home it will require some or perhaps lots of shuffling. And moving the start of a partition can take a very long time, and if int interrupted will cause data loss. So have good backups,  which should be normal practice, anyway. 

Post this:
sudo parted -l

Be sure to use Something Else when installing and include /home partition as new /home in the install, but be sure to NOT check the format box or all your data will be lost.

---

### Post by steveredshaw on 2017-07-30
Thanks for that - yes Ubuntu Studio is on partition next to /home (the 486 GB partition is the one with my files on)

```
steve@steve-ubuntu-studio:~$ sudo parted -l[sudo] password for steve: 
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  20.0GB  20.0GB  primary   ext4            boot
 2      20.0GB  1000GB  980GB   extended
 6      20.0GB  506GB   486GB   logical   ext4
 7      506GB   995GB   489GB   logical   ext4
 5      995GB   1000GB  5000MB  logical   linux-swap(v1)
```

---

### Post by oldfred on 2017-07-30
Then if the partition after /home, you just have to delete it & expand /home partition into unallocated space. That will be very quick. If the other way around, and you have to move all data left and then expand right would be the very slow process, depending on amount of data & speed of system/drive.

I typically allocate 25 or 30GB for / (root), and currently in my 16.04 install have used about 7.5GB. I do regularly houseclean and have most of my data in another /mnt/data partition on my HDD, sdb. I installs are on sda which is a SSD.

---

### Post by steveredshaw on 2017-07-30
:KS That went well, all changed over, files preserved and /home partition resized - even got previous menu items (from Cinnamon) showing up on the xfce Whisker menu! Also some previous bookmarks now appearing on Thunar!! The only thing I could not do is get Libre Office (latest version) menu items in the Office category, but that's not a huge problem, I am still working on that.

Ubuntu Studio is a lot snappier than Mint on my laptop and the range of software - audio and graphics - are just the tools I need to be using

Thanks for the advice and reassurance....

---


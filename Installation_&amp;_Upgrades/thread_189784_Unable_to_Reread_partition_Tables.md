---
title: "Unable to Reread partition Tables"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Flashstar on 2006-06-05
I have a 120gb external USB drive connected to my computer which I am attempting to install Dapper to. I've heard that Dapper has USB boot support so I should be able to install it like a regular hard drive right? Anyway, I had a ntfs partition on it with windows files so I just clicked reformat entire drive when I was installing. All was fine untill the progress bar reached 15% at which point an error message came up warning me that it could not edit or read the partition. I then decided to open up the partition manager and all it said was that it could not reread the partition tables on my drive. It then said that this would result in limited functionality. Sure enough I was unable to edit the main (ext2) partition. (It did seem to create an extended, ext2, and swap partition though.) So then I thought that the problem was that I was trying to format a NTFS partition, so in windows I formatted the drive with a logical FAT32 partition. Again in linux I recieved the same error. I was able however this time to modify the ext2 partition, but as I was trying to convert it to a FAT32 partition again just for yucks, it failed and gave me another error at about 34%. This resulted in an "unknown" partition being produced. Currently I am trying again by formatting the drive in Windows with a primary ext3 partition and a logical swap partition. If anyone has any advice, it would be appreciated. Remember, this is an external USB drive. Thanks

---

### Post by Flashstar on 2006-06-05
EDIT: I just opted to use the ext3 and swap partitions that I created in Windows so the installation seemed to work, but I ran into a grub error 17 when I tried to reboot. :( What should I do?

---

### Post by Flashstar on 2006-06-05
I guess I will just take the hard drive out of the external enclosure and put it inot my computer.

---


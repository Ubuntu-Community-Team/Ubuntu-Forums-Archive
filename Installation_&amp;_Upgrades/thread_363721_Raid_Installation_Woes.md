---
title: "Raid Installation Woes"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by kragen on 2007-02-17
Ok, I've just bought myself a new 250 GB hard drive, identical to the first one that I already have. I have a Asrock ConRoeXFire-eSATA2 motherboard, and I want to install a windows - linux dual boot system - 50-100 GB assigned for windows, the rest assigned for linux,both installed on a performance raid.

First thing I did after putting the extra drive in was go into the BIOS and set the drives to RAID mode, next time I boot up, I get an extra screen displaying some info about the RAID, and need to press <Control><I> to boot up a RAID config menu in which I set the two drives up as part of a raid 0 array.

Next thing I do is to try and install windows (vista). I boot up the dvd, enter all my details, when I come to the partitioner stage I see one large block of unpartitioned space, I assign 50 Gb of it as an NTFS partition and continue to install windows seamlessly.

I then move onto installing linux, I boot up the 64-bit Alternate install CD (the one for raids), and when I get to the partitioner it see's two disks, each 250 Gb, the first one has 50 Gb partitioned, the second one has no space partitioned. At this point i'm a little confused, so I decide to start again and wipe all the partitions. I create two sets of identical partitions on each (1 swap partition and one big one for /), and create them as raid partitions, then goto the "create raid" option at the top and create what I think is two raid partitions - one from the two 1 GB partitions, and one from the 2 200 GB partitions. When its done I come back to see 3 devices - a raid array with a 2 Gb and a 400 Gb partition, and my two drives, each with 50Gb free space. I assign my two partitions as swap / ext3 ext... and continue onwards. 

At the end of the installation, GRUB fails to install a boot loader and linux wont boot. (I think there is a problem with the CD - it did this when I tried to install "normally" on one drive, no raid, to fix it I had to boot into another live CD - the normal non-64 bit one to get it to work at all, even then it took some doing.

I then move onto trying to install windows again, thinking that it should see 100 GB free space, and 400 Gb partitioned space, but instead it see's 50 Gb free space, followed by 1 Gb partitioned space, followed by 200 odd GB partitioned space, followed by 250 Gb free space. 

I'm totally lost - what the hell is going on? Why doesn't windows recognise the raid properly, and how the hell am I meant to install a boot loader onto my Ubuntu installation? Also, have I partitioned my raid correctly in my Ubuntu installation? (apart from the fact I'm lacking a /boot or /home partition etc...)

---


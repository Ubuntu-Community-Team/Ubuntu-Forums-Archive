---
title: "Trying to shift Ubuntu"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2008-05-29
Hi, I'm trying to shift ubuntu from my current hard disk to a faster hard disk. 

I found many great guides on how to do that, and maintain the boot status. But, my problem/concern is that currently my Ubuntu's home folder is not on a separate partition.

I'd like to move my ubuntu to one partition and link the /home to another partition in the seperate hard disk.

I've backed up my home folder, but I was wondering if I did create the partition image, or use 'dd if=/dev/sdbx of=/dev/sdax', it'll just transfer  it with /home also. 

Currently my ubuntu partition is 60gb and I'd like to transfer it to 25gb    ( / ) and the home folder on a seperate, bigger partition. 

If I were to backup my home folder, is it safe to delete the original then create the partition image? I'm very concerned that if I were to do that, all the links to home would be messed up after shifting, and it might not even boot up. It's my first time trying to do something like this. 

Or I'm thinking I install a fresh copy of ubuntu on the new partition and specify home as I want it, and then slowly transfer my settings. I hope it wouldn't come to that. 

I need advice on how to do this, which is the best way.

All ideas are welcome.

---

### Post by ridgeland on 2008-05-31
Hi psycho5,

I use $ sudo cp -a 
to move partitions around and to make backups.
I can restore with just $ sudo cp -a and when it restores to the same partition all is fine.  Easy for a backup and restore.
It also works well for moving an OS from one partition to another, or just creating a clone OS for testing new software you don't full trust until you've seen it.  In this case you MUST edit /etc/fstab in the new copy and also edit GRUB's /boot/grub/menu.lst.
Do not use "cp -a" on the current OS.  That is to backup Ubuntu using cp -a boot into Mandriva to do it.  To back up Mandriva boot into Ubuntu to do it.
I use something like:
$ sudo cp -a /Ubuntu/* /DataPartition/Ubuntu_backup/

Also a note on strategy.  I partition with OS in 10 GB partitions and have a /Data partition of 150GB.  I leave /home in the root partition but keep all the Music, Photos etc in /Data.  My logic is /home is for settings which are OS dependant.  /Data is for OS independant files likes Music, Photos etc.  All the OS share the /Data partition.  I have Ubuntu 7.04, 8.04, Mandriva 2008.1, Fedora 8, 9, SuSE 10.3 and Xubuntu on this PC.  None have a large /home.  I really only use Mandriva and Ubuntu but I can play with the others to see how they solve a problem I encounter.

To do what you are wanting I would try this:
Copy /home to the new partition (sda9 for example)
Verify it works fine by changing /etc/fstab and booting.  Add something like this to /etc/fstab
/dev/sda9/home /home ext3 defaults 0 0
Reboot - $ df --- to see if it mounted OK.
Then you can edit something in /home. Comment the new line back out of /etc/fstab and boot again.  And see if you have the old /home back.
If it were a PC I was planning to support long term I would run Disk Usage Analysis to see why /home is so large and move the none settings files to a new partition /Data and then use cp -a to move whats left (including a small /home) to a new smaller partition (of about 7 to 10 GB).
Have fun.

---


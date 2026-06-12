---
title: "Dua booting ubuntu/xp failure!!!"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by justsomelinuxuser on 2007-12-22
I am using a fairly new Dell Dimension 8400 Desktop computer with about 80 gb of HDD space, and 1gb of ram.

I was using Ubuntu Linux as a primary OS for a while. I have decided to dual boot ubuntu 7.10 with win xp media center  edition 2005. This is how I did it: 
I first backed up my home directory into an external HDD drive, so all my photos/music and files are safe and intact. Then, I used the Ubuntu 7.10 Live CD to repartition my HDD (there is only 1 HDD, I am not using any RAID array) so that where will be 3 partitions (one ubuntu, one xp and a linux swap partition). After that, I booted back in to my normal ubuntu (not using the live cd) to check if everything was alright. And everything was, except that my HDD space was a bit smaller (which was good). 
Now, I put the XP MCE 2005 install disc and restarted my computer and told it to boot off of the disc, I told it to install on the partition i made for it ( am sure that I installed on the right one) and told it to install. It went through the normal process and when it was completed, I restarted and it turned out, It did not go into GRUB. It only went to XP. I tried rebooting, bot every time, it always booted into XP, bypassing GRUB. So, in XP I went to a partition manager (it was one of their system tools) to find out there were 2 primary partitions. XP and Ubuntu7.10. After that, I booted into Live CD and used the partition manager. I looked aroung in GParted and flagged the Ubuntu partition to 'boot'. I thought this was going to work, turns out, It did not boot at all. I undid it.  I got frustrated. Back in Ubuntu Live cd, I went online and I saw a thread of how to reinstall GRUB. ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) and did it. I rebooted then all I see now is "No boot Device". Now, I dont know if some one else out there has the same problem. So if there is, please redirect me. Otherwise, Please respond. I am a linux n00b. thanks! :)

---

### Post by bhavard on 2007-12-22
I had a similar problem. I installed XP Pro, leaving app. 9 GB for Ubuntu Christian Edition install. I then booted the live cd, went to the install icon and everything went fine, except when I tried to boot back into XP it detected some problem, did a scan of the disk, then rebooted fine. The problem now was to get XP to be first on the boot options as I am new to Linux. using Partition Magic I tried to add "boot magic"  to the computer - it need some free space, so I proceeded to free up  some using Part. Magic. Now, I'm going to have to reinstall everything as nothing works

---

### Post by Pumalite on 2007-12-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---


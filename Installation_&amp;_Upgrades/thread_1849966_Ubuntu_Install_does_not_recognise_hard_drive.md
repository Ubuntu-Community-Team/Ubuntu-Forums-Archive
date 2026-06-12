---
title: "Ubuntu Install does not recognise hard drive"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by King Big Ben on 2011-09-25
Still a bit of a Linux newbie here. I am installing 64 bit Ubuntu onto an old 64 bit Athlon machine that I have lying around. It boots into the installer fine yet it does not list my hard drive. I quit the installer and tried out the version just on the cd, which actually mounts the drive! it showed my old folders from windows and everything! I tried the installer again, and it still could not find the drive. I then tried GParted, and set up new partitions on the drive, creating an ext4 partition and a 2 gb or so swap partition. I tried the installer again after this, and still no luck.

I built this machine a long time ago, and from what I can tell, I believe the hard drive is set up on some kind of RAID system, but I'm not sure. 

Thanks,

-Ben

---

### Post by YesWeCan on 2011-09-25
Hi there. One possible cause is the presence of mobo RAID superblocks on your disk. These (erroneously) cause the Ubuntu installer to "not see" the disk at all.

Boot the live session and run
[COLOR="DarkSlateBlue"]sudo dmraid -s[/COLOR]
To see superblock info. if there is any.


If you are sure you are not using Windows/SATA RAID (preferably disable all RAID options in the BIOS) then run
[COLOR="DarkSlateBlue"]sudo dmraid -E -r /dev/sdx[/COLOR]
where x is the letter of your drive.

---


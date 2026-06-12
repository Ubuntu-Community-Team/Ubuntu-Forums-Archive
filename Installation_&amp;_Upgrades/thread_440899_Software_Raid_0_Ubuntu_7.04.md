---
title: "Software Raid 0 Ubuntu 7.04"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by dlouwers on 2007-05-12
Yesterday I tried to get Ubuntu up with Raid 1, using the 7.04 alternate cd, for most part of the day to no avail. First I tried the methods listed in [http://users.piuha.net/martti/comp/ubuntu/raid.html#3]("http://users.piuha.net/martti/comp/ubuntu/raid.html#3")
Unfortunately this didn't work. The boot loader didn't even kick in, I just got a black screen with a white blinking cursor on boot. When using the Live CD and choosing the option to boot from harddisk I got a Grub error 15.

The second time trying to install my system again, this time planning to make a tiny boot partition at the start of my disk instead of a root partition right away, the strangeness started. I deleted my previously created partitions and made some new ones. Then I went on to configure software RAID. Here I saw that my previous MD devices were still in existance but obviously they aren't correct anymore so I tried to delete them to no avail: "Failed to delete the multidisk device. (...) It may be in use." I see no disk activity whatsoever...

Can anyone please help me here? It seems that I cannot use the installation program anymore since it keeps the old multidisk information and does not allow me to delete it.

Regards.

---

### Post by dlouwers on 2007-05-12
Update:

I have tried to manually remove these md partitions from a second console. I failed and removed a few partitions. However two don't let themselves be marked faulty and will not be removed. cat /proc/mdstat now looks like:

md2 : active raid1 sdb3[1]
    95739264 blocks [2/1] [_U]

md1 : active raid1 sdb2[1]
    1951808 blocks [2/1] [_U]

unused devices: <none>

I have the suspicion that the installation software writes them back from memory every time. I will load a command line interface and try removing these devices there.

---

### Post by dlouwers on 2007-05-12
Ok after another restart after manually marking all md devices as failed I started installation with a clean md table. I tried to wait for the array to fully rebuild after installation but the system restarted itself after a few minutes on the last screen...
Afterthe restart I was once again greeted by a blinking cursor and no disk activity. The same happened when choosing "boot from first hardisk" from the alternative cd. However after choosing "boot from first harddisk" from the standard cd the system booted up, slowly, displaying all boot-up data instead of showing the splash screen. After logging in I clicked "Places" in the top menu and the system froze completely. Not even my mouse cursor was moving anymore so I had to do a hardware reset.

After another reboot using the Live CD as a kickstart I normally booted into the system. /proc/mdstat showed my raid to be rebuilding so I am waiting on that before doing any updates and the sort.

I verified that only md devices are mounted. That was the case. I also setup grub on sdb to try and make it bootable when a failover occurs. I will do this with sda as well if it fails to boot after the resync of the array.

---

### Post by dlouwers on 2007-05-12
When the synching process for my last partition was at 17% the system frooze and did an automatic reset. After the reset Ubuntu gets stuck on the loading screen with the progress bar at about 2%. After that I get a busy box starting Read-error on swap-device (9:1:8. /bin/sh: can't access tty; job control turned off (initramfs). 
I am now utterly and completely at my wit's end and cannot think of any other action to take. I sincerely hope that someone will be able to help me solve this or point me in the right direction. I will try this week to get it all up and running again. Else I'll have to give up and get XP up again :(

---

### Post by dlouwers on 2007-05-14
It appears that something is dreadfully wrong with my SATA controller. I have downloaded SeaTools from the Seagate site to scan my drives. This has resulted in the scanning software actually crashing on several occasions.
Ran a full memory test. My RAM seems to be fine.

Any suggestions would be most welcome.

---

### Post by think!! on 2007-05-17
Hello dlouwers,
I had the same problem to day, it seems its a bug. :(
But there is a way to solve. I had a ubuntu 5.10 lying around at home and I started the installation with it and there I was able to delete the virtual raid sections. :) I started the partition and after that i killed the installation.
Perhaps it also work with a later version of Ubuntu. 

think!!

---


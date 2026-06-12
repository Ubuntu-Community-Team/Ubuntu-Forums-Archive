---
title: "Ubuntu 6.06 LTS installation issues"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by FraserGreen on 2007-09-29
Hello, I am installing the Ubuntu 6.06 LTS desktop. My system is as follows:

Intel(R) Core(TM)2 CPU 6700 @ 2.66GHz
NVIDIA GeForce 8800 GTX   768MB
ASUS StrikerExtreme with SoundMAX Integrated Digital HD Audio
2.0GB 800MHz DDR2 RAM
500GB SATA HDD
TSSTcorp CD/DVDW SH-S182M

The system already has Windows XP Professional installed on a partition with 350GB, and I am trying to install Ubuntu 6.06 on the second 150GB partition. These partitions were made when I installed XP. I first attempted to install Ubuntu from the desktop CD, however the installation would get to 94% and error out. However I do not recall the exact error message, though IIRC it was something involving GRUB. On my second attempt at installation I recieved the error message:

"The ext3 file system creation in partition #2 of SCSI4 (0,0,0) (sda) failed."

So I cannot start the Ubuntu installation now to see what the error message at 94% was, as it will not start now! I have searched the forums for similar issues, however I did not find any solutions or similar problems. Help would be appreciated, I would like to get Linux up and running because I have started an MSc in Computing and it would be very useful.

Regards,
Fraser

---

### Post by FraserGreen on 2007-09-29
Anyone? :(

---

### Post by Pumalite on 2007-09-29
This might be your problem: NVIDIA GeForce 8800 GTX 768MB
It's too new. 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by rsambuca on 2007-09-29
Your PC has some pretty new specs.  I really think you would be better off trying the newest version of Ubuntu, 7.04.  You might even consider waiting a couple of weeks and using 7.10 when it comes out.

---

### Post by Pumalite on 2007-09-29
That's a great idea!

---

### Post by FraserGreen on 2007-09-30
Thanks for the replies, however it's not the graphics acceleration I am having trouble with, I just can't get the installation to start.

[Edit: Spelling]

---

### Post by Pumalite on 2007-09-30
Try the Alternate CD:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark 6.06 server and then mark box below green sign 'Start Download'

---

### Post by tgalati4 on 2007-09-30
Only 150 GB for an Ubuntu partition?

Dapper comes with an older version of GRUB that trips up with certain RAID/SATA drive configurations.  Try Feisty, or better yet, give Gutsy a spin.

If your drive is a Hitachi Deathstar, then I've experienced problems with the 500 GB model.  They need breaking in and checking.  Do a security erase to make sure that the entire paritition is writeable.

---


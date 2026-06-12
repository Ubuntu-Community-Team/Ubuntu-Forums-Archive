---
title: "new install woes"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by kelvin45 on 2008-06-11
I'm a complete beginner to Obuntu. got the linux starter pack.
When I try to install it (option 1 on the menu)
I get the following message "cannot allocate resource region 3 of device 000.00000"
the install continues until the screen goes blank (apart from a flashing curser in top left) and I then get 134.600000 HDB: timeout waiting for dma and 140.000000 HDB: drive not ready for command.

I am using windows xp pro and a sata hard drive,(with plenty of space).

any help gratefully recieved

kelvin

---

### Post by Vivaldi Gloria on 2008-06-11
1) I don't know anything about the linux starter pack. Does it come with a single dvd or does it come with different cds, one for each operating sytem? That is, do you have a seperate cd for ubuntu?

2) You mentioned some options menu. I have attached a snapshot below. Are you talking about that one?

3) Are you aware that if you have a single hard disk with a single partition and install ubuntu on it then it will delete windows (unless you use wubi)?

---

### Post by Pumalite on 2008-06-11
They the Alternate CD. Download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Check the box below sign 'Start Download'
Use this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, bur at 4x or less on CD-R
If not I'll give you some boot parameters.

---

### Post by Vivaldi Gloria on 2008-06-11
kelvin45

Download and watch the videos (links below) to get a better feeling for ubuntu. They are for the previous version of ubuntu but still relevant. I suggest you especially watch these:

Installing Ubuntu Part 1
Installing Ubuntu Part 2

and maybe also

Tour of the Ubuntu Desktop 
Tour of the Ubuntu Applications
Tour of the Places and System Menus 
Updating and Upgrading 
Installing Applications 


These videos are available in different sizes. Goto

[http://screencasts.ubuntu.com/MoS2007](http://screencasts.ubuntu.com/MoS2007)

and click one of the links on the right. I attached a snapshot.

---

### Post by Pumalite on 2008-06-11
Keep this in mind too:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by kelvin45 on 2008-06-14
Hi Vivaldi Gloria
The Starter Pack comes with 1cd with ubunto on, according to the instructions when it starts the install it will make a partion on my main drive (wubi is included as part of the install)

Yes that is the menu I mean.

Kelvin

---

### Post by kelvin45 on 2008-06-14
Thanks to both of for the info, I am slowly going through the various links etc, I'm also going to try to install my current cd on my laptop, see if I can get a versionjh on there taht I can at least play with.

kelvin

---

### Post by Pumalite on 2008-06-14
Download the iso from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum,burn at4x or less
Install XP first, Ubuntu last. Let Grub install to the MBR.

---


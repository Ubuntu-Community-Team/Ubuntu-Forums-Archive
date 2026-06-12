---
title: "Unable to install Lubuntu 12.04 on Compaq Laptop"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by bailey1399 on 2012-07-05
Hey, I'm new to any form of Linux, so forgive any stupidities/failures I make. I made an account on here specifically for this issue. I'm not sure if this is in the right place, but here I go!

I have found an old Compaq Presario 2500, with 191 MB of ram, 2.6 GHz Celeron processor. It ran Windows XP, but I have wiped the drive to install Lubuntu. I did some research around the different variations of Ubuntu, and decided that Lubuntu would be my best choice. So, I created a Live USB with "UNetBootin" and managed to get the live demo running pretty well. So, I clicked install, and after a couple of minutes the installation window popped up. I went through the installation untill it got to partitioning the drive. Apparently it still had Ubuntu 12.04 LTS that I had attempted (and failed) to install earlier. So, I chose to wipe the drive (I think...) and it came up with some error messages about unable to partition the drive. I'm really not sure what's going wrong here, I'm experienced with computers, I have been using Windows for years, and know a little bit about Macs. But, I have never used Linux before in my life.

I appreciate any help that you guys can give me, thanks in advance!

---

### Post by leclerc65 on 2012-07-05
Choose option 'Something else'... and handle the partitioning youself.
Worse comes to worse, download a Parted Magic CD, that can be valuable to you for years.

---

### Post by Bucky Ball on 2012-07-05
Welcome. 

Perhaps try this: Boot from the USB to a Live session. Open Gparted (Partition Manager) and that will show you exactly what is on the drive, partition-wise. Whatever you find, delete, so you have just free space, no partitions.

Partitions need to be unmounted to manipulate them so right click on the partition in Gparted and 'unmount', although any partitions should be unmounted already. Best to check. ;)

... and as mentioned in post #2; 'something else' and manually partition. Ubuntu doesn't always cough up the setup you want when left to its own devices with an 'automatic' install. I generally go for something like:

/ = root; operating system, etc.;
/home = your personal data. 'Documents' 'Video' 'Music' etc ... big or small as you like;
/swap = 2Gb fine, last partition.

Having a separate /home partition means if you break the system you can install just the OS back to / without losing all your personal stuff in /home. If you don't designate a separate /home partition, the install creates a /home folder in /. 

Good luck ...

---

### Post by bailey1399 on 2012-07-06
Thanks for the help, Bucky Ball, I'm trying your suggestion now.

I was also wondering, is this computer actually powerful enough to run Lubuntu? Or will I have go with an OS such as Puppy or DSL?

---

### Post by Rex Bouwense on 2012-07-06
You should be able to run Lubuntu with only 191 Mbs of RAM, however RAM is so inexpensive now that adding another chip or increasing the size of the what you have will not hurt.

---

### Post by bailey1399 on 2012-07-06
Alright, thanks. I don't think I will buy any RAM for it, because I won't be using it daily. It is really just a little project for me, to try out Linux for the first time. I am going to be giving it to my little sister. :D

---

### Post by bailey1399 on 2012-07-06
Umm, guys, I have a problem. Whenever I have done the partitioning, but now whenever I click "Install Lubuntu 12.04" it freezes up, and nothing happens. I have tries rebooting the computer but this still happens. Help please!

---

### Post by overdrank on 2012-07-06
It could be related to the 191 MB. I do not believe this is enough memory.

---

### Post by Rex Bouwense on 2012-07-06
Good point.  While 191 Mbs might be enough to run Lubuntu, it might not be enough to install.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by bailey1399 on 2012-07-06
I have been able to get into the installation before though...

---

### Post by Rex Bouwense on 2012-07-06
You have been able to get into the installation but by your own admission you have not yet successfully installed.  You can continue to try to install with marginal RAM.  You can try the minimal install.  You can try another OS (DSL or Puppy come to mind.)

---

### Post by Bucky Ball on 2012-07-06
Yea, the mini.iso, although more involved, is a good way to go. Just installs the base Ubuntu (used by all the flavours, including Lubuntu) then the rest is installed via the network, and only the things you ask for (no apps are loaded by default).

This means can then install lxde, the desktop environment for Lubuntu, any other apps you are intending to use, and take it from there. You wind up with a fast, sleek, fully customised install. I would be careful though as with that little RAM there is going to be a definite limit to how far you can stretch things. ;)

Find more info here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by bailey1399 on 2012-07-08
Thanks for all your help guys, but I have installed MacPup on this laptop, and it runs like a charm :D I have a few other computers that I am going to install Ubuntu on though, some higher specced ones (P4 2.5 GB RAM & Atom 1 GB RAM)

Thanks to everyone posting on this thread, I appreciate all of your help!

---

### Post by Bucky Ball on 2012-07-08
Cool. Please mark thread as solved from Thread Tools to help others. Good luck, enjoy the system and the learning curve. ;)

---


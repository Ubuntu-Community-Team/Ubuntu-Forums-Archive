---
title: "Ubuntu server, booting from USB + partitioning"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Dmitry13 on 2010-11-17
Hi, everybody!

I have a small question regarding partitioning of a USB Stick and an HDD during installation Ubuntu server.

Input : 1 GB USB Stick + 250 GB HDD

Output : I would like to boot Ubuntu server from USB Stick and use HDD as some file storage(/storage) and for http server files (/storage/www), so I want to keep HDD in STANDBY mode most of the time. 

Server is for my personal use at home.

What I already tried was following : 

USB - 100 MB(/boot) ext2 ,800 MB (/)ext3 , 100 MB (swap)
HDD - all space (/storage)ext3.

at some point ubuntu complained that there was not enough free space left on USB.

How differently can I partition these two devices so that some parts from usb stick would go onto hdd, at the same time that wouldn't trigger hdd too often? Which folders are not accessed by the op.system frequently? for instance /home or some others? Also, which ones would make difference in releasing  space if are moved on hdd?  

How would you partition having such devices with keeping in mind that hdd should stay in STANDBY mode as much time as possible?

thank you in advance.

P.s I know I can buy a bigger USB stick, and solve the problem. But it's not my way. So, please do not suggest that. 
I would highly appreciate reasonable thoughts about it.

---

### Post by cybergnome on 2010-11-17
My reasonable thought is that your expectations aren't realistic given the size of the stick and your desire to have your HDD in standby.  Of course, you may need to see that for yourself.  ](*,)

---


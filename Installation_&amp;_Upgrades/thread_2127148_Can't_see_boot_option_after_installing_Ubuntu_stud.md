---
title: "Can't see boot option after installing Ubuntu studio with Windows7 ultimate"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by Shovan Roy on 2013-03-19
Hello to all- This is my first post. I am using ubuntu since 2 years. I have a windows 7 ultimate(32bit) in my PC. Previously I used wubi to install ububtu. But now I am thinking to install ubuntu studio. I have downloaded the ubuntu studio 12.04 LTS version from internet. I burned a DVD with .iso file and created a partition of 20GB on my hard disk to install it. I successfully installed ubuntu studio on that partition in ext4 file system. It was fine. The system automatically shut down after the successful installation process. Everything was fine till now. But when I restart my computer, I didn't see the ubuntu studio boot option!!! It's directly starting the windows operation system. I was so surprised at this situation. I searched internet in various forums but i didn't get the reason. Do you know the reason for this? I am so much confused.:confused:

---

### Post by oldfred on 2013-03-19
Best to see details, but if you just did not install grub to MBR, this will also let you fix it.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---


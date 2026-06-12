---
title: "Installing Ubuntu Server 18.04 - some questions to make a better start for version-II"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by pepper662 on 2019-01-23
Goodday Ubuntu-experts,
  I am trying to make a home server and I have a very basal question that is perfectly fit for a forum because it is both essential as basal and I can not find the exact answer on the fora until now. I am fairly handy around windows and MacOS but relatively new on linux.
   
  The situation: 
  I am trying to make a home server for 3 services;
  
[LIST]
[*]Owncloud
[*]Plex media server
[*]Samba LAN server
[/LIST]
   
  The hardware I have:
  
[LIST]
[*]Old but sufficient;      motherboard, CPU and RAM (not important)
[*]2,5 TB hard disks (1x 1,5tb      and 1x 1tb)
[/LIST]
   
  I already made server version 1.0. The server was up and running and providing all the needed services. I am contemplating how I will proceed now. I will make server 2.0 (fresh install). Now I added the secnd harddrive. I wanted to install ubuntu on a logical volume. What I did; during the install I made a LVM from the two availlable hard drives. From this volume group (2,5 Tb) I made several logical volumes. I mounted all selectable mounts (e.g. /Var, /Home). But if I do that I can not continue. Here is where I am stuck!
   
  The concrete questions I have:
  
[LIST]
[*]How can I continue? I do not      seem able to mount the /boot on a logical volume?!
[*]How much space should I      reserve for what mounts? Like I said I am only using owncloud, plex and      samba. I would like to use most of the availlable space for these      services.
[/LIST]
   
  That was it for now. I would be very grateful for an answer on these questions. Then I can finally make progress for my second attempt to make my house-server 2.0.
   
  Greets,
   
  Pepper662

---

### Post by SeijiSensei on 2019-01-23
I've built a lot of servers. I stopped using LVM years ago because it wasn't worth the effort.  

My current home/office server consists of a single drive on which Linux is installed, a pair of 1 TB drives in a RAID 1 for /home, a pair of 3 TB drives in a RAID 1 array where I store video and music, and a 4 TB USB external drive for backups.

---

### Post by pepper662 on 2019-01-23
Hi SeijiSensei,

Thanks for the response. So you would divide it physically! That is ofcourse an option that is always there! Thanks. It seems a bit old-skool but you seem to have quite some experience with it so wise for me to follow!

Need to find me some more disks :)

---

### Post by Tadaen_Sylvermane on 2019-01-23
You need a backup of course but mergerfs pooling is a good way to use all space without relying on lvm. Great for media especially. I do it at home.

---


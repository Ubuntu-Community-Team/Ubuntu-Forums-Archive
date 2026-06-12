---
title: "Server partition size for /root - longevity and LVM"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by npinn001 on 2014-04-22
I'm going to install tonight using LVM. When I tested an install last night I chose guided LVM and it installed a /root partition of 250GB (the whole drive).

I usually add a seperate /Home partition, and I use a seperate drive altogether to store files and media.

My question is, if I wanted to have a seperate /root partition, what size would be good for a server on a 250GB drive.

Second question is, do I even need a seperate /home partition. What I dont want to do is limit the server. The only benefit I saw was maybe for backing up the /root partition and if it was smaller this might be better?

Thanks

---

### Post by tgalati4 on 2014-04-22
20 to 25 GB would allow some room to add services and room for log files which can get big if the server develops a problem.  If you want to run a Content Management System (CMS) such as Drupal, you would need to consider how much room you need to store the content.  A separate partition for /home depends on how you are going to use the server.

What services do you plan to run on this server?  How many people will be using it?

There is no right way to set it up.  You want to minimize the agony units of maintaining the server and only you can measure that.

---

### Post by npinn001 on 2014-04-22
> **tgalati4 said:**
> 20 to 25 GB would allow some room to add services and room for log files which can get big if the server develops a problem.  If you want to run a Content Management System (CMS) such as Drupal, you would need to consider how much room you need to store the content.  A separate partition for /home depends on how you are going to use the server.

What services do you plan to run on this server?  How many people will be using it?

There is no right way to set it up.  You want to minimize the agony units of maintaining the server and only you can measure that.

Thanks, its just me that will use it. All the main content will be stored in VMs. Basicaly, a storage hard drive (separate) will house all my media files. Then I'll be running VMs on top of a base install. I dont need a seperate home for anything really, but it was more for security or error checking/backup benefits?

---


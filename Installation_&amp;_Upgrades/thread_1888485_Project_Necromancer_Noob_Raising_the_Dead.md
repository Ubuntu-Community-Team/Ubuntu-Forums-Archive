---
title: "Project Necromancer: Noob Raising the Dead"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by nickreinvented on 2011-11-29
Hi there everyone!

I'm launching a new project here since I found myself being given two dual processor P3 servers and two 12 HDD JBODS.  I hope to get a Ubuntu media server built for the house.  Unfortunately, I am nothing more than a basic Linux user and have no server experience other than with RDP and Web Servers (Linux and Windows).

I have performed the install about three times now and am still having some major issues understanding the JBOD and RAID.  I'm using an Adaptec 7899 SCSI card in the server, but I have had no experience with SCSI or RAID. (Being born in 1988 explains the SCSI part!) 

Currently, I've got a dual channel AVID JBOD which is housing 15K 73GB HDDs.  I would like to use a single channel, 6 HDD, per server.  I was given two.  I talked to a fellow tech here about the benefits / downfalls of RAID and was explained RAID 5 will accomplish a balance of speed and reliability.

My reason for posting this?  I am going to need support as I have no done anything with server software / hardware.  I may be getting in over my head at the moment but, I have installed 10.04 three times and I know what doesn't get me to my goal so I am learning!

Here is a picture of my project (necromancer), thought it was appropriate since I feel like I am reviving the dead.

This is both JBODs and Servers:
[IMG]http://i3.photobucket.com/albums/y89/Twitched1/WP_000235.jpg[/IMG]
[IMG]http://i3.photobucket.com/albums/y89/Twitched1/WP_000233.jpg[/IMG]

---

### Post by nickreinvented on 2011-11-29
Okay well this time I was successful in getting Ubuntu installed and I can see the drives in /dev but I am not sure how to get the drives formatted and set in a RAID array.  I tried [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) but I didn't have much of the same in the initial install.  I am guessing it is because I'm using a JBOD.

Anyone have any ideas while I research?

At this point I have Ubuntu 10.04.3 LTS installed on my primary (0) drive in the server itself.  There are two other HDD in the server alongside (1) and (2).  They, meaning the server and the JBOD, should all display the same though right?

---


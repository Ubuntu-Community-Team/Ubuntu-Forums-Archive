---
title: "Command Line Install Mass Deployment?"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by rustyhann on 2010-03-23
I'm working on building a large production render farm using farmerjoe.  I've built the correct setup using a server, master, appserver and slaves on 8.04.  I've done a command line install and installed only a few packages:

[INDENT]nfs-common and nfs-kernel-server[/INDENT]
[INDENT]dhcp3[/INDENT]
[INDENT]blender and imagemagick[/INDENT]
[INDENT]the scripts to make farmerjoe work[/INDENT]

I now want to be able to rapidly distribute this system and have a way to restore any part of it in the event of hardware failure or any other such disaster.  I've looked into rolling a livecd using remastersys, but I could not get it to replicate my custom /etc/fstab files, dhcp config, and networking configs to properly run farmerjoe.  I have the farm setup to run on DHCP and a hardcoded IP address for the master so it is ok to have 100 plus machines with the same name, credentials, etc.  What I really need is an **EXACT** image that is deployed across the machines.

The only thing I can think of is to run a FOG server and image the base machines (server, master, slave, appserver) and then use FOG to push them to the render slaves (approximately 100) and any machines that die like the appserver or master.  I would like to find a better way to do this, especially if it could be through the use of livecd's (i.e. put the master cd in and that sets the machine up as the master, same for slaves and appserver).  The caveat to the livecd approach is that **EVERYTHING** has to be replicated correctly, as if using a binary identical image.

I've looked at reconstrtuctor, but can't find a command line version of any documentation.  Anyone have any ideas?

---

### Post by Dayofswords on 2010-03-23
Clonezilla sound like something you'd want
[http://clonezilla.org/](http://clonezilla.org/)

"Clonezilla, based on DRBL, Partition Image, ntfsclone, partclone, and udpcast, allows you to do bare metal backup and recovery. Two types of Clonezilla are available, Clonezilla live and Clonezilla SE (server edition). Clonezilla live is suitable for single machine backup and restore. While Clonezilla SE is for massive deployment, it can clone many (40 plus!) computers simultaneously. Clonezilla saves and restores only used blocks in the harddisk. This increases the clone efficiency. At the NCHC's Classroom C, Clonezilla SE was used to clone 41 computers simultaneously. It took only about 10 minutes to clone a 5.6 GBytes system image to all 41 computers via multicasting!"

server editions sound like the version for you

---

### Post by rustyhann on 2010-03-25
Thanks for the info on Clonezilla SE and DRBL :)  I've got DRBL installed and am working on customizing it to see how viable it is.  The idea of going to diskless slaves has a lot of promise and I hope to get it working.  I'll keep the post updated with my progress.

---

### Post by rustyhann on 2010-03-28
I have successfully setup and deployed my slaves for the render farm. Here is the problem. When the slaves are cloned, the MAC address from eth0 is also cloned, which creates problems. The solution to the problem is to open 
 
```

[FONT=Verdana][COLOR=#000000][COLOR=#000000][FONT=Verdana]sudo nano /etc/udev/rules.d/70-persistent-net.rules[/FONT][/COLOR]
[/COLOR][/FONT]
```
[COLOR=#000000][FONT=Verdana]and delete the MAC address mappings, followed by[/FONT][/COLOR]
 
```

[FONT=Verdana][COLOR=#000000][COLOR=#000000][FONT=Verdana]sudo modprobe -r pcnet32 [/FONT][/COLOR][/COLOR][/FONT]
[FONT=Verdana][COLOR=#000000][COLOR=#000000][FONT=Verdana]sudo modprobe pcnet32[/FONT][/COLOR][/COLOR][/FONT]

```
 
[COLOR=#000000][FONT=Verdana]NOTE: pcnet32 is the name of the nic[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]as per this thread:[/FONT][/COLOR]
 
[COLOR=#000000][FONT=Verdana][http://ubuntuforums.org/showthread.php?t=255018](http://ubuntuforums.org/showthread.php?t=255018)[/FONT][/COLOR]
 
This is by no means a useful way to deploy 100+ slaves in a render farm. It was also the reason I was looking to create a customized LiveCD using remastersys. The overall plan was to then put that custom LiveCD into ClonezillaSE and perform network installs as opposed to imaging operations and avoid the MAC address mapping problem. My problem with remastersys was that it would not preserve the customizations I had made to files like /etc/fstab and /etc/network/interfaces.
 
The ideal situation would be to create a LiveCD or other means of installation that includes the packages and scripts to run the farmerjoe render farm and can preserve the customized network, such as the hardcoded address of the farmerjoe server and the locations of the farmerjoe NFS shares. The scripts are very, very simple. The only command to run farmerjoe is farmerjoe.linux --master, farmerjoe.linux for the slave, and farmerjoe.linux --appserver for the appserver. I only have one entry in /etc/exports and /etc/slave (depending on the machine - master or slave).

---

### Post by rustyhann on 2010-03-28
The more I think about it, the more I realize I haven't had this problem with normal Ubuntu installations.  Is there something that is ran on startup of a normal install that isn't ran on a command line install?  Can you setup Ubuntu to wipe the MAC Addresses and re-modprobe the NICs at sytem startup?  It wouldn't matter if it extended startup time because these systems will rarely be restarted :D

---

### Post by rustyhann on 2010-04-11
I solved my problem by running the render farm on Windows XP.  Attaining the proper licensing was easier and more cost effective than having a Linux render farm that doesn't work and isn't deployable.

---

### Post by thomas_d_j on 2010-05-20
> **rustyhann said:**
> Attaining the proper licensing was easier and more cost effective

That's really sad.

Thanks for posting the follow-ups; always good to hear how the story ends and a good reference for the next guy and/or developers.

---


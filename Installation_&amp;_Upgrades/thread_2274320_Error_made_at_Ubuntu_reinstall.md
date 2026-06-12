---
title: "Error made at Ubuntu reinstall"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by maxcmel on 2015-04-19
I've just reinstalled Ubuntu 14.04 and have kept my home directory intact. My HD had a sda1 partition for the OS of 30gb, a sda3 of 215gb /home, a sda2 extended of 6gb that is marked in a light blue box  and lastly, sda5 Linux swap, also marked as 6gb inside the extended partition with a purple perimeter. 
I marked the sda1 for formatting and made sure the home directory was not!
However, I made the mistake of  not marking the old home bootable and now have 2 home directories. 
A new /home of 20gb (that is empty and created inside the former 30gb partition) and the old one that is marked as 215gb volume intact with an icon on the side bar.). I can access all my data, work with it or change it. It acts as a folder. 

I like to make the old directory the one that is mounted on startup and lose the new /home. Is there a way to accomplish that without too much trouble?
Any help will be greatly appreciated.  
maxcmel

---

### Post by Bashing-om on 2015-04-19
maxcmel; Hello;

I would think that is a function of ' /etc/fstab ' to effect what is mounted at bootup.

Might examine the file and see what is mounted presently .. then mount what you desire using the outputs:
```

sudo blkid
sudo fdisk -lu
sudo parted -l

```
as the reference to determine mountpoints and UUIDs.

Once partitions are mounted to your liking, one can repurpose the superfluous /home.

[INDENT][INDENT]or so I think
[/INDENT][/INDENT]

---

### Post by maxcmel on 2015-04-19
Thanks for your fast reply! I'll have to wait till tomorrow to figure how to do it after I have the answers to the 3 commands you presented. I know how to use Ubuntu and LM but am not well versed in the command section. I let you know how how I fared after tomorrow.

---

### Post by grahammechanical on 2015-04-19
Did you select sda3 and give it the mount point of /home? Did you keep the same username and password? Especially the user name? A re-install with a new user name would create a new user with a home folder in that users name. And so giving two user folders in /home with the original possibly not accessible to the new user.

Regards.

---


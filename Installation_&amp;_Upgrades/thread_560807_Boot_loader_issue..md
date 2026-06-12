---
title: "Boot loader issue."
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2007-09-26
Ok, so I managed to fix the whole trash on the Hda/Hdb issue, problem solved. In fact, don't ask me how I did it :confused:. So after managing to get it reinstalled I had a little issue, known issue in fact quite a few people here had it, I had read a few of their posts, none in relevance to my issue unless I did not read it correctly. So again, after reinstalling the Ubuntu Gnome(Ftw!) I noticed that it did not have the boot loader, keep in mind this was a legit installation through the GUI based portion, I read carefully all the instructions on the screen. After coming to the conclusion of what partitions were created for the installation(e.g., / /boot SWAP /usr /home) it did not what so ever install the boot loader. Now before I had the scattered issues with trash and what not, It installed perfectly  with the Live CD. I was told by articles and forum posts of ways to install the boot loader, but I am afraid that if I try once more to reinstall Ubuntu the boot loader will not install along with messing up my windows partition again. Frankly I'm sick of reinstalling windows and to the point of just having Ubuntu on my drive, but how do I know if I can get Ubuntu to pick up my Digital camera and installing Counter-Strike Source without an performance based issues?

---

### Post by Pumalite on 2007-09-26
Your digital camera is probably no problem depending on brand and drivers. As for games; you have wine. Not sure which games work and which don't. If you installed Ubuntu and you have access to it, post from Terminal:
sudo fdisk -lu

---

### Post by cowboy.bebop on 2007-09-26
Ok, so I partitioned my HDD once again, using Parted Magic on a CD. And after installing I executed the command 'sudo fdisk -lu' and this was the result:
> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   305829404   152914671    7  HPFS/NTFS
/dev/sda2       305829405   320159384     7164990    5  Extended
/dev/sda5       305829468   311966234     3068383+  83  Linux
/dev/sda6       311966298   312062624       48163+  83  Linux
/dev/sda7       312062688   316255589     2096451   82  Linux swap / Solaris
/dev/sda8       316255653   318311909     1028128+  83  Linux
/dev/sda9       318311973   320159384      923706   83  Linux
ubuntu@ubuntu:~$ 


In order these are their labels:
Primary: XP
Extended
Logical: /
Logical: /boot
swap
Logical: /usr
Logical: /home

S what I am going to do now is reboot my system and see if the boot loader was installed, if not I will be on another system to keep in contact.

---

### Post by Pumalite on 2007-09-26
You boot loader is installed. The question now is to know if you can access your Windows through Grub??

---

### Post by cowboy.bebop on 2007-09-26
Ok so I rebooted the system, and well yes I was able to access my windows partition cause that the only thing that booted up :lolflag:. I didn't see any GRUB appear on the screen sadly. Should I try setting the boot flag on /boot by using parted magic?

---

### Post by Pumalite on 2007-09-26
You had access to Ubuntu a minute ago and now you don't? I don't understand. How did you post : sudo fdisk -lu?

---

### Post by cowboy.bebop on 2007-09-26
Well I did 'sudo fdisk -lu before I rebooted after installing, I guess while it was mounted virtually I didn't think it would have made a difference, I guessed wrong. But even if I try someway of accessing Ubuntu again, it would just mount virtually again and would return the same results if I did fdisk again, I have no way of getting to the base terminal of ubuntu, because it boots directly to windows. Oh and I have no floppy drive installed on my system, so creating the boot image on the floppy is out of the question :lolflag:

---

### Post by Pumalite on 2007-09-26
This problem beats me. Somebody will chime in.

---

### Post by cowboy.bebop on 2007-09-26
Oy its no problem, I appreciate all the help I can get, you have done a great job, nno doubt. I am gonna go ahead and set the boot flag on '/boot' although it not important, knowing that GRUB ignores the flag but I can give it a shot. 

I do know that the files have been installed correcly to the system so even if it is I can use the LiveCD to rewrite to that specific area so if I am unable to locate the grub boot loader I can reinstall it by browsing tutorials while virtually mounted on the CD.

---


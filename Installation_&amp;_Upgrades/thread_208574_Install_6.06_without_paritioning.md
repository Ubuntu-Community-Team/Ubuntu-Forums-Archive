---
title: "Install 6.06 without paritioning?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by MarcG on 2006-07-03
I'm running Gentoo right now and would like to switch to Ubuntu. I've got the 6.06 CD. I've had problems restoring backups in the past and would like to make this as risk-free as possible.

Most, if not all, of my data is in my /home directory. What would be the best way to install Ubuntu and leave my user data intact and accessible? I'm thinking I could just delete everything except /home and install Ubuntu. Will the install repartition the drive automatically, therby erasing all my stuff, or can I install without repartitioning?

And this is more of a Linux general question, but when I add a user (myself), would I be able to specify my old user ID and home directory so I can just jump right back in?

Thanks.

---

### Post by BrianK on 2006-07-03
it depends on your setup and your old partition table.  

Was your old drive paritioned so that /home was its own partition?  If no, are you installing Ubuntu on the same partition that held your old /home?  If yes, I'm out of suggestions, otherwise...

If your old drive had a separate /home partition, the ubuntu installer will allow you to use that partition, set its mount point as /home, and then just make sure not to reformat it.  Should work fine.

If you're installing ubuntu on a different disk, again, just tell the ubuntu installer that /home is on another disk & everything should be fine.

re: UID.  Assuming you want to be the initial user that ubuntu wants you to create during install, just use any UID, then, as root, edit the /etc/passwd & group file, then chown/chgrp -R your home dir (which may or may not be neccessary)... at that point, to make your life easier, just reboot so that nothing with your old UID is sitting around in memory. 
 It may be easier to setup a dummy user as the first user, then add yourself as a user later... when you add a user, you can specify UID & home dir location.  Just be sure that your new user has access to all the goodies like sound card, administrative stuff (package management), graphics, etc - all which can be done in "user accounts" in the settings menu.

---

### Post by MarcG on 2006-07-04
Thanks for the info, Brian. My current setup has everything on one partition, so that's a problem. But I do have a second drive. That one is smaller, 3G vs 30G, and is currently a Windows partition. I have no intention of keeping any Microsoft anywhere, and that disk is pretty empty of useful data, so repartitioning that one is what I plan to do.

I could just install onto that one, but is 3G enough to install Ubuntu onto and remain useful? And how about installing other software? Can I put that onto my 30G drive easily enough?

Another idea would be to move my /home on the smaller drive. Is there a way to repartition that one before I load the Ubuntu CD?

Thanks again.

--Marc

---

### Post by jewelewu on 2006-07-04
Im using ubuntu 5.10. I got cd ubuntu LTS 6.06. Now i want to upgrade it using this CD without partitioning & without deleting old ubuntu files.How it is possible?Another way i can upgrade it from internet but i want to upgrade it from "Ubuntu6.06 LTS" cd. When i boot this cd its start new installation, no upgrade option....so anyone can tell me plz.....how can i just upgrade ubuntu 5.05 to ubuntu 6.06 LTS using CD? Thx in advance.

---

### Post by nolongerlivecd on 2006-07-05
As for the 3G question, I've got Ubuntu running on a 4GB partition. Going to check with GParted the exact size

---

### Post by nolongerlivecd on 2006-07-05
1.74GB used with fresh install. 386 kernel

---

### Post by MarcG on 2006-07-05
Thanks for that size info. Now I've got another question, and I apologize for the newbie-ness. I'm familiar with *nix, but not down at the system level.

What makes up the Ubuntu system install that fits in that 1.74GB? I'm just wondering how the system knows where to find things. I hope I'm making sense here. I understand how the partitions work. For example, I can have an entire partition called /home and put that on my smaller drive, /dev/hdb1. But if I install Ubuntu and it takes multiple directories, how does the system know that /etc and /usr/bin are on /dev/hdb1, while /home and /<something_else> are on /dev/hda?

So when I install new apps, how do I make sure they get onto the bigger drive? It's possible that when I actually get to installing all this it will be clear, but I want to find out what I can in advance to prevent me from wiping everything out accidently.

---

### Post by ezsit on 2006-07-05
> What makes up the Ubuntu system install that fits in that 1.74GB? I'm just wondering how the system knows where to find things. I hope I'm making sense here. I understand how the partitions work. For example, I can have an entire partition called /home and put that on my smaller drive, /dev/hdb1. But if I install Ubuntu and it takes multiple directories, how does the system know that /etc and /usr/bin are on /dev/hdb1, while /home and /<something_else> are on /dev/hda?

The install may very well fit on 1.74GB, but on a 3GB drive you have very little room for growth. Adding applications will require space. Also, the /tmp directory will need sufficient space if you plan on burning CDs or DVDs. Even extracting large compressed files like .tar and .zip files will temporarily require space in /tmp. So I would suggest having a minimum of 8GB for the / partition as long as you do not plan on creating multiple partitions for /tmp (and possibly /var).

As for your next question. When you install Ubuntu, part of the install process will write a file called fstab and place this file in your /etc directory. the fstab file tells the system where each directory is located (if not on the same partition as the / filesystem). The fstab file is editable by root and you can change the mount points (locations of the filesystems) and indicate mounting preferences. man fstab for more info, also, man mount.

---

### Post by MarcG on 2006-07-05
Thanks, folks, for the help. It looks like my best path would be to just keep /home on the smaller drive and install on the bigger one. That'll give me the best room to grow.

Time to dive in :-? 

--Marc

---


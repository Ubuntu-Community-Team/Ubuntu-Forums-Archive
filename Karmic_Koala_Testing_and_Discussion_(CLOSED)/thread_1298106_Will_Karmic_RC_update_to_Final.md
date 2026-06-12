---
title: "Will Karmic RC update to Final?"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Altaflux on 2009-10-22
A friend  gave me his laptop for me to install ubuntu. And i know that if i install him 9.04 he will not upgrade to 9.10. So i was thinking in downloading 9.10 RC and let ubuntu upgrade itself to final version. Is that possible?

---

### Post by NightwishFan on 2009-10-22
Yes, Ubuntu will update to the final. If you install 9.04, you can update to the 9.10 release from there anyway. The process is very easy, and nearly automatic. Either way will work fine.

---

### Post by mr_rg on 2009-10-22
He is not asking if 9.04 will update to 910 RC I think he is asking if 9.10 RC will update to final 9.10. I do not know though.

---

### Post by winotree on 2009-10-22
The answer is still *yes*, just accept the updates as [when] they arrive in the repositories.  ;)

---

### Post by Martin Marshalek on 2009-10-24
Do you need to run update-manager -d or do a dist-upgrade or will it come as regular updates?

---

### Post by NightwishFan on 2009-10-24
If you are running jaunty I think it will show up when it is released. You can set your upgrade preferences in Software Sources.

---

### Post by flipper9 on 2009-10-24
I would recommend NOT upgrading from Jaunty to Karmic.  Why?  Because you will not get the benefits of the new EXT4 disk format (unless you used that format, which was not the default under Jaunty but you could use it if you wanted) which is faster and better.  Also, you won't get the new Grub2 without serious hacking and potentials for problems.

If you did a fresh install with the Karmic Beta or RC, then just keep updating with Update Manager (remembering to be cautious if it offers a "partial upgrade", see sticky above) and you will get the final release as things get fixed.

---

### Post by NightwishFan on 2009-10-24
You can do a fresh install to get the new stuff, however, I would say the update is fine. Ext4 is not strictly necessary, and if you have never played with grub, you will hardly know the difference. I have never heard of having to hack to get to grub2 but I may be ill informed.

---

### Post by flipper9 on 2009-10-24
Here are the benefits of EXT4...

Info: [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)
Benchmark: [http://www.linux-mag.com/id/7271/3/](http://www.linux-mag.com/id/7271/3/)

---

### Post by novafluxx on 2009-10-24
This gets asked once a day, maybe more so.

Please learn to use the nifty little search feature they just recently invented.

YES, by installing the RC and continuing to run update-manager, you'll end up with the final release, just avoid any partial upgrades unless you know what you're doing.

Thats when you come ask here...

IF you installed alpha 4 and ran update-manager all the time, you'd end up with final on release day...

---

### Post by josdomingues on 2009-10-24
I am thinking in a fresh install of Karmic but I have some questions.
    Now I have a dual boot instalatiom of Windows XP and the Jaunty.
    Both OS are running well.
    To do a fresh and clean install of Karmic shall I clean, clear or unalocate the partition were is now the Jaunty? 
    And after that install de karmic in that (clean) partition from the ISO CD?
    May I use, for example the EASEUS from inside the XP for manage the partitions?
    It is a problem to alter the partition of the Jaunty if I will not use it anymore?
    Am I going in truble with the GRUB2, because the old GRUB?
    What is the best procedure?
    Thanks in advance.:-)

---

### Post by howefield on 2009-10-24
> **josdomingues said:**
> To do a fresh and clean install of Karmic shall I clean, clear or unalocate the partition were is now the Jaunty?

You can prepare the partition before you install Karmic with the partition editor on the live cd. (System > Administration > GParted) or you can install over your existing Ubuntu by choosing the "manual partitioning" option during the Karmic installation process. Tell the partitioner how to mount the partition, what file system you want to use and to format it.

The Ubuntu Partitioning video here might help you.

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by andrewabc on 2009-10-24
> **josdomingues said:**
> I am thinking in a fresh install of Karmic but I have some questions.
    Now I have a dual boot instalatiom of Windows XP and the Jaunty.
    Both OS are running well.
    To do a fresh and clean install of Karmic shall I clean, clear or unalocate the partition were is now the Jaunty? 
 
Boot Karmic livecd. When get to partition editor, simply go to advanced option (specify partitions manually). Select your jaunty 9.04 partition, delete it, create new ext4 filesystem, and install ubuntu 9.10 there. GRUB should detect your winxp install and you can continue dualbooting.

[img]http://www.ubuntugeek.com/images/9.10/7.jpg[/img]
Specify partitions manually. It'll show your jaunty install, winxp, and swap. Pretty sure just delete jaunty ext3, and from new free space create new ext4 partition. Make the ext4 mount point: /   

Backup before doing anything in case it doesn't work. Don't touch your winxp partition.

---

### Post by rahul_4096 on 2009-10-25
Right now I am running on Jaunty. I want to upgrade on Karmic RC. Will I be able to upgrade on Karmic final through alternate CD method. This is important to me as my Internet connection is not suitable for 700 MB download. I can get the ISO downloaded at my friend's place.

---

### Post by rahul_4096 on 2009-10-25
> **rahul_4096 said:**
> Right now I am running on Jaunty. I want to upgrade on Karmic RC. Will I be able to upgrade on Karmic final through alternate CD method. This is important to me as my Internet connection is not suitable for 700 MB download. I can get the ISO downloaded at my friend's place.
can anyone help me out with this

---


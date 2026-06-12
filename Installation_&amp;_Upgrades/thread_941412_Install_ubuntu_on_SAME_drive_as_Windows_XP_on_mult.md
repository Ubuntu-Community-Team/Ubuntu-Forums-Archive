---
title: "Install ubuntu on SAME drive as Windows XP on multiple HDD system"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Malax on 2008-10-08
Hey all, I'm just getting into Linux and trying to install ubuntu on my machine.  I couldn't exactly find what I was looking for so hopefully this thread will generate some help.

I currently have a machine with 3 drives, one with my xp os and most of my programs, one is essentially just sitting blank for right now as I'm about to replace it, and one with my games/media/etc on it.

I ran the installer from the xubuntu live cd, and it's attempting to install linux on my media drive, however I want it on the same drive as my windows install, and to let linux use any programs it can that are already installed.

Can anyone tell me how I would go about doing this?  My os drive is a 40 gig with about 5.75 gig of free space.  The xubuntu minimum free space requirement is 1.5 gig, so I know that shouldn't be a problem.  Thanks.

---

### Post by Patb on 2008-10-08
Malax, that 5.75 Gb space just might be a bit of a squeeze sooner or later. You will have your /home partition in there too by the look of your post. It should be fine as a short term measure though, until you replace that other drive. 

A guide on dual boot setups is here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/). The steps for Xubuntu will be virtually identical to those for Ubuntu. 

Cheers, Pat.

---

### Post by vanadium on 2008-10-08
I don't know if you are able to indicate a drive in the installation program during "easy" setup. If you can, do that and then select the option "use largest free space".

If that is not possible, you will need to choose "Manual" under "Prepare disk space. At that point, you must create your root partition and your swap partition yourself, and in a subsequent step specify which partition is going to be used for the root ("/") and for swap.

---

### Post by vanadium on 2008-10-08
I see in the mean time you have got great help from Australia. Looking at the guide Patb linked to, I have the impression that the easy setup option does not allow for choosing another drive. You will probably need to go for "manual". This will be scenario B ([http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)) or C ([http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)) (I favour C: you do the partitioning not during the installation, but before: less chance to have an interrupted install).

I concur with Patb that 5.75 Gb is on the small side, especially when it also needs to hold the swap. However, as a dual boot user, your home directory will not contain user data, only program configuration files, and in these conditions, it will work.

---

### Post by Patb on 2008-10-08
+1 for Vanadium's posts.

I forgot to say that during installation, I almost always use the "manual" partition option. That way, I can see exactly what is happening to partitions before I commit to changes. 

Cheers, Pat.

---

### Post by Malax on 2008-10-08
Thanks guys.  The replies were fast an the information was spot on.

I feel a big better knowing that I was on the right track by manually changing the partition size.  I just didn't want to continue and mess something up.

Pat, I think I'm gonna take your advice and install to a larger drive.  I'll probably clone my windows install to my 80 gig and install ubuntu there as well.  Thanks again, I'll keep you posted.

---


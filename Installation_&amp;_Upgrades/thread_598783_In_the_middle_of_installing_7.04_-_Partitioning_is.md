---
title: "In the middle of installing 7.04 - Partitioning is scary!"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by TheGibson on 2007-10-31
OOOOkay....  This is an adventure!  First time installing Linux.

When I set up my laptop ([[COLOR="RoyalBlue"]hp dv6140us[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00770965&lc=en&cc=us&dlc=en&product=3253933&rule=44525&lang=en")), I left a 15gig partition open to install Linux later.  I put XP on my first drive and now I'm putting 7.04 alternative CD on my 2nd HDD (the 15GB).  I'm at the point where I choose how to partition the drives and while reading the HELP ON PARTITIONING stuff, it mentions a "swap" file.

Swap file?

F?  B?  K?

I'm getting cold feet.  This is what's on the screen:
[B]
SCSI1 (0,0,0)  (sda) - 120.0 GB ATA FUJITSU MHV2120B
           #1 primary 104.9 GB B K ntfs                /media/sda1
           #5 logical     15.2 GB    K ntfs                /media/sda5
                pri/log       8.2 MB    FREE SPACE[/B]


I have 2GB RAM, which I understand is how large my swap file should be.  Is this needed if I don't plan on using the hibernate feature?  I've looked through a ton of threads and knowledge bases and whatnot, but can't find this exact issue dealt with.

My question is: how do I break off 2gigs from my 15 to create a swap file, and what do I have to do to them so everything boots properly (also, will I get a choice on startup between XP and Linux then?)?

I have been extremely impressed with how helpful everyone here is to outlanders (me) so any information you have will be much appreciated.  If you can find where the infomratin is located, please feel free to just post a link that sends me in the right direction.

I'm looking forward to using the Feisty Fawn!

---

### Post by Pumalite on 2007-10-31
Make your /swap 1 GB and you'll have more than enough.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by TheGibson on 2007-10-31
> **Pumalite said:**
> Make your /swap 1 GB and you'll have more than enough.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Reading now... looks promising.   Thanks!

---

### Post by TheGibson on 2007-10-31
Also, is it normal to get a weird morphinng screen (wth lateral lines) when you're using the LiveCD?

---

### Post by Pumalite on 2007-10-31
No. You should have a nice graphical interface.

---

### Post by TheGibson on 2007-10-31
> **Pumalite said:**
> No. You should have a nice graphical interface.

No luck.  I have something that shifts from gray to black back to gray... morphing.  Kind of like [COLOR="Blue"][THIS GUY'S]("http://ubuntuforums.org/showthread.php?t=552257&highlight=grey+screen+moving")[/COLOR] problem.  Only happens with LiveCD, so I'm using Alternative text CD (plus I have an nVidia card, not ATI... not going to worry about it).  Would love to try this graphical interface I keep hearing about.  :)


Okay, the guide you gave me was a little bit helpful, but runs through only one example of him setting it up.  He talks about the mount point, but doesn't say what it is so I can apply that info to my situation.

My 15gig partition settings:

[B]USE AS: ntfs
MOUNT POINT /media/sda5
BOOTABLE FLAG:  off
Resize Partition (currently 15.2GB)[/B]

I'm guessing I want to resize the partition to 14.2GB and leave 1GB of free space for the swap file.  Would I need to change any other settings on this one?  Also, don't I want the bootable flag on so I can duel boot with XP?

Thanks so much for your help.  I'm hoping this will translate to Kubuntu as well, as I also want to give that a try.

---

### Post by Pumalite on 2007-10-31
1 GB /swap is fine. I'd do 10 GB for '/' and the rest for /home. Don't worry about the boot flag.

---

### Post by TheGibson on 2007-10-31
> **Pumalite said:**
> 1 GB /swap is fine. I'd do 10 GB for '/' and the rest for /home. Don't worry about the boot flag.

So I'd be looking at 3 new partitions?  1GB "/swap", 10GB "/" for Ubuntu, and 4.2GB for "/home" ?  What is the /home for?

---

### Post by scorp123 on 2007-10-31
> **TheGibson said:**
> So I'd be looking at 3 new partitions?  1GB "/swap", 10GB "/" for Ubuntu, and 4.2GB for "/home" ?  What is the /home for? [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

" ... **/home** .... Users' home directories - containing saved files, personal settings etc. Often a separate partition. ...."

---

### Post by Pumalite on 2007-10-31
It keeps your settings and things you want to have handy. It's nice to have a separate /home partition in case of a clean install in the future. You can use /home again and keep your settings.

---

### Post by TheGibson on 2007-10-31
> **Pumalite said:**
> It keeps your settings and things you want to have handy. It's nice to have a separate /home partition in case of a clean install in the future. You can use /home again and keep your settings.

Oh.  Handy.

I'll give it a shot.  Thanks.

---

### Post by Pumalite on 2007-10-31
You are welcome. Good luck.

---


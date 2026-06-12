---
title: "installation of 32 bit 10.04 failed miserably"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by Stonefolks on 2010-06-05
My brother was finally fed up with windows and decided to install ubuntu but didn't know where to start. I volunteered to help him. 

We decided he didn't have enough room to dual boot windows and ubuntu. He is using an older dell desktop that has has 512 megs of ram and 40 gigs of memory, 2.44 gHz celeron processor. 

I tried installing the 32 bit version of ubuntu 10.04 on his machine. I gave him 5 gigs of swap and 3 gigs in boot. It worked fine for two days and on the third day he tried to boot up his machine and got the message "primary drive 1 not found, secondary drive 1 not found" and the boot loader never appeared. He waited for a while and eventually the ubuntu splash screen appeared with five red dots, and after a moment of that the screen went totally dark. After "a very long time" (in his words) the desktop appeared but his desktop toolbars never appeared. The one folder on his desktop did appear. He "couldn't do anything" and eventually shut it down.


I apologize for the length of this post, but I tried to provide as much detail as I could. If anyone could tell me what went wrong I would appreciate it very much. If you needmore information let me know and I will try to provide it.

---

### Post by dino99 on 2010-06-05
follow this little help to make an install:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

the problem seems to be due to graphic driver not activated: check into system admin hardware driver

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by 00b00nt00 on 2010-06-05
My first thought is that you have allocated far too much HDD for swap, and far too little for the boot partition.

As you are not dual booting, why didn't you just let Ubuntu handle the partitioning?

Run the Ubuntu installer again, and when the disk options are presented, just tell Ubuntu to use the entire hard disk. Don't poke around under 'Advanced' unless there is something very specific you are trying to achieve.

---


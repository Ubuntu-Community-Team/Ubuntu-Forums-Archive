---
title: "smallest computer to run 6.06 reasonably?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2006-06-01
Hi all,

I would like to install 6.06 on a P2-400 with 192M and a 4G hd and an 8M agp graphics card.  My concern is the speed of the machine after the install completes.  Will it be "sluggish"?  What are the reasonable specs for a computer I won't have to waite for too much?  I don't plan on doing anything to taxing just web browsing and email and some document creating and small spreadsheet manipulations.

thanks,
charles.....

---

### Post by deweese on 2006-06-01
I recommend you try it out and see if it works.  I tried to install Breezy on a Pentium 2
333MHZ laptop with 160 mb of ram and it wouldn't install the grub booter.
If it installs it should be good.  If it is too slow you can upgrade ram or try Xubuntu for 
slower/older computers in Dapper Drake.

---

### Post by spin2cool on 2006-06-01
Yes, it's going to be slow.  You'll probably pick up some speed by ditching GNOME and using IceWM or fluxbox or one of the other lightweight window managers.

Honestly, though, you might be better off trying a distro that has low end hardware in mind.  Slackware comes to mind, but be aware that it's not as n00b-friendly as Ubuntu

---

### Post by catlett on 2006-06-01
Why don't you try xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) It's the newest addition to the ubuntu distros. Just in case your curious. Ubuntu = gnome window manager, kubuntu = kde window manager, xubuntu = xfce window manager. Xfce runs lighter and should run aloy better on your machine than ubuintu or kubuntu

---

### Post by shae on 2006-06-04
Might I suggest "Ubuntu Lite."  It uses ubuntu, but installs only what is needed to run IceWM and other lite replacements.  I am using it on a P-3 933 Mhz w/ 128 MB and Integrated Intel Video from 810e.  [http://www.ubuntulite.org]("http://www.ubuntulite.org")  By no means is setting up such an install is as easy as Ubuntu is, but it runs about 200% better (from personal observation).  If you are new to linux, then you might want to go with Xbuntu instead, but I just feel that "Ubuntu Lite" is snappier and, for me, more of a learning experience.  According to them, they have Ubuntu lite running on 133 Mhz Pentium with 64 MB though they suggest 128 MB and of course a faster processor helps.  I think it will run quite a bit better that Gnome would with the standard install.  Good luck.  If you have any questions email me at [email]starfall87@gmail.com[/email]

---

### Post by confused57 on 2006-06-04
If it were me, I would try Xubuntu first; it would be the easiest to install.

If this doesn't work, then try Ubuntu Lite:

[http://www.ubuntuforums.org/showthread.php?t=98233](http://www.ubuntuforums.org/showthread.php?t=98233)

I just set up a dual boot with Ubuntu Lite and Xubuntu; it's not difficult, but a little more time consuming to install Ubuntu Lite.  My system is 500MHz, 256 ram, 16 Gb Hd.

If you go with Xubuntu, you'd want to install with the alternate iso, not the desktop(livecd) cd...if you have a fast internet connection, you may want to download and burn both.  Run the desktop livecd to see how it runs on your computer...if it runs reasonably well, by at least getting you to a working GUI, then install with the alternate cd.  Installing with the desktop cd would be quite slow...

---

### Post by brucenduane on 2006-06-04
For a machine that small, I would recommend Puppy Linux.  
Chubby Puppy Linux 1.05 with Open Office Suite would fit all your needs.
The New Puppy 2.00 was just released June 1, 2006 which would also work
and you could download Open Office after it is installed.  Puppy Unleashed is about 750 MB which would fit within the 4G hard disk with plenty of room left over.

I like Puppy because of it's small size, great simple applications, and ease of use.  It runs on my ancient, diskless notebook  and runs totally in memory and frees up the CDROM after it boots, so I can play movies on it.  There is no chance of a virus because it boots fresh from the CD each time.  I can store my changes on a USB thumb drive or on my camera's Flash Card via USB card reader.  It even can connect to the Wifi with MadWifi and a Dlink DWL-G630 Cardbus card.

Don't Flame me!!   >>>> I think Ubuntu is GREAT!! <<<<<  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif) 
Up until December 2005 I have always had 5-8 different distribution of linux on my computers and installed them on my friend's computers.  In December I found Puppy Linux and put it on a 256 MB thumb drive for a friend.  I love this small but complete distribution.  The new 2.00 release will run on my new computer with SATA serial drives.  It was a simple system to help convert Windows people to Linux.  Once they are happy with Linux they will want to use Ubuntu.

Later in December 2005 I discovered Ubuntu 5.10 and installed it from a "Linux Format" Magazine DVD disk.  Since then I have not played with any other distribution except Chubby Puppy 1.05.  My SUSE 10.0, Mandriva 2006, Knoppix 4.02 CD & DVD, Gentoo, Fodora, Kanotix, and Debian Sarge 3.1r1 distributions CDs/DVDs have been gathering dust and their partitions have been wiped as Ubuntu meets all my normal computing needs.

Next week I will be upgrading to Ubuntu 6.06 Dapper Drake and installing Puppy Linux 2.00 on all my computers and my friend's three computers.  Puppy can use Ubuntu's installed applications where possible as well as it's own.   It will be interesting to see how well the duck and puppy play together.

Thanks to both communities for their effort and support!

-Bruce.

---

### Post by ubuntu_demon on 2006-06-04
Try xubuntu instead of ubuntu. 

If it's not fast enough then install icewm : 
$sudo apt-get install icewm 

Then choose icewm from the login screen under sessions. This is probably sufficient because a while ago I ran breezy with  icewm on a far slower computer. (I don't remember which display manager probably gdm)
find more packages related to icewm with :
$apt-cache search icewm
to get more information about a package :
$apt-cache show packagename

If you need even more speed you might try ubuntulite from **non-official repos** :
[https://wiki.ubuntu.com/UbuntuLite](https://wiki.ubuntu.com/UbuntuLite)
[https://wiki.ubuntu.com/InstallingUbuntuLite](https://wiki.ubuntu.com/InstallingUbuntuLite)

I've no experience with Ubuntulite

---

### Post by mcwtlg on 2006-06-05
My server is a Celeron 400 w/512 megs Ram and an 8 gig hd (I have other drives installed but those are just for storage).  I installed XFCE and it runs just fine with Ubuntu.  Now, to be fair, I did a dist-upgrade and I have been having issues with it locking up after it is running for about an hour.  I have not investigated that yet, but it ran fine until the dapper upgrade.  I am sure it is the bios issue that is being talked so much about.

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=mcwtlg]My server is a Celeron 400 w/512 megs Ram and an 8 gig hd (I have other drives installed but those are just for storage).  I installed XFCE and it runs just fine with Ubuntu.  Now, to be fair, I did a dist-upgrade and I have been having issues with it locking up after it is running for about an hour.  I have not investigated that yet, but it ran fine until the dapper upgrade.  I am sure it is the bios issue that is being talked so much about.[/QUOTE]
What issue are you referring to ? Do you have some links for me ? Is there already a fix / solution ?

thnx

---

### Post by Johnsie on 2006-06-05
Might be the same as the issue on my laptop.... THehad disk goes busy and then everything eventually grinds to a halt.... This sual happens ever hour or so.... Anyway... Back to the topic... I think I might try this puppy linux on my server :-)

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=Johnsie]Might be the same as the issue on my laptop.... THehad disk goes busy and then everything eventually grinds to a halt.... This sual happens ever hour or so.... Anyway... Back to the topic... I think I might try this puppy linux on my server :-)[/QUOTE]
Maybe there's a process that gets started every hour :
$cat /etc/cron.hourly

---

### Post by mcwtlg on 2006-06-05
[QUOTE=ubuntu_demon]What issue are you referring to ? Do you have some links for me ? Is there already a fix / solution ?

thnx[/QUOTE]

I would have to dig, but I did a search yesterday and found some posts that people had power mgmt issues and when they turned them off in the BIOS, the problems went away.  The same box was running Breezy 3 days ago but now that I have Dapper on it, it locks up.  The posts were pretty similar to the problems I am having.

---

### Post by eppoh on 2006-06-05
I am also running Puppy on my old Celeron 400 in the gargage. It flies. 
I like Ubuntu, am running Dapper Drake, but the instal is a pain because it installs the 386 kernal by default and it is slow. I have had to upgrade everything to the 686 and now it is fine.

---

### Post by ubuntu_demon on 2006-06-06
[QUOTE=mcwtlg]I would have to dig, but I did a search yesterday and found some posts that people had power mgmt issues and when they turned them off in the BIOS, the problems went away.  The same box was running Breezy 3 days ago but now that I have Dapper on it, it locks up.  The posts were pretty similar to the problems I am having.[/QUOTE]
If you had said ACPI I would have understood :p

---


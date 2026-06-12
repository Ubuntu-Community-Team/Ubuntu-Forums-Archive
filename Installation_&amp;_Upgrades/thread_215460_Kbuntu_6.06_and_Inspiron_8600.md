---
title: "Kbuntu 6.06 and Inspiron 8600"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by paulsiu on 2006-07-14
Hi,

I am trying to help a friend out. She has an Dell Inspiron 8600 with Slackware 9 on it. She's been wanting to do stuff like connecting her digital camera to the computer. However, she isn't a computer person and can't really figure out how to run the command line package manager on slackware.

I was thinking about install Kbuntu 6.06 on her machine (she likes KDE, but dislike Gnome). Has anyone have any experience with installing this distro on a Dell Inspiron 8600. Did everything worked right away or needs a bit of fiddling? Earlier post indicate that it would be a problem, but the posts are over a year old. 

Alternately, I could look into Mepis, which seems to be similar to Kbuntu.

Please help or she may go back to Windows :twisted: 

Paul

---

### Post by André on 2006-07-15
Hi paulsiu,

i do not like these "uhoh, going back to Windows statements" but i will answer anyway ;-))

I am running Kubuntu on an Inspiron 8600 here.

Most stuff runs very well:

- Suspend out of the box
- after some fiddling great hardware support
- ...

But there are also some shadows:

- I kicked out the open source driver for the wlan card and using ndiswrapper again because it did work better.

- My screen has a common resolution of 1920x1200. I do not like it to be that big and use 1280x800. When i use the ATI drivers (having a Radeon 9600) the fonts are bad, ... The resolution works well with the 3D drivers from X.Org but 3D accelaration is not very good (bad performance -> but better then without :-))

If you have any more questions i will try to answer them.

Greetings
André

---

### Post by iridesce on 2006-08-12
Greetings,

Currently fighting ... er, working with an Inspiron 8600 on an Ubuntu 6.06 installation.  It is a dual boot installation with XP in the first partition, a fat32 partition for files, a ext3 partition ( a failed Mepis installation ) and a swap partition.

I downloaded Ubuntu 6.06and burned the desktop ISO onto a disk, and began.  It took a few minutes of nothing happenings and I gave up.  Tried the installation on a workstation and found out that it does take some time to begin the installation ( or more time than I am used to in Mandrake and Mepis installations ). 

Back to the 8600, after waiting a long time for the installation to find open space on the disk, Ubuntu Live opened - pretty - and clicked on Install.

Took some time to begin the installation ( I'm learning ) and clicked on the defaults 

Selected 'Manually edit partion table" and continued with the installation.

Silly me, after an initial problem in which the installation froze at the 82% mark during the 'Installing system' component of the installation, I rebooted and everything went fine.  

My first successful installation of a Gnome desktop and what do I do?, install Kubuntu as I am comfortable with KDE.  

That installation went well also, but, as the machine is for my partner and 1) she has a major thing for solitaire ( the AisleRiot Solitaire in Ubuntu has over 80 varieties ... ) and 2) what??, no Firefox in the default Kubuntu installation ??? and 3) I think the Shuttleworth effort ( including giving away free { as in plastic and shipping } disks, initiatives for education and general lightbringing is way cool, so I tried to reinstall Ubuntu ( besides, I always did want to play with Gnome ).

Then ... a variety of issues, the installation freezing at 84% during 'Installing system', installations aborted due to errors, not being able to get the live version up and running, using 'root' as a user name ( seem weird not to be able to do so ... ), etc - probably about everything that could go / be done wrong...  Probably would have given up, and since I did get an installation to take and want my partner to experience the joys ( no smirk - truly ) of a penguin powered puter, I persist ( its only 1:00 am ).

Currently on installation attempt# 8, including burning another ISO, just because... and success !!! Could have been dust on the CD ( though I did clean it about install try# 4 ) - who knows - I just thank the gods of electrons ( possibly the universe wanted me to write this ... )

Good luck on your attempt

Michael

Also, re: the networking card issue - I found out a long time ago that the Orinoco ( Proxim ) Gold Card works well ( without tweaking ) on every combination of Linux distro, Windows OS, and laptop I have ever tried - I do have to enter the WEP key, but has run well every time.  Sometimes $50 ( or whatever they cost now ) is much easier than tweaking software -  at least for a life long newb like me ...

---

### Post by André on 2006-08-12
Giving "support" is a bit offtopic here, but:

@Michael: You really should check your RAM and harddrive. I never (!) had a problem bringing the installation to 100%. Does your system freeze? Than it could probably be the RAM or harddrive...

Greetings
André

---


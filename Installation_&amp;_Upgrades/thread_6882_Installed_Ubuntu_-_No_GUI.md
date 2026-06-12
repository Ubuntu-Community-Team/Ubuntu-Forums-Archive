---
title: "Installed Ubuntu - No GUI?"
date: 2004-12-02
forum: Installation &amp; Upgrades
---

### Post by MJoshi on 2004-12-02
I am new to Linux so please be patient!

I managed to install Ubuntu onto to the hard-drive but had a few error messages stating that there wasn't enough space and that I would have to remove some components.  I attempted to do this but somehow after pressing return, the installation just finished by itself?

I am able to login as root with the username and password specified during signup.

Excuse my ignorance but how do you load up the GUI from the command prompt?

---

### Post by deception on 2004-12-02
See if  "startx" works.

---

### Post by MJoshi on 2004-12-02
Will do, thanks.

---

### Post by arctic on 2004-12-02
[QUOTE=MJoshi]I am new to Linux so please be patient!

I managed to install Ubuntu onto to the hard-drive but had a few error messages stating that there wasn't enough space and that I would have to remove some components.  I attempted to do this but somehow after pressing return, the installation just finished by itself?

I am able to login as root with the username and password specified during signup.

Excuse my ignorance but how do you load up the GUI from the command prompt?[/QUOTE]
if your installation told you that there ain't enough space, then it could be that you do not have gnome installed. you should use at least a 2 gb partition for your installation.

apart from startx, if that does not work, log in at the commandline and run "sudo xorgconfig". this should set up all your "relevant" hardware (mouse, monitor, keyboard, graphics-card, resolutions). if you run that text-based script, you will need to know some data (like refresh rates, graphic-card memory etc.), otherwise you could damage your hardware.

---

### Post by jdong on 2004-12-02
[QUOTE=MJoshi]
I am able to login as root with the username and password specified during signup.[/QUOTE]

Are you sure? root should be disabled? Make sure you installed Ubuntu...  :mrgreen:

---

### Post by MJoshi on 2004-12-03
I'm not sure it is root, but I am able to login to the command line interface with the username and password specified during installation.

When I type 'startx', it reports back saying "command not recognised"  :confused:

---

### Post by ubuntu_demon on 2004-12-03
I don't think you should run startx as root. It will could create other problems.

You are running warty and therefore x.org configuration tools won't work.

If you want root power just type sudo before a command. (it will ask for your password again)

You can run XF86Config or something like that (I'm not logged in at my ubuntu right now) to config X.

You can find things on your harddisk with locate. For example :

locate XF86Config

Before you use locate you have to do first : 

sudo updatedb

And do :

df

and post the results of it here

good luck!

---

### Post by MJoshi on 2004-12-08
I just want to access the standard GUI.

Will I need to re-install Ubuntu again?

---

### Post by ubuntu_demon on 2004-12-08
If you can repartition so ubuntu has some more space then that would be the easiest I think.

---

### Post by MJoshi on 2004-12-09
I only have a 1GB SCSI HDD!

I think the Swap is allocated about 100MB by default?

Do I need to re-install using the 'Expert' option?

---

### Post by ubuntu_demon on 2004-12-09
I would buy a new harddrive and reinstall that would make life a lot easier.

Otherwise I would recommend two options :

* try beatrIX 
it's a small distribution based on Ubuntu. I haven't tried it but it seems nice.

[http://www.watsky.net/index.html](http://www.watsky.net/index.html)

* reinstall
reinstall (expert or normal whatever you want), don't create a swap-drive and use your whole harddrive for /
install ubuntu-base + gnome + only the packages you'll need (you can make a selection a the stuff ubuntu-desktop delivers). Maybe you're lucky and it fits. But you would miss a lot of stuff. (for a default install I would recommend at least 2 GB harddisk)

---

### Post by p!=f on 2004-12-09
[QUOTE=demon666_nl]
don't create a swap-drive and use your whole harddrive for /
[/QUOTE]
What do you suggest when he runs out of memory?

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=p!=f]What do you suggest when he run out of memory?[/QUOTE]
 well I was hoping he had enough of that. How much memory do you have MJoshi?

---

### Post by MJoshi on 2004-12-09
I only have 64MB of RAM - will I not need Swap space?

The info on the front of the C.D says that you can do a minimal install which uses about 954MB - How do you do that?

---

### Post by ubuntu_demon on 2004-12-09
The installation with custom package selection might not be a good idea since you're new to linux MJoshi.

I thought up something better. Parition your entire harddrive as ex3 /home.

Boot up from livecd you like  (ubuntu / gnoppix / beatrix / knoppix) and use your harddisk only to store your files.

---

### Post by MJoshi on 2004-12-09
Unfortunately, I tried running the live C.D installation on my computer but it was incredibly slow (P-120)!

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=MJoshi]I only have 64MB of RAM - will I not need Swap space?

The info on the front of the C.D says that you can do a minimal install which uses about 954MB - How do you do that?[/QUOTE]
 That changes everything.

I would try :

Boot from beatrix live cd and store your files on your hardrive (partion it as /home)

beatrix has also a forum : 
[http://www.watsky.net/cgi-bin/yabb/YaBB.cgi](http://www.watsky.net/cgi-bin/yabb/YaBB.cgi)

I hope they can help you. Please post your experiences back in the ubuntu forums so we can help others like you.

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=MJoshi]Unfortunately, I tried running the live C.D installation on my computer but it was incredibly slow (P-120)![/QUOTE]
 Ubuntu isn't fit for such a system. I'm sorry.

from [http://www.watsky.net](http://www.watsky.net) :

> 
BeatrIX Linux is a compact (Less than 200 megabytes), operating system aimed at both office and home users who want something simpler, safer and superior to Microsoft Windows, and that will run on just about any IBM-compatible PC made in the past 10 years. It runs as a live CD or it can be installed to hard drive. As a live CD, it does not touch your hard drive or touch any other operating system you have. SImply insert the CD, re-boot, and about two minutes later, you're surfing the Internet, writing letters, sending e-mail and instant-chatting.

It is optimised for any Pentium-class computer of any speed with at least 64 megs of RAM. Its next release will boot from a USB pendrive and compact flash. We have reports of people using it on Pentium 90s with 24 megs of RAM. We don't recommend that, but it can be done. At the other end of the spectrum, it runs flawlessly on an Opteron 64. It was originally designed for a special computer system called the mini-ITX but it runs on nearly anything.


Please report your experiences and findings back. Because I'm very curious.

---

### Post by MJoshi on 2004-12-09
I have tried so many distro's with no luck whatsoever.

Firstly, I tried Mandrake but could not get that to work so someone on the Mandrake forum recommended Peanut Linux.

Peanut Linux had problems with recognising the SCSI devices.

I then tried the Knoppix live C.D but that ran too slowly.

A friend recommended DSL (Damn Small Linux) which is 50MB but I couldn't get that working either.

I am now trying Ubuntu and having some luck!

Not another distro' pleeeeeeaaaaaaaase!

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=MJoshi]I have tried so many distro's with no luck whatsoever.

Firstly, I tried Mandrake but could not get that to work so someone on the Mandrake forum recommended Peanut Linux.

Peanut Linux had problems with recognising the SCSI devices.

I then tried the Knoppix live C.D but that ran too slowly.

A friend recommended DSL (Damn Small Linux) which is 50MB but I couldn't get that working either.

I am now trying Ubuntu and having some luck!

Not another distro' pleeeeeeaaaaaaaase![/QUOTE]
 downloading BeatrIX (under 200 megs) and running the livecd can't mess up your system.
It's ubuntu based. So with a little bit of luck it starts up and you don't have to do anything.

If I had such a pc I would try beatrIX or buy a new one. (no rant intended)

---

### Post by MJoshi on 2004-12-09
I thought Linux was backward compatible with old hardware too?

I also thought the whole idea was that Linux was not 'bloat-ware' and you didn't need the latest spec. machine to run it on?

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=MJoshi]I thought Linux was backward compatible with old hardware too?

I also thought the whole idea was that Linux was not 'bloat-ware' and you didn't need the latest spec. machine to run it on?[/QUOTE]
 You're right. Linux supports a lot of old hardware. Ubuntu certainly does.

There are some distro's that focus on being light and fast. It's possible to do something like this in Ubuntu. But it needs a bit of work by the user. And I don't think it's something n00bs/average-desktop-users would like to do.  You could for example install xfce instead of gnome.

GrumpyGroundhog the Ubuntu version after Hoary (warty is the current stable version) arriving in a little short than a year has planned: minimum memory / processor requirements?. I hope they do this.

---

### Post by MJoshi on 2004-12-09
Thanks for that.  Until the new Ubuntu version is released, i'll give BeatrIX a go.  Will it recognise SCSI devices (HDD & Optical Disk Unit)?

---

### Post by TravisNewman on 2004-12-09
No, unless you use the Live CD, Ubuntu isn't going to work very well for you honestly. There simply isn't enough space for it all, and to include swap space, which you'd need with only 64 megs of ram. Linux IS made to run on older hardware, but I got my first PC in 98 and it had a 6 gig hard drive. I'd imagine the first 1 gig hard drives were coming out in 95, and there has to be some sort of cut-off to what an OS can run efficiently on.

---

### Post by ubuntu_demon on 2004-12-09
[QUOTE=MJoshi]Thanks for that.  Until the new Ubuntu version is released, i'll give BeatrIX a go.  Will it recognise SCSI devices (HDD & Optical Disk Unit)?[/QUOTE]
 SCSI devices worked in Ubuntu for you. So probably it will also in beatrIX. If beatrIX is too slow for you you might want to replace gnome with xfce. Good luck!  (and report your experiences)

---

### Post by ubuntu_demon on 2004-12-09
I've started a thread about Ubuntu and BeatrIX :

[http://www.ubuntuforums.org/showthread.php?t=7652](http://www.ubuntuforums.org/showthread.php?t=7652)

---

### Post by oskarku on 2004-12-09
BeatrIX should run fine on your box. Please let us know if you have problems.

Thanks,

oskarku, developer, BeatrIX Linux

---

### Post by Randabis on 2005-01-21
[QUOTE=MJoshi]I only have a 1GB SCSI HDD!

I think the Swap is allocated about 100MB by default?

Do I need to re-install using the 'Expert' option?[/QUOTE]
There's a guide to using ubuntu on systems with very low disk space. I think it is in the wiki.

---

### Post by MJoshi on 2005-02-07
I thought I would just reply to this thread to let you guys know how I was getting on.

I tried installing BeatrIX Linux on the system but it was just took far too long to load.  I gave up in the end!

My friend has now given me another computer which I have managed to load Ubuntu sucessfully on.  Yeay!   :D 

I connected a USB ADSL MODEM to the computer and it is recognised as a Dynamite MODEM.  I just wanted to know what I need to do to create a PPPoA connection in Ubuntu?  I think this MODEM might be a generic chipset based ADSL MODEM (Alcatel?). 

Do I need to download any drivers?

---

### Post by eque on 2005-02-09
Guys,

Just thought I'd post this for other newbies like myself.   You guys are right about the 2.0 GB size.  I tried to install on a primary partition sized at 1.9 GB and the same thing happened to me; not all the packages were installed and I couldn't get into the GUI.  So I went back and re-partitioned to 2.0 GB and the installation ran smoothly without any problems.  

I tried using "xstart" before reinstalling though; didn't work and the message said I didn't have root access to do it.   Being a newbie, I resigned myself to reinstalling it on a 2GB drive (and the LOOONG install session, sigh :(  ).

My overall experience with Ubuntu has been somewhat frustrating compared to Fedora install.   Anaconda on fedora gave me more options in terms of what package to install to fit my drive size.   

Anyways, thx for the tips guys!

My specs: Dell Latitude Pentium 3, 700 Mhz, 256 RAM

---


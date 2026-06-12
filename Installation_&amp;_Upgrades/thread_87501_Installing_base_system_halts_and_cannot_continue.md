---
title: "Installing base system halts and cannot continue"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by icekin on 2005-11-08
I know cross posting is frowned upon, but since this was posted in the less active hoary forum, very few people took a look at it. Anyway, the below problem happened to Breezy as well when I tried it :

I have the following hardware and am trying to do a server-expert install :

Pentium 166 Mhz CPU
32 MB RAM
2 GB Hard disk
Realtek LAN network card

I plan to use this as a web server, nothing more. The install said low RAM, so certain options, like language will be disabled. The install goes okay until the screen where it tries to copy the base packages to the system. At this stage, the packages are copied till 35% and the copying stops. The install screen with the various stages of install comes back. So, I try the same step again, but it again fails to complete.

Why are the packages not being copied to hard disk properly? The CD is alright because its new and I used it to successfully install Ubuntu on another computer. I got the following message when trying to boot from CD :

strange...kswapd0 not stopped

Is this normal? The install still proceeded. I tried running Mandrake 9.1 and that worked (except for video and sound).

Also, if this hardware is not good enough for Ubuntu, is there any other distro I could try, just for running a webserver with a basic window manager like fluxbox or fvwm. I don't mind trying even trying BSD or some hardcore thing like slackware like if it can detect my hardware and install Apache + PHP + mySQL properly.

My video card : S3 Trio64V2/DX
Sound Card : Opti 82C931

Some more Added info: 

I also posted this on linuxquestions.org. One person said I had too little RAM and needed a swap file. 

I remember : Ubuntu said "Low memory, so install will proceed in limited mode (only english). You should enable swap as soon as possible. But before I could get to the stage where I had to partition the disks, the install failed. Now, if I make a swap parition using some 3rd party tool like Ranish Parition Manager, is there any way I can tell a linux install to start using this swap space for the install itself? There seem to be no parameters I can pass into the boot screen to do this.

---

### Post by icekin on 2005-11-09
Solution :

I decided to try Debian sarge out. The same problem was there too, it stalled during base package install. Then, I tried the install again, saying no when it asked "This machine may have a PCMCIA card. Do you want to turn on PCMCIA devices?". This time the base packages were all copied fully and I was able to proceed with the partition and finish the install.

I think this will work to solve the same problem on Ubuntu as well.

---


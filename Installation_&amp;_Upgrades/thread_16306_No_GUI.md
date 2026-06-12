---
title: "No GUI"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by sparks40 on 2005-02-20
I am attempting to install "hoarey" on a Gigabyte mother board.I am using aP4 processor and an 82845G Graphics controller. 

By way of background, other variants of Debian Linux (Mepis, Beatrix, etc.) seem to run fine. The installation appears to go fine until I get to the end of the process (video configuration) and then it hangs. I have to cold boot to regain control of the box. After power-up I am unable to get a login prompt... text based or graphical. I used a live CD to mount the UBUNTU file system and checked the contents of my log file. 

The last two lines of the log show the following:

Could not init font path element unix/:7100, removing from list!
Could not init font path element /usr/lib/X11/fonts/Speedo, romoving from font list!

It would appear that the XOrg files have been copied to disk but a pathing problem has arisen. The only obvious difference I can see, vs previous installs, is that I am attempting to install Xorg instead of Xfree for the first time.

Any suggestions???

TNX

---

### Post by CyrilleMortreux on 2005-02-20
[QUOTE=sparks40]I am attempting to install "hoarey" on a Gigabyte mother board.I am using aP4 processor and an 82845G Graphics controller. 

By way of background, other variants of Debian Linux (Mepis, Beatrix, etc.) seem to run fine. The installation appears to go fine until I get to the end of the process (video configuration) and then it hangs. I have to cold boot to regain control of the box. After power-up I am unable to get a login prompt... text based or graphical. I used a live CD to mount the UBUNTU file system and checked the contents of my log file. 

The last two lines of the log show the following:

Could not init font path element unix/:7100, removing from list!
Could not init font path element /usr/lib/X11/fonts/Speedo, romoving from font list!

It would appear that the XOrg files have been copied to disk but a pathing problem has arisen. The only obvious difference I can see, vs previous installs, is that I am attempting to install Xorg instead of Xfree for the first time.

Any suggestions???

TNX[/QUOTE]

Well; with Hoary, xorg didn't set up xorg.conf on my laptop, and a few another things went wrong. 

I first installed a Warty, changed sources.list and made an upgrade on all. I worked fine.

---

### Post by sparks40 on 2005-02-20
Thanks for your suggestion. I am going to downnlload nad try it now!

---

### Post by sparks40 on 2005-02-20
Warty works fine. I used the following to upgrade my system:

# apt-get upgrade

However, the kernel did not seem to upgrade and OOo is still at 1.1.2; but the machine is working fine.

Should I have used:

# apt-get install-upgrade?

TNX

---

### Post by crane on 2005-02-21
[QUOTE=sparks40]Warty works fine. I used the following to upgrade my system:

# apt-get upgrade

However, the kernel did not seem to upgrade and OOo is still at 1.1.2; but the machine is working fine.

Should I have used:

# apt-get install-upgrade?

TNX[/QUOTE]


Are You trying to upgrade to Hoary?
If so I read that you should changes all instances of warty to hoary in the /etc/apt/sources,list file then do
sudo apt-get dist-upgrade.

I tryied this myself and it did not work so well. The newest test release of hoary installed fine for me thought.

---

### Post by CyrilleMortreux on 2005-02-21
[QUOTE=sparks40]Warty works fine. I used the following to upgrade my system:

# apt-get upgrade

However, the kernel did not seem to upgrade and OOo is still at 1.1.2; but the machine is working fine.

Should I have used:

# apt-get install-upgrade?

TNX[/QUOTE]

There is a diffrence between "apt-get upgrade" and "apt-get dist-upgrade". 

apt-get upgrade is upgrading everything but not the core system
apt-get dist-upgrade is upgrading the system too


apt-get update
apt-get dist-upgrade

that is he way to upgrade from warty to hoary.

---


---
title: "Installing Lotus Notes 9 on 14.04"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by ataylor1988 on 2014-05-01
So i decided to test out 14.04 in a dual boot enviroment with window7

I am trying to install lotus notes 9 on my system.  The only issue is there is a package its dependent on that doesnt exist and is not available.
libcupsys2.

Has anyone done this yet.  If so is there a good write up.  I have found several on 12.04 but non much newer than that

---

### Post by ataylor1988 on 2014-05-01
bump

---

### Post by ataylor1988 on 2014-05-02
Anyone?

---

### Post by Mark Phelps on 2014-05-02
Repeatedly bumping your post is NOT going to get you an answer.  IF the package is not available, then you're out of luck!

---

### Post by ataylor1988 on 2014-05-02
The package wasnt available in 12.04 either.  There are write ups on a work around.  So i am trying to find a similar solution for 14.04
The issue i believe arises from ubuntu not using standard gnome interface.  I am sure someone on here uses Lotus notes on ubuntu.

---

### Post by nigel7 on 2014-05-06
[http://insane-on-linux.blogspot.com/2014/04/installing-lotus-notes-9-on-ubuntu-1404.html](http://insane-on-linux.blogspot.com/2014/04/installing-lotus-notes-9-on-ubuntu-1404.html)

I got Lotus Notes 9.0.1 installed on Ubuntu 14.04 64bit following this. It is not at the above by itself a complete idiot's guide step-by-step you must go back to the link it refers to and cobble a couple of steps into it, which is really just extracting from a .deb, editing and making a .deb , apart from that the steps are there.

I got it working, then I went onto installing the 9.0.1. Sametime, it didn't work as its too new for my Notes Server but it totally screwed the whole install up and I had to de-install Sametime and de-install Notes and then reinstall Notes, then its working. Avoid Sametime I say til the rendering issues are fixed. I'm using Pidgin for Sametime, its working.

---

### Post by El-Ape on 2015-03-03
I found after following the link in nigel7 post I found some extra dependencies where required.
You can either fire off the dpkg -i ibm.notes.blah-blah.deb and install the additional libraries mentioned in turn yum -y install libname:i386 or just fire off this little lot. I just used notes.deb and sametime.deb when I recreated my packages ;)
Sametime is working fine for me.

apt-get -y install gdb:i386
apt-get -y install libart-2.02:i386
apt-get -y install libasound2:i386
apt-get -y install libatk1.0-0:i386
apt-get -y install libbonobo2-0:i386
apt-get -y install libbonoboui2-0:i386
apt-get -y install libgconf2-4:i386
apt-get -y install libgnome-desktop-2-17:i386
apt-get -y install libgnomeui-0:i386
apt-get -y install libjpeg62:i386
apt-get -y install libpam0g:i386
apt-get -y install libstdc++6:i386
apt-get -y install libxkbfile1:i386
apt-get -y install libxp6:i386
apt-get -y install libxss1:i386
apt-get -y install libxt6:i386
apt-get -y install libxtst6:i386
dpkg -i notes.deb
dpkg -i sametime.deb
dpkg -i ibm-activities-9.0.1.i586.deb
dpkg -i ibm-feedreader-9.0.1.i586.deb
dpkg -i ibm-opensocial-9.0.1.i586.deb

---

### Post by thiago-canaes on 2015-03-04
Did it work?
I installed following the steps in this tutorial:
[https://www.mundotibrasil.com.br/instalando-lotus-notes-9-no-ubuntu32-e-64bits-debian-e-derivados/](https://www.mundotibrasil.com.br/instalando-lotus-notes-9-no-ubuntu32-e-64bits-debian-e-derivados/)

Though its not in english, just looking at the commands is easy to understand.

---

### Post by Thomaz on 2015-11-18
I achieved installing Notes9 and Sometime 8.5.2 in UBUNTU 14.04.
My Sometime9 is defective guess, the reason to download and install an older version.

---


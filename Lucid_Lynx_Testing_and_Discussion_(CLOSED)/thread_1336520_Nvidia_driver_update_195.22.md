---
title: "Nvidia driver update 195.22"
date: 2009-11-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hype on 2009-11-24
Hi, 
just noticed the arrival of a new Nvidia driver !
check out here:
 [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.22/](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.22/) for 64bit version.

More info about the driver on [Phoronix ]("http://www.phoronix.com/scan.php?page=news_item&px=NzY4MA").
They'll probably post an update about the driver release soon !

About to test on a 8600GT, not exepcting much change tho :D

---

### Post by RedSingularity on 2009-11-24
I wonder when someone will make it a PPA for easy install???

---

### Post by jmmL on 2009-11-24
Here's the forum post by Aaron:
[http://www.nvnews.net/vbulletin/showthread.php?p=2129618](http://www.nvnews.net/vbulletin/showthread.php?p=2129618)

---

### Post by darco on 2009-11-24
I'm on it!


darco

---

### Post by 3vi1 on 2009-11-26
On it as in running the driver, or creating a ppa package?  :)

---

### Post by buzzmandt on 2009-11-27
i am running it, from nvidia installer.... very good.  It's the first one that has worked with this machine since karmic.  I'm quite pleased

Edit:  oh ya, nvidia geforce 5500 fx

---

### Post by ubername on 2009-11-28
Also running it. I get weird multi-coloured ascii-character sized blocks obliterating the screen on resume from suspend (or hibernate - whichever it is that happens when the 'put the computer to sleep ---' function of power management kicks in). ctl-alt-f1-6 does nothing. I need to reboot to get back.

Anyone else with this?

---

### Post by joey-elijah on 2009-11-29
Also running it with an 8500gt and my word, whether it's just an improvement over the last or not, it works much much better - from desktop effects being immensely slicker and less tear-y. Video playback is almost perfect now - hardly ever notice a horizontal tear in videos now. 

I've never found installing nvidia drivers an issue; i know people want a PPA. 

it's a five step process that takes less than 3 minutes... 

Alt+f1
kill gdm 
cd to driver and run it
click yes yes yes yes
restart

If people don't want the "hassle" of that they should stay with the supported drivers.

---

### Post by sdowney717 on 2009-11-30
just did it for karmic and all is well

download it here, i used the driver with pkg1, it has more stuff in it
[ftp://download.nvidia.com/XFree86/Linux-x86/195.22/](ftp://download.nvidia.com/XFree86/Linux-x86/195.22/)

go into nautilus, right click and make it executable

hit the keyboard cntrl-alt-F1

login with user and password

CD to the installer

stop gdm or it wont install

sudo gdm stop or sudo stop gdm

run the installer

sudo sh ./packagename.run

answer yes to everything

sudo reboot

the readme says there is an uninstall utility built in to the installer
[ftp://download.nvidia.com/XFree86/Linux-x86/195.22/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/195.22/README/README.txt)

the installer also successfully merged my old xorg.conf with tv out into the newly generated one.

---

### Post by Luptor on 2009-12-16
[Installare da** **Repository i driver Nvidia 195.22]("http://www.crismonblog.org/ubuntu/karmic-koala-repository-driver-nvidia-195.22-1%C2%B0-parte.html") (Tutorial for Italian "karmic" user) 

Tnk

---


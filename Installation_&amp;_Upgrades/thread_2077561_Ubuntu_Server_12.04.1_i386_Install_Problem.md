---
title: "Ubuntu Server 12.04.1 i386 Install Problem"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by builtfordtough on 2012-10-28
So as i was going about installing Ubuntu Server 12.04.1 LTS i386 on my Dell Poweredge 2600. I got all the way to installing the base system when this message popped up: "Please insert the disc labeled: 'Ubuntu-Server 12.0.4.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)' in the drive '/media/cdrom/' and press enter"

As far as i know the iso i downloaded is that release version, the name on the CD is ubuntu-12.04.1-server-i386. And that is what the iso was called so i left it at that. Any help would be greatly appreciated. I am installing this with all 6 36.4 GB drives that were all formatted (no other OS is going on there or is on there). If you need any other info to help me out with this, please feel free to ask.

-Thanx

P.S, i am fairly new to Linux

---

### Post by jerrrys on 2012-10-29
You need to comment out (#) the entry in your  /etc/apt/sources.list that says something like CDrom bla bla bla.  Its at the top of the sources.list.

---

### Post by builtfordtough on 2012-10-30
Thanx for the reply jerry! This seems easy to do, but how do i get there? Edit the file on the disc with lets sa my laptop, then save the changes or...sorry for sounding stupid, but i am new to linux and want to start gaining some knowledge on it, as i just got a job at a computer repair store and it would just be useful to know more than Windows!

---

### Post by mastablasta on 2012-10-30
*cd* is change directory command
 
if you are not familiar wiht command line interface in linux then perhaps you need to install a GUI (maybe one of desktops or windows managers)?
 
if you want to stay with CLI then here is a good free ebook: [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by jerrrys on 2012-10-30
The command is:

sudo nano /etc/apt/sources.list

Also this may help

[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

Like mastablasta said, you may be better off starting with a GUI.  You could add several basic desktops to a server, so here's an example.  To add the fullblown ubuntu desktop:

sudo apt-get install ubuntu-desktop

To add a lighter version:

sudo apt-get install xfce

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en")

Before you do anything you need to update your fresh install:

sudo apt-get update

sudo apt-get upgrade

Any other questions?

---

### Post by inicdominus on 2013-05-11
> **jerrrys said:**
> You need to comment out (#) the entry in your  /etc/apt/sources.list that says something like CDrom bla bla bla.  Its at the top of the sources.list.

Hey everyone,

I hope this thread still going, i am having the same problem.
when i checked the sources list, it was alreaded commented out so i uncommented and had the same problem. (then put comment back)
i have made an install cd from 3 different computers and a usb thumbdrive so i dont think cd/usb integrity is the problem.
:confused:

thank you in advance!
Dominic

---

### Post by steeldriver on 2013-05-11
Hmm well there used to be a problem with the Server iso in which some filenames got truncated - discussion + some workarounds here:

[http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

I *think* what worked for me was the method posted by 'ajay' (adding a copy of the iso as well as burning the image, then pointing the installer at the iso)

This may not be your issue though

---

### Post by inicdominus on 2013-05-11
Thank you for responding! ill give that a shot

---


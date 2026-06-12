---
title: "No Graphical Display"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by tbrothers on 2007-09-29
I'm new to Linux and need a little help.  I just installed ubuntu for the first time.  It was a fresh install of version 7.04 server.  I wanted a graphical display so I did the following.

sudo aptitude install ubuntu-desktop

It appeared to install OK.  I then typed the following command.

sudo /etc/init.d/gdm start

The problem is that gdm does not exist in the /etc/init.d directory.

Can someone help me get to Gnome?

Thanks,
Terry

---

### Post by Pumalite on 2007-09-29
What happens when you reboot?

---

### Post by tbrothers on 2007-09-29
It takes me straight to the command login.  I read somewhere to try Ctrl-Alt-F7 but that didn't help either.

Terry

---

### Post by Pumalite on 2007-09-29
Do you see a Grub with a menu, before it takes you to the command line?

---

### Post by tbrothers on 2007-09-29
Yes.  Pressing escape displays a menu ...

Ubuntu kernel 2.6.20-15-server
Ubuntu recovery something
Ubuntu x86 memory something

---

### Post by Pumalite on 2007-09-29
Have you tried to get into recovery?

---

### Post by tbrothers on 2007-09-29
Yes - Didn't make a difference.  Still just got the command login.

---

### Post by Pumalite on 2007-09-29
At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by tbrothers on 2007-09-29
Says xserver-xorg is not installed.  Should I do the following?

sudo aptitute install xserver-xorg

---

### Post by Pumalite on 2007-09-29
That means you don't have a system installed. Lets start from scratch and post your specs.

---

### Post by tbrothers on 2007-09-29
What do you mean my specs?

---

### Post by Pumalite on 2007-09-29
Desktop?Laptop?Processor?Memory?Graphics?How many drives?What system do you have installed now?

---

### Post by tbrothers on 2007-09-29
HP dc5000 MT, 1-GB RAM, 300-GB HDD
Ubuntu Server 7.04

Ubuntu installed fine.  I've installed Midnight Commander and can navigate the file system.

---

### Post by tbrothers on 2007-09-29
Continued ...

P4 3 GHz, integrated Intel graphics, integrated Broadcom nic

---

### Post by Pumalite on 2007-09-29
OK. After you do:
sudo apt-get install ubuntu-desktop
Try: startx
(I hope you are connected to the Internet)

---

### Post by tbrothers on 2007-09-29
Says cannot start X
No such file ... Aborting

Yes - I am definitely connected to the internet.

The way I installed Ubuntu is by downloading the ISO image from the Ubuntu site.  I boot from the CD and 15 minutes later the installation was complete.  The only questions I was asked during the installation were do I want to install LAMP and DNS.  I selected yes to both.  Once the installation was complete I ran the commands from the following web site to install Gnome.  It took a while to install because it appeared to install OpenOffice and a lot of other desktop components.  The installation did not give any errors.

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Terry

---

### Post by Pumalite on 2007-09-29
Did you do md5sum on the iso? Did you burn at 4x? Did you check for corruption of the CD after burn and before install?

---

### Post by tbrothers on 2007-09-29
I have a graphical display now.  Just for kicks I ran the exact same install command again to see if it would tell me it was already installed.  It pulled down 89MB of packages including xserver-xorg.  When it was complete I reboot the server and got a graphical login.

Thanks for your help!!

Terry

---

### Post by Pumalite on 2007-09-29
Finally!! Glad you got it working.

---


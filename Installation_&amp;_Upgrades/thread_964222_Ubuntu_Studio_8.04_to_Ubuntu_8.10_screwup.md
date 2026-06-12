---
title: "Ubuntu Studio 8.04 to Ubuntu 8.10 screwup"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by fprintf on 2008-10-30
I tried upgrading to Ubuntu 8.10 today from Ubuntu Studio 8.04. I didn't care for Ubuntu studio. I did the upgrade via Synaptic but now I cannot start X even after doing: 
> 
sudo dpkg-reconfigure xserver-xorg
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade


I have quite a few personal files on this laptop, so I'd rather not do a clean install (especially if I cannot get Samba started to pull the files off of it). 

Any suggestions how to get a nice clean install while keeping most of my $HOME directory intact?  I'd even be willing to just have 8.04 just to get my laptop working!

Thanks in advance!

---

### Post by fprintf on 2008-10-31
So I have been playing with this laptop for hours. The best I can do is get to a screen saying "Ubuntu is running in low-graphics mode" which then leads to a series of questions and I can get to an 800x600 display. If I reboot then I have to start all over again.  At least I can get to a command line if I need to. 

I need to figure this thing out, it is getting frustrating!

edit: looking at the logs, I get an error
> cp: cannot stat '/etc/X11/xorg_conf':
No such file or directory

---


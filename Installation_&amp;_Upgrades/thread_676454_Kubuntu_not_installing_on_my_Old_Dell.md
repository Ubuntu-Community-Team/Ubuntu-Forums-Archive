---
title: "Kubuntu not installing on my Old Dell"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by jhend60 on 2008-01-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/185510](https://bugs.launchpad.net/ubuntu/+bug/185510) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a intel 82810 graphics card which is quite buggy. 
When I load kubuntu live cd ( i havent installed it yet) normally, 
the screen goes blank after loading, but when I use it in safe graphics mode with VGA, 
after loading, it shows a non-moving colour bar at the top of the screen. 
After that I can not do anything and do not see any movement so i have to reboot. 
I would really appreciate some help on this. 
Also, with my XP, when I originally installed it, it too would not load 
untill i downloaded and installed the driver in safe mode.

I have an Intel Celeron Processer, a PC about 6 Years old, 512 MB Ram, a CRT monitor, and the rest. I have spoken on the MIRC channels 
but noone seems to be able to help me. 
If anyone can help me come up with a solution, please email [email]jhend60@gmail.com[/email].

PS i have a desktop PC.
BTW I have never used any linux distribution before, only windows, so if this is apparently really easy to fix dont blame me. Also, I have checked the CD for faults and there is none, and it is a brand new just downloaded version of Kubuntu Gutsy Gibbon.

Heres what happens
I boot up onto the Kubuntu CD
Then, I press Start/Install Kubuntu
It shows Kubuntu loading with a bouncing blue box, then loads a straight line
After it loads, the screen goes completely blank
It is a graphics driver problem

Otherwise, I go
Start Kubuntu in safe graphics mode
It loads again
THen, after 5 seconds, a line appears at the top of the screen. it is long, and cycles through 3 colours repetedly. THis could mean a graphics error.
If it is, how could I put my Intel 82810 graphics driver onto Kubuntu( the only way I see it working)

My Specs
(already above)
I have INtel 82810 Intergrated Graphics Card
Intel Celeron 1Ghz Processor
512Mb RAM
WInXP Home Already INstalled

I am trying to run this live as a preview, not install it yet. THanks for any1s help, coz I really need it!

I AM A NOOB :)

---

### Post by a_posse_ad_esse on 2008-01-23
I am using an Inspiron 1100 at the moment, and had problems with the display as well.  What I ended up doing was using the alternate server disk to load the base system on, then installed kubuntu-desktop through the command line.  The end result is the same.

---

### Post by Rocket2DMn on 2008-01-24
If you are stuck at the command line after install (no GUI), then try reconfiguring X and selecting the "intel" driver.  At the resolutions page, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.  You will be asked questions about your hardware, do your best to answer (use defaults if you really can't guess)
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart kdm (stop it first in case it thinks it's still running)
```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start
```

On a side note, your computer is fairly old and may not run KDE very well.  You may want to use straight up GNOME or even XFCE.  GNOME is on the default Ubuntu install and XFCE is what comes with Xubuntu.  If you choose to use either of these, you don't need to get the disk and reinstall, you can download them:
```
sudo apt-get install ubuntu-desktop
or
sudo apt-get install xubuntu-desktop
then
sudo /etc/init.d/gdm start
or
sudo /etc/init.d/xdm start
```

---


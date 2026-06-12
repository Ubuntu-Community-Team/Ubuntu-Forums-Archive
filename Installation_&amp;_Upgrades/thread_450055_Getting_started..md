---
title: "Getting started."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by sylva on 2007-05-20
Hi,

I am not new to Linux but I am new to Ubuntu. First I installed the 7.04
CD desktop. Flawless, everything worked from the get go, never a problem. Colors and graphics gorgeous on my new HP w2207.

Then I ordered the Server DVD. I deleted the partition the Desktop was in,  re-instituted the partition and formatted. Then installed from the DVD with servers. 

It started and gave me the **rootMyName**> command line prompt. However, when I typed in **startx** it demanded that **apt-get** be installed and gave me the how-to instructions. That was great, I thought, but when trying to install this program it demanded the installation of **sudo**. Then, when I obliged it said "Can't find sudo". 

Is there anything else I can do? I went into the documentation concerning **apt**-**get** and **sudo** but everything presupposes that these programs are already installed. 

Any ideas? :confused:

Thanks a bunch.

---

### Post by mikewhatever on 2007-05-21
The server edition does not have any GUI, consequently, no xserver. Why install a server anyway, especially if everything was great? Are you looking for troubles? If you still want to use it, you can get a windows manager installed.
[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by Ubimad on 2007-05-21
have installed feisty server and there is sudo included
for a gui you need install apt-get install xserver-xorg gdm xfonts-base xfonts-75dpi xfonts-100dpi 

and a windows manager like fluxbox or xfce

---

### Post by RedSquirrel on 2007-05-21
X is not installed with the server. If you want a graphical environment to work in, here's one way to get it:

```
sudo apt-get update
``````
sudo apt-get install xorg xterm gdm fluxbox firefox gksu synaptic

```Configure the X server:

```
sudo dpkg-reconfigure xserver-xorg
```Start X so you can login to Fluxbox:

```
sudo /etc/init.d/gdm start
```Obviously, you can trim that down further. For example, if you don't want to install firefox or synaptic, just leave them out. 

You could also try IceWM in place of Fluxbox. Whatever floats your boat. :)

---

### Post by sylva on 2007-05-29
Sorry for being so late. My thanks go out to all of you who have been so gracious to respond.

Since I am a networks person, it's only natural that I am looking for networking features in an OS as well. I understand Ubuntu is a free OS and am taking it as such. However that doesn't mean it has to apparently be so difficult and unintuitive to bridge the desktop with the OS's networking functions. This has been done pretty well in SUSe (well, not a free OS by far, but Linux nevertheless). 

Then, at first installation (from the CD) my HP w2207 monitor's recognition was flawless. But after installing from the DVD Ubuntu won't budge, it caps everything to 1024x768 and there's absolutely no way to reconfigure or force the OS into any resolution above the former. There's a limited resolution configurer but it only shows resolutions till 1024. It's early in the game and I am NOT by any means after turnkey software. I went through configuring Red Hat, SUSe, Caldera, Debian, etc. However, the configuration possibilities in Ubuntu are not open for me YET because I know so little about it. 

So, my question: how can I make Ubuntu recognize this monitor after it already has done it before? There are NO Linux drivers written for this monitor by HP. Are there any configuration applications that can be installed from the package manager? I also installed all of KDE's functions and programs and they work, however, configuration for the X server seems to be missing. I'll take to sudo in earnest. Interestingly, out of the blue I just pressed Ctr + Alt + F1 and it got me out of the desktop interface into the command line giving me the possibility to log in as the root. Well, I guess to you I may seem to be talking about the obvious.

I thought about reinstalling but first want to make sure that there's not another way to getting the right resolution.

Thanks :)

---


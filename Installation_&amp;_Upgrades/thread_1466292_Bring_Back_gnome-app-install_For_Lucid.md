---
title: "Bring Back gnome-app-install For Lucid"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by TK-Tex on 2010-04-30
I hate using Software Center. I can't pick more than one program to install at one time. It downloads only one program at a time.The downloads take longer.  I'm not able to look at all available programs at once. It doesn't categorise the programs on the sidebar, but instead you have to use another icon window. Gnome-app-install was just easer to use. Anyone else feel this way?

Following lines taken from other replies in this post to make it easier to do:

-You can install gnome-app-install from [this]("https://launchpad.net/%7Ehammera/+archive/ppa")  ppa repo.

-Update the repository (including the new PPA):

sudo apt-get update

-Install the gnome application installer:

sudo apt-get install gnome-app-install

-Run the gnome application installer:

gnome-app-install

---

### Post by wilee-nilee on 2010-04-30
Use the terminal or synaptic, the one you want and the one that is there that is irritating are basically for beginning users. These other two methods will work much faster.

---

### Post by snir on 2010-04-30
this guy is right...we want apps-install back!
nothing is better in this software center

---

### Post by TK-Tex on 2010-04-30
> **wilee-nilee said:**
> Use the terminal or synaptic, the one you want and the one that is there that is irritating are basically for beginning users. These other two methods will work much faster.

I understand that the Software Center is for beginners. The thing is though, gnome-app-install is still easier than software Center. If your going to make Ubuntu user friendly, then give them the easiest software to use. Using the "other two methods" is useful if you know what program you are looking for. But for those of us who are beginners or lazy (lol) we would like to be able to find the programs in a straight forward easy manner. Not being a pro linux user, I don't know how to use the terminal proficiently. And using the synaptic is only useful if you know what text to use to search for things. Don't get me wrong, those two methods are faster for those in the know, but I don't know. lol.

---

### Post by sisco311 on 2010-05-01
> **TK-Tex said:**
> I can't pick more than one program to install at one time. It downloads only one program at a time.


You don't have to wait until one application is installed, go ahead an pick another one. 

> **TK-Tex said:**
> 
The downloads take longer.

Probably because the servers are busy...

> **TK-Tex said:**
> 
 Gnome-app-install was just easer to use. Anyone else feel this way?


I like the software center better, but to be honest I prefer the CLI for package management.

You can install gnome-app-install from [this]("https://launchpad.net/%7Ehammera/+archive/ppa") ppa repo. 

NOTE1: It conflicts with software center, it will remove it.
NOTE2: Installing software from third party repos is always a security risk.

---

### Post by TK-Tex on 2010-05-01
> **sisco311 said:**
> You don't have to wait until one application is installed, go ahead an pick another one. 



Probably because the servers are busy...



I like the software center better, but to be honest I prefer the CLI for package management.

You can install gnome-app-install from [this]("http://https://launchpad.net/%7Ehammera/+archive/ppa") ppa repo. 

NOTE1: It conflicts with software center, it will remove it.
NOTE2: Installing software from third party repos is always a security risk.

Link doesn't work. Please fix. Thanks!

---

### Post by sisco311 on 2010-05-01
> **TK-Tex said:**
> Link doesn't work. Please fix. Thanks!
Oh, sorry, fixed.

---

### Post by TK-Tex on 2010-05-01
> **sisco311 said:**
> Oh, sorry, fixed.

Thank you very much. Now people will have a way to reinstall this program by coming here.

---

### Post by solgius on 2010-05-02
> **TK-Tex said:**
> I understand that the Software Center is for beginners. The thing is though, gnome-app-install is still easier than software Center. If your going to make Ubuntu user friendly, then give them the easiest software to use. Using the "other two methods" is useful if you know what program you are looking for. But for those of us who are beginners or lazy (lol) we would like to be able to find the programs in a straight forward easy manner. Not being a pro linux user, I don't know how to use the terminal proficiently. And using the synaptic is only useful if you know what text to use to search for things. Don't get me wrong, those two methods are faster for those in the know, but I don't know. lol.

i agree with you: i would like to use the old gnome-app-install, because it was faster when you need to read the description of a packet, easier (you can check more applications with one click, without going up and down in the pages), and allows me to see the opinion of users on each software (which is an important feature if you don't know the software you need to install and have different choices).
it also allows to sort applications by name or user's preference.
let's hope to see it again in lucid.... :(

---

### Post by Youresorock on 2010-05-06
I thought everyone was overreacting when I read this thread.  9.10 didn't ship with gnome-app-install either.  However **after I just installed it** on a fresh 10.04 box I realized what the commotion was about.

```
~$ gnome-app-install
gnome-app-install: command not found
```

```
find / -name 'gnome-app-install' 2>/dev/null
```

You get the config folder in /etc and the docs folder in /usr/share/doc

No App!  What's the point of it being an installable package?

gnome-app-install was the fastest way to go when setting up a new box.  Queue up a ton of stuff while searching.  I'm bummed to lose it.

---

### Post by isbiyanto on 2010-05-07
hot discussion :guitar:

---

### Post by sisco311 on 2010-05-07
> **Youresorock said:**
> I thought everyone was overreacting when I read this thread.  9.10 didn't ship with gnome-app-install either.  However **after I just installed it** on a fresh 10.04 box I realized what the commotion was about.

```
~$ gnome-app-install
gnome-app-install: command not found
```

```
find / -name 'gnome-app-install' 2>/dev/null
```

You get the config folder in /etc and the docs folder in /usr/share/doc

No App!  What's the point of it being an installable package?

gnome-app-install was the fastest way to go when setting up a new box.  Queue up a ton of stuff while searching.  I'm bummed to lose it.

In Lucid, gnome-app-install is a dummy upgrade package so that gnome-app-install users get software-center on upgrades.

You can still install gnome-app-install from a ppa repository (see my first post) but it will remove software center.

---

### Post by gnumaru on 2010-05-08
It is possible to have both software center and gnome-app-install installed on ubuntu 10.04 Lucid lynx

First, add the repo indicated by sisco311
sudo add-apt-repository ppa:hammera/ppa

Second, before installing gnome-app-install, uninstall the package "ubuntu-desktop" (a dummy package) and remove the software center entry on /var/lib/dpkg/status.
sudo gedit /var/lib/dpkg/status
Then, delete the lines:

------------------------------
Package: software-center
Status: install ok installed
(...)
 access on the computer.
Python-Version: current
------------------------------

This will fool the system, making it think software center is not installed, when in fact we know it is.

---

### Post by ffonz on 2010-05-29
Thanks for the tip, gnumaru.

But for complete nono's, just like me, I try to make the description more complete:

Update the repository (including the new PPA):
sudo apt-get update

Install the gnome application installer:
sudo apt-get install gnome-app-install

Run the gnome application installer:
gnome-app-install

Et voila.

Yes, finally I got my Popularity-rating back!!
:guitar:

---

### Post by solgius on 2010-06-29
thank u very much... i was getting crazy with ubuntu software center... i finally have back all the features and fast access to every information i need through gnome-app-install... thank guys... it's the best way to start this new day! ;)

---

### Post by andriy.gerasika on 2010-10-25
does not work in Maverick, says:

The following packages have unmet dependencies:
 gnome-app-install : Depends: python-gtkhtml2 but it is not going to be installed
                     Depends: python-sexy but it is not installable

---

### Post by TK-Tex on 2010-11-24
Here is the web site to go to and get gnome-app-install. (Add/Remove Programs)

[http://packages.debian.org/lenny/all/gnome-app-install/download](http://packages.debian.org/lenny/all/gnome-app-install/download)

Enjoy!!!

---

### Post by gerix76 on 2010-11-28
> **TK-Tex said:**
> Here is the web site to go to and get gnome-app-install. (Add/Remove Programs)

[http://packages.debian.org/lenny/all/gnome-app-install/download](http://packages.debian.org/lenny/all/gnome-app-install/download)

Enjoy!!!

thanks, but GDebi says python-sexy is required, and [http://packages.debian.org/lenny/all/python-sexy/download](http://packages.debian.org/lenny/all/python-sexy/download) does not work

---

### Post by TK-Tex on 2010-12-15
You can install gnome-app-install from [this]("https://launchpad.net/%7Ehammera/+archive/ppa") ppa repo.

---

### Post by relgames on 2011-02-06
I have the same error - it can't find python-sexy.

Any ideas?..

---

### Post by dryphi on 2011-08-23
Does this work on Natty?
I had it installed but it always hanged (hung?) on "loading universal access" so I uninstalled it.

Now I'm back to Software Center, which is marginally better with the ratings; however there is still no category view, no option to sort by rating / category / whatever, no popularity, etc etc.

I liked Add/Remove Programs SOOO much better but I'm reluctant to try and install again just to have it not work...

---


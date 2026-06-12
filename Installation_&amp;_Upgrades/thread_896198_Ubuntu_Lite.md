---
title: "Ubuntu Lite?"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by bulazeem on 2008-08-20
Is there a lightweight version of Ubuntu that i can put onto my laptop.  It's an old laptop from 1998 and based off of how Ubuntu runs on my desktop, I don't think the laptop would handle it too well.  Hardy seems kinda bloated and at times is kinda sluggish.  If not, is there any other user friendly distro out there that I could try?

---

### Post by tamoneya on 2008-08-20
yep.  Its called xubuntu.  It uses xfce instead of gnome.

---

### Post by Sef on 2008-08-20
How much ram do you have?

---

### Post by cogitordi on 2008-09-12
On a notebook of that season, Xubuntu will *not* be light-weight. People who tell you to try it have not tried it on a similar system themselves. 

I just spent a week researching how to save a 1999 notebook from landfill using Linux. I found the solution.

I wanted a solution based on Ubuntu's LTS package system. I wanted low-maintenance and easy set-up. I also wanted Firefox and wireless functionality, if possible.

Here are your real options (I tested them):

- "Crunchbang Linux" will run using about 80 MB of RAM. It uses the OpenBox window manager and a couple of panels. d

- There is a meta-distro called "UbuntuLite". It's not formally related to Canonical. You install using the Ubuntu mini iso image and then run the UbuntuLite script. I tried it and like it but it wasn't light enough. Your success will depend on the notebook's specifications. I have a Pentium 300 MHz and a generous 162 MB RAM. 

- The option I've chosen: I followed the advice in this very helpful thread:

[http://ubuntuforums.org/showthread.php?t=298835&highlight=gnome-core+gdm+firefox+synaptic](http://ubuntuforums.org/showthread.php?t=298835&highlight=gnome-core+gdm+firefox+synaptic)

The idea is to start with the Ubuntu mini iso image and install the bare CLI subset of packages. Then run specific apt-get commands to install a minimal gnome system. Doing this has given me a very usable system. 

That's really all that Crunchbang and UbuntuLite do. But Crunchbang doesn't use Gnome, and UbuntuLite installs things that I don't want. (Oh, like Evolution, say). I have Ubuntu running in the same amount of RAM as I did using Crunchbang (which uses the OpenBox window manager). 

- Damn Small Linux is based on Knoppix but damn, it is small. It will run well on your notebook. But Damn Small has a slow release schedule. You have to realize that what Canonical is doing for Ubuntu with the LTS strategy is a significant advantage for all Linux users.

---

### Post by snowpine on 2008-09-12
What are your system specs? That will make a big difference on which distros you can use. Personally, I am currently using Crunchbang on my 600mhz Pentium 3 with 256mb of ram. I also had pretty good luck with Fluxbuntu in the past. If you're willing to go outside the Ubuntu family, there are lots and lots of super-lightweight options that will be speedier, like DSL, Puppy, or SliTaz.

---


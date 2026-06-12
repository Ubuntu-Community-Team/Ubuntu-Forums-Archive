---
title: "Sound isn't working..."
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Argoneus on 2008-02-18
Hello. I just got a new NB, formatted it, installed Ubuntu 7.10, but there isn't any sound. Could you help me to fix it? Please note I'm on my desktop and on my laptop I haven't got internet.

---

### Post by Argoneus on 2008-02-18
Ah sorry!!! I forgot to mention that my laptop is [Acer Aspire 5315]("http://www.play.com/PC/PCs/4-/3477502/Acer-Aspire-5315-Celeron-M-530-1-7GHz-1GB-80GB-15-4-DVD-SM-Vista-Home-Premium-Laptop-Notebook/Product.html")

---

### Post by frodon on 2008-02-18
Open a terminal and enter the following command :
```
sudo apt-get install linux-backports-modules
```Then :
```
sudo gedit /etc/modprobe.d/alsa-base
```and at the end of the file add :
> options snd-hda-intel model=acerAnd finally reboot.

The reason is that sound cards used in acer laptops are rather new and the default version of sound drivers in gutsy don't support these new cards.

Tell me if it solved your problem or if you still have issues.

---

### Post by Argoneus on 2008-02-18
It says it can't find package linux-backports-modules

---

### Post by frodon on 2008-02-18
Enable all your repositories first (main, restricted, multiverse and unisverse). You can do this in synaptic package manager clicking on "repositories" in the setting menu. Once added press the refresh button and close synaptic.

---

### Post by Argoneus on 2008-02-18
I don't get it... By the way the laptop doesn't have internet connection...

---

### Post by frodon on 2008-02-18
> **Argoneus said:**
> I don't get it... By the way the laptop doesn't have internet connection...Ok that's impossible to install this that way without internet connection unfortunately, the easiest for you would be to find an internet connection maybe friend's connection.
Otherwise you will have to download the package and install it manually on local.

[https://launchpad.net/ubuntu/gutsy/+source/linux-backports-modules-2.6.22/2.6.22-14.10](https://launchpad.net/ubuntu/gutsy/+source/linux-backports-modules-2.6.22/2.6.22-14.10)

---

### Post by Argoneus on 2008-02-18
> **Argoneus said:**
> Hello. I just got a new NB, formatted it, installed Ubuntu 7.10, but there isn't any sound. Could you help me to fix it? Please note I'm on my desktop and **on my laptop I haven't got internet**.
Well, is there a way to download it to my desktop PC and then to laptop?

---

### Post by ajgreeny on 2008-02-18
You can use synaptic on your desktop, I'm assuming it has ubuntu installed at the moment, set it to "Download package files only" at the point where you click on "Apply" and the package will be put into /var/cache/apt/archives.  You can then copy that package from your desktop to laptop and double click it to install.  There may be some dependencies as well which will be downloaded and you will need to copy and install those as well.

If that seems a bit of a palaver, put aptoncd onto both machines and it will all be done with a terrific gui.  You will need to use my first method to get aptoncd onto the laptop, though, so you might as well use that method to install whatever you need on the laptop.

---

### Post by Argoneus on 2008-02-18
the desktop has windows xp MCE SP 2

---

### Post by ajgreeny on 2008-02-18
So go to [http://packages.ubuntu.com/gutsy/base/](http://packages.ubuntu.com/gutsy/base/) and download the ones you need and do the same with them.  I windows you will download the files to wherever you have the system set, but after that it will be the same arrangement, though it will not be quite so simple to sort out the dependencies.

---

### Post by frodon on 2008-02-18
> **Argoneus said:**
> Well, is there a way to download it to my desktop PC and then to laptop?I gave you the link in my post, at the right all the builds are available depending of your architecture.
Download the right deb file on your desktop then double click on it to install, as said by ajgreeny you may miss some dependencies and have to download some more packages.

If you are not comfortable with this you have still the possibility to download and burn the ubuntu repositories dvds, then you would just have to configure synaptic to search on the dvd for packages, as you can see in the following link it is big (5 DVDs)..
[ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/](ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/)

---


---
title: "Minimal Xubuntu Install"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by RippyMan on 2006-11-22
Hi All,

I have recently acquired a 850 mhz PC (homemade, brand unknown). My goal is to make it into a dedicated Linux file server. Currently it is running Ubuntu Server install without anything on it. However, I would like to have a GUI on the server so that I can administer it with less difficulty and be able to check files more easily. I want the minimum installed on it as possible, almost exclusively Samba and a file manager. So I was wondering, is it possible to install Xfce without all of the normal components that would come with it in a desktop install (abiword, gnumeric, xfburn, thunderbird, firefox, etc.)? Really all I would need is Thunar, Mousepad, Terminal, Synaptic, and Samba (am I leaving anything out?). Is this possible or will I be forced to get rid of everything after installing xubuntu?

Thanks,
RippyMan

---

### Post by n3Cre0 on 2006-11-22
Please post your RAM. Imho the most important

---

### Post by RippyMan on 2006-11-22
The computer has 512mb Ram and 850mhz Athlon Processor. Also it has a 20GB HD. Certainly not stellar specs, but definetely enough to run Xubuntu.

---

### Post by aysiu on 2006-11-22
It's definitely possible and quite easy to do: ```
sudo aptitude update
sudo aptitude install x-window-system-core thunar xfce4 mousepad xterm synaptic gksu samba
```

---

### Post by RippyMan on 2006-11-22
> **aysiu said:**
> It's definitely possible and quite easy to do: ```
sudo aptitude update
sudo aptitude install x-window-system-core thunar xfce4 mousepad xterm synaptic gksu samba
```

Awesome! I will go ahead and see if that works. Thank you!

---

### Post by aysiu on 2006-11-22
You may need to enable the universe repositories first, but otherwise it should work.

Don't forget about ```
startx
``` afterwards to actually get the graphics working.

---

### Post by kerry_s on 2006-11-22
> **aysiu said:**
> It's definitely possible and quite easy to do: ```
sudo aptitude update
sudo aptitude install x-window-system-core thunar xfce4 mousepad xterm synaptic gksu samba
```

Just to let you know, x-window-system-core includes xterm & xfce4 includes thunar. So you can shorten it.->

sudo aptitude install x-window-system-core xfce4 mousepad synaptic gksu samba

Also if you want to save space you can drop the gksu & just link it to sudo->

sudo ln -s /usr/bin/sudo /usr/bin/gksu

Not that it matters but using leafpad(500kb) in place of mousepad(1548kb) will spare some space. mousepad was built on leafpad and they look exactly the same.

---

### Post by kerry_s on 2006-11-22
Just incase your interested i did a simple how to auto login with out a login manager-> [http://www.ubuntuforums.org/showthread.php?t=303319](http://www.ubuntuforums.org/showthread.php?t=303319)

Personally though i'd just go for gdm->

sudo aptitude install x-window-system-core gdm xfce4 leafpad synaptic samba


gdm includes gksu.

---

### Post by RippyMan on 2006-11-22
aysiu,

At one point in the install should I do **startx**? Is it something I should do afterwards in xterm in xubuntu or should it be done in Ubuntu Server? Just wondering.

kerry_S,

I will definitely look into your suggestions. I have not heard of leafpad but I will definitely consider it. My question is: I wonder why they created mousepad if leafpad already did the same ting? I'm glad you told me about it though. I originally considered even not installing a GUI text editor and just using nano exclusively, but then I figured that would become somewhat inconvenient.

Both of you, thanks again for your help.
RippyMan

---

### Post by kerry_s on 2006-11-22
> **RippyMan said:**
> aysiu,

At one point in the install should I do **startx**? Is it something I should do afterwards in xterm in xubuntu or should it be done in Ubuntu Server? Just wondering.

kerry_S,

I will definitely look into your suggestions. I have not heard of leafpad but I will definitely consider it. My question is: I wonder why they created mousepad if leafpad already did the same ting? I'm glad you told me about it though. I originally considered even not installing a GUI text editor and just using nano exclusively, but then I figured that would become somewhat inconvenient.

Both of you, thanks again for your help.
RippyMan


The "startx" would be used after you login at startup to get you to the gui.

I just spent the weekend teaching some friends how to do there own custom installs & we did alot of installs trying alot of different setups, from the smallest we could get to the fastest working setup. We tried every WM in the repos. Let me tell you there are alot of options when you go custom. But it's east to learn and it always starts the same. Substitute apt-get with aptitude, i'm a apt-get person->

Command-line system install

sudo su  <- makes you root

nano /etc/apt/sources.list  <-comment(#) out the cdrom & uncomment all the repos(they start with deb)> ctrl+x & y & enter to save

apt-get update

apt-get install x-window-system-core gdm


Once you have that done you can install any setup, examples->

apt-get install fluxbox etc....
apt-get install jwm etc...
apt-get install icewm etc...


Sorry, i'm still in teaching mode. Just play with it and have fun.

---

### Post by RippyMan on 2006-11-22
Thanks again everyone for your help. Kerry_s, I did your set of commands, [B]
sudo aptitude install x-window-system-core gdm xfce4 leafpad synaptic samba[/B], and it installed fine. However, I haven't been able to get it to work and that's not because of your settings. On startup, I get the following error in the xserver log: **Fatal Server Error: no screens found**. I tried to boot Xubuntu Live CD and received the same error, so it's not a software issue but a hardware issue most likely. Like I said originally, it's a homemade PC and thus the hardware is not entirely known. I will have to find out more about it before installing Xubuntu. At least I know it works with Ubuntu Server. For now it is something to play around with.

Cheers,
RippyMan

---

### Post by K.Mandla on 2006-11-22
It's possible you could try *sudo dpkg-reconfigure xserver-xorg* and correct the settings, or directly edit /etc/X11/xorg.conf to avoid that error. In my experience, that usually happens when there's some sort of conflict between the settings and the hardware.

In the future, if you want to further trim that list of programs to install for a minimal XFCE, I usually slim it down to just *sudo aptitude install x-window-system-core xfce4*. 

Of course, you have to be willing to log in at the terminal and start the GUI manually, since you don't have gdm. 

And you wouldn't have synaptic to play with. 

And. ... ;)

---

### Post by kerry_s on 2006-11-23
> **RippyMan said:**
> Thanks again everyone for your help. Kerry_s, I did your set of commands, [B]
sudo aptitude install x-window-system-core gdm xfce4 leafpad synaptic samba[/B], and it installed fine. However, I haven't been able to get it to work and that's not because of your settings. On startup, I get the following error in the xserver log: **Fatal Server Error: no screens found**. I tried to boot Xubuntu Live CD and received the same error, so it's not a software issue but a hardware issue most likely. Like I said originally, it's a homemade PC and thus the hardware is not entirely known. I will have to find out more about it before installing Xubuntu. At least I know it works with Ubuntu Server. For now it is something to play around with.

Cheers,
RippyMan

 Do you know what kind of video card/built-in you have?Do>   
nano /var/log/Xorg.0.log

To view your log, the ee are errors.

---

### Post by RippyMan on 2006-11-23
Okay, I did **sudo nano /var/log/Xorg.0.log** and found the following errors: **(ee) Trident (0): No Valid Modes Found**; **(ee) Screens found, but none have a usable configuration**. The card is a Trident Microsystems TGUI 9660/938X/968X PCI Video Card. I realize that we are probably getting off topic, so I will check out the Hardward forum. Thanks again.

---

### Post by kerry_s on 2006-11-23
Yeah better you start a new topic & make sure you list your system specs. Maybe someone has the same setup and has got the answer already.

---

### Post by RippyMan on 2007-01-05
I know this is very delayed, but I'd thought I should post a followup to this problem. I eventually got everything to work. It was definitely a hardware issue. The Trident card was very old and lacked the memory capable of running Ubuntu (or anything more than Windows 3.1 for that matter :) ). The lack of memory was causing X to crash. I installed a new nVidia card and everything worked great. I ended up installing xubuntu-system-tools also, because I wanted to create Samba shares graphically. I did this after the system was installed. Overall the whole thing worked great. I am now able to serve up Samba shares with the minimal amount of software, though I am still having some problems with Samba (mostly unsolved and unexplained permissions issues). I would like to thank everyone again for their help.

RippyMan

---


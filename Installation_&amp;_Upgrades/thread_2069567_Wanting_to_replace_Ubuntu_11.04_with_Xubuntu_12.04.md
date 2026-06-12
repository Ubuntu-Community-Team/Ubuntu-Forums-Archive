---
title: "Wanting to replace Ubuntu 11.04 with Xubuntu 12.04"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2012-10-11
Have been running Ubuntu on my desktop since 9.something... now on 11.04, but have not done any updates for a LONG time... I saw Unity and decided I wanted no part of that!   I have a laptop that I installed Xubuntu 12.04 on, and like the Xubuntu MUCH better than Ubuntu...  So, decided that I would put Xubuntu on the desktop.  Found this page:  [http://xubuntu.org/upgrading/](http://xubuntu.org/upgrading/)

And it says:  
> Install Xubuntu from Ubuntu:  
If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. Next time you login, you can choose Xubuntu from the Session menu on the login screen.

If you want to have a default Xubuntu install but have installed Ubuntu or Kubuntu, you can remove all Gnome and KDE packages by following instructions on this page.

So, I did that.  But, I have NO login choices, the machine simply boots up, and I'm running Ubuntu.  I went to <Control Center> <Login screen> and set it to log into the Xubuntu when I boot up, but nope, didn't happen...

The above "instructions on this page" refers to [http://www.psychocats.net/ubuntu/purexfcenatty](http://www.psychocats.net/ubuntu/purexfcenatty), and  tells how to eliminate Ubuntu and only leave Xubuntu, but I'm not sure that I wanna go there...  

So, wondering if anyone else has done this and if there are any tricks?  Thinking I maybe need to remove Ubuntu, boot from Xubuntu CD and install?  If so, what do I need to back up?  Looking at possible long time project?

TIA  DK

---

### Post by vasa1 on 2012-10-11
> **dkolars said:**
> ...

**So, I did that**.  But, I have NO login choices, the machine simply boots up, and I'm running Ubuntu...
Do you recall the exact steps? Could you list them? I feel you may have done something differently.

---

### Post by dkolars on 2012-10-11
> Do you recall the exact steps? Could you list them?

I went into Synaptic Pkg. Mgr., selected "xubuntu-desktop" [Ver 2.128], which then also selected "xubuntu-default-settings" [ver 11.04.18], and installed them.  Re-booted, and nothing different... no choice of OS at login...  I did notice that I see the Xubuntu "critter" logo at log-off for a split second, so I'm guessing that something from Xubuntu is running in the background?

Looking at my running processes, I see nothing that references Xubuntu...  Only 1 'xf..." file (xfconfd).  On my laptop, there are 9 'xf..." files loaded, so it would appear that Xubuntu is not active on the desktop.

Thanks!

---

### Post by pqwoerituytrueiwoq on 2012-10-11
i think this is the guide you want
[http://www.psychocats.net/ubuntu/purexfceoneiric](http://www.psychocats.net/ubuntu/purexfceoneiric)
to install xubuntu
```
sudo apt-get install xubuntu-desktop
```

11.04 has to upgrade to 11.10 then to 12.04

---

### Post by dkolars on 2012-10-11
> i think this is the guide you want

That is the link that I posted in my original article...  running the sudo command tells me that I have the lastest version installed.  My problem is that I am not give the choice at login to run either Ubuntu 11.04 or Xubuntu...  It boots straight into Ubuntu 11.04.  So, while I understand that I will need to upgrade the Xubuntu 2x to get it to 12.04, I have to be able to RUN it first!!

I have the .iso for 12.04 on CD, but don't want to lose all my "stuff" that currently resides under Ubuntu 11.04 should a new install decide to overwrite things... not familiar enuf with the process to know what will happen...

---

### Post by vasa1 on 2012-10-11
I don't fully understand what's going on but I'm thinking you want to upgrade your **U**buntu 11.04 to **X**ubuntu 12.04.

If my understanding of your intention is correct, I don't think that that is possible (or, if it is possible, it won't be easy.

To be on the safe side, back up your data completely elsewhere. Then, if you're sure you want Xubuntu and if you're sure you want to stay on LTS, download Xubuntu 12.04 and do a clean install on your machine.

Otherwise, wait for a few days and get Xubuntu 12.10 which has Xfce 4.10 instead of 4.8.

---

### Post by dkolars on 2012-10-11
Yes, I'm wanting to change my OS from Ubuntu 11.04 to Xubuntu 12.04... didn't think of it as an "upgrade"...  That was my concern, the switch from U to Xu...  I was thinking that I might need to uninstall U and then do a clean install of Xu... Yes, I'd like to stay with the LTS!!  Much easier time-wise for me...  Thanks...  DK

---

### Post by lykwydchykyn on 2012-10-11
Both are built from the same base, pull from the same repositories, and share a majority of the same core packages.  The difference is in which desktop packages are installed.  

So, this is perfectly possible and shouldn't be that hard.  If you installed xubuntu-desktop and it's not showing up as a session option in the login screen, that would indicate that it didn't install properly.

Can you enter this into a terminal screen and paste the output you get:

```

sudo apt-get install xubuntu-desktop

```

---

### Post by dkolars on 2012-10-11
> Can you enter this into a terminal screen and paste the output you get:
Code:  sudo apt-get install xubuntu-desktop

Why, sure thing... already did that earlier...   Looking at this I'd say all is well...  But, nothing is different with my login/screen/etc., so not sure what is happening...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 370 not upgraded

When I did a new install on my laptop from the CD, it was a LOT different... so, maybe Xu is using my settings from U???  I was expecting to have to set "stuff" up...

---

### Post by darkod on 2012-10-11
OK, hold on.

1. Do you have your ubuntu set up to auto login, or it displays the login page where you enter your password under your name?

2. If it stops at the login screen, next to your name you will see an icon like the ubuntu logo. Click on it and it should display other environment options, the recently installed xubuntu desktop should be one of them. Just select it, enter your password as normal, and it should boot the "other" desktop.

The last booted option is remembered, so next time if you want to login to xubuntu again, you only type your password.

---

### Post by dkolars on 2012-10-11
I must have it set to Auto Login, as I do not enter a password...  I'd like to get rid of the whole password thing, but that's a different thread...

Wanted to put in a screenshot of my settings, but can't do that here, I guess...  

I have it set to login as me automatically, and Select "Xubuntu Session" as default session.  My choices for default sessions are:

[LIST]
[*]Recovery Console
[*]Ubuntu
[*]Ubuntu Classic
[*]Ubuntu (Safe Mode)
[*]Xubuntu Session
[*]User Defined
[*]Ubuntu Classic (No effects)
[*]Xfce Session
[/LIST]

So, I was assuming that the Xubuntu Session should be what starts up, not the Ubuntu that I had before.

---

### Post by Frogs Hair on 2012-10-11
The upgrade instruction for Xubuntu in the first post will  work  only in you start with a  base installation of Xubuntu . Starting with the Ubuntu , installing the Xubuntu desktop and then trying to do an upgrade  to Xubuntu 12.04 won't work . As stated above the session list in the login screen has changed positions.

---

### Post by Frogs Hair on 2012-10-11
> So, I was assuming that the Xubuntu Session should be what starts up, not the Ubuntu that I had before.If you started with Ubuntu you will have to change the default session for auto login  via the command line. Methods vary depending version but I know it can be done.

---

### Post by dkolars on 2012-10-11
Well, I set my login prefs so that I had to choose a user (only one choice) and enter my pw... no place to choose anything else, but the Xubuntu screen showed up, then was replaced by my Ubuntu desktop wallpaper and icons...  so, Xubuntu is running and using my prefs from Ubuntu by the look of it...  Hmmm...

Guess I'll have to backup everything (not sure exactly which "everything" I need to back up) and delete Ubuntu 11.04and install Xubuntu 12.04.  The difference in speed on my laptop between the two was amazing... Xubuntu boots in about half the time, loads programs quicker, Chrome doesn't hang up when I have too many things open... I tried them both from the Live CD before I went with Xubuntu...

Perhaps next week I'll have time...  must finish building a ukulele and repairing a 1910's mandolin.  

Thanks for all the assists!!

---


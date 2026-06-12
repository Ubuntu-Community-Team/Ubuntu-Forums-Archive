---
title: "So maybe this (upgrading) was a bad idea...."
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Ancalagon82 on 2010-01-23
So... yeah.  Decided I would put on my 'Big Damn Hero' hat and venture in the wilds of Ubuntu.   My Mini9 w/Ubuntu has been great this past year, but mostly b/c I haven't tried to actually DO anything.   Maybe that was the correct decision.

Anyway, it seems my first step failed.  I looked up how to upgrade via USB and according to [here](https://help.ubuntu.com/community/Installation/FromUSBStick) the first step is to install the USB-Creator.

This is what I got though when I did what they said:

matthew@matthew:~$ sudo apt-get install usb-creator
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package usb-creator


Besides thinking I do anything with this computer in the first place, where did I go wrong?

---

### Post by Fir3chi3f on 2010-01-23
Is there any reason you don't want to just upgrade within your current installation? 

If you click on System>Administration>Update manager does it say at the top: "New distribution release '9.10' is available"?

---

### Post by Ancalagon82 on 2010-01-23
> **Fir3chi3f said:**
> Is there any reason you don't want to just upgrade within your current installation? 

If you click on System>Administration>Update manager does it say at the top: "New distribution release '9.10' is available"?

At the top of what?  All I get is a little window asking if I would like to check for updates.  If I click yes, it does a check tells if there are updates available or not, and then asks if I want to install them.  I never see what the updates are or get a choice on what to upgrade or what not, it is just a yes or a no.

Oh I also get this error message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.

For that all I can click is close.  I've had that error messages since the first day I took it out of the box.

---

### Post by Fir3chi3f on 2010-01-23
From what I can tell, Dell only supports Ubuntu 8.04. Which is why it wont just ask you to upgrade. Normally that window I had you go to would ask you if you wanted to upgrade to the next version of ubuntu when released.

If you really want to upgrade try running

```
sudo update-manager -d
```

In the terminal located in Applications>Accessories>Terminal

It will ask for your password and that should force it to look for an update. I do still want to point out that Dell does not support this. 

I do not own a Dell and have no idea what might entail within this upgrade.

---

### Post by Fir3chi3f on 2010-01-23
I did want to quote some other members of the community for informational purposes on this topic. In case someone else is trying to do this and information for yourself:


From Roxbury Ranger:

> You should be careful in upgrading to 9.10. It has definite stability issues related to Intel Graphics chips. I have a PC with integrated Intel GMA950 and when I installed 9.10, it could only run on "low" graphics settings. If I tried "normal" or better, the system would freeze. 9.04 - which is quite stable contrary to rumor - could run with full graphics effects, including Compiz. Either way, both are more polished than 8.10.

If you want the latest version of Office, and an incredibly polished interface, you might want to try Mandriva 2010 One in its Live CD form. Mandriva is very end-user friendly and it uses KDE 4.3 (which I like much better than GNOME). It has very clean, crisp graphics and font representation, and includes the latest version of Open Office. It's worth a shot running it from Live CD. In that way, you can test it out without having to install it (no risk at all).

I think once you've used KDE 4.3, you'll have a hard time going back to Ubuntu GNOME. But, that's just my opinion :)

Good luck.


From ToeBee:

> Yes, you can boot from the CD without touching anything on your hard drive. That is the whole reason that Live CDs exist. As for the USB startup disk creator, that was not included in Ubuntu until 9.04 I think - maybe 8.10. And even then it didn't work for me when I was trying to make some 9.10 images. I think the bootloader they used on the 9.10 CDs was too new for that utility. What did work for me is a program called UNetbootin. Not sure how long it has been around but it was in my 9.04 repositories so if you want to make a USB startup disk, check Synaptic and see if it is there.

Always make a backup of any important files before you do any system upgrades! Doesn't matter if you are running Windows, Linux or Mac! If nothing else, get a free account on dropbox.com and sync up your documents.


You may also get more system specific information over at the Dell linux forums: [http://en.community.dell.com/forums/3523.aspx](http://en.community.dell.com/forums/3523.aspx)

---

### Post by Ancalagon82 on 2010-01-23
> **Fir3chi3f said:**
> From what I can tell, Dell only supports Ubuntu 8.04. Which is why it wont just ask you to upgrade. Normally that window I had you go to would ask you if you wanted to upgrade to the next version of ubuntu when released.

If you really want to upgrade try running

```
sudo update-manager -d
```

In the terminal located in Applications>Accessories>Terminal

It will ask for your password and that should force it to look for an update. I do still want to point out that Dell does not support this. 

I do not own a Dell and have no idea what might entail within this upgrade.

Thanks, but no dice.  It just ran the update manager same as before.  :/

---

### Post by Fir3chi3f on 2010-01-23
8.04 doesn't want to go without a fight! 

Lets fight back and try to fix those nasty update errors:
System>Administration>Software Sources

In the "Download from:" pick Server for United States. I believe that Dell might have their own server in this spot.

---

### Post by Ancalagon82 on 2010-01-24
> **Fir3chi3f said:**
> 8.04 doesn't want to go without a fight! 

Lets fight back and try to fix those nasty update errors:
System>Administration>Software Sources

In the "Download from:" pick Server for United States. I believe that Dell might have their own server in this spot.

I don't have those options.   My tabs are:  Updates, Third-Party Software, and Authentication.

Under Third-Party Software there are alot of different stuff there.  Should I unclick the Dell ones?

[http://dell-mini.archive.canonical.com/updates](http://dell-mini.archive.canonical.com/updates) hardy-dell-mini public 
[http://dell-mini.archive.canonical.com/updates](http://dell-mini.archive.canonical.com/updates) hardy-dell-mini public (Source Code)

---

### Post by Fir3chi3f on 2010-01-24
No, those aren't hurting any one.

But this is quit the pickle isn't it? You can't install usb-creator because your running 8.04, which is also locked down because of Dell, so we can't use Ubuntu's easy upgrade. Hmmm...

---

### Post by Fir3chi3f on 2010-01-24
Could you copy paste the contents of this into the thread? 


Put this code into the terminal and hit enter:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Ancalagon82 on 2010-01-24
> **Fir3chi3f said:**
> Could you copy paste the contents of this into the thread? 


Put this code into the terminal and hit enter:
```
sudo gedit /etc/apt/sources.list
```

Yep!  Thanks for the help btw.  If I disappear it's not me ignoring you but going to bed.

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse #Added by software-properties

---

### Post by Fir3chi3f on 2010-01-24
Yes, yes, I am out of coffee also..

Hopefully in the mean time someone else can chime in with a better idea, because what I'm going to suggest is a bit extreme.

Past this into the terminal:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

then:

```
sudo gedit /etc/apt/sources.list
```

at the bottom of that list you just gave me, copy all this into it:

```
##--------------------
## UBUNTU REPOSITORIES
## -------------------
deb http://my.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://my.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy universe
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://my.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://my.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://my.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main # Ubuntu Muslim Edition
deb-src http://ppa.launchpad.net/ubuntume.team/ubuntu hardy main # Ubuntu Muslim Edition
deb http://www.linuxmint.com/repository romeo/
deb http://tskariah.000webhost.com/ubuntu ubuntu main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubu...gutsy main
 ## +++ Backports & Proposed (Ubuntu Unstable) +++
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
 ## +++ Source Repositories +++
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubu...hardy main
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
 ##Universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
 ## Multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
 ## Backports
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
 ## Canonical Partner Repository
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
 ## PLF REPOSITORY
deb http://packages.medibuntu.org/ gutsy free non-free
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
 ## +++ Medibuntu +++
deb http://packages.medibuntu.org/ hardy free non-free
deb http://packages.medibuntu.org/ feisty free non-free
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubu...hardy main

```

Go to System>Administrator>Update Manager and hit the check button.
Cross your fingers, this will ether allow you to upgrade the easy way or just break your system when you hit the update button.

Make a backup off all your stuff and hope that someone else chimes in with something known to be safe. Good luck, you'll need it.

---

### Post by Ancalagon82 on 2010-01-24
What exactly is that doing?

---

### Post by benmoran on 2010-01-24
It's replacing all of the software sources with the normal Ubuntu ones, instead of the limited Dell ones.

---

### Post by snowpine on 2010-01-24
Hi Ancalagon, there is some dangerous advice on this thread, be careful. :)

The Dell Mini comes with a special "Dell branded" version of Ubuntu 8.04. This is *not* regular Ubuntu and has no upgrade available at this time. The good news is that it will be supported through April 2011, and it supports all of the Dell Mini hardware out of the box.

If you want to use a newer version of Ubuntu, you will have to do a fresh reinstall--there is no other way at this time. There are great tutorials on this site:

[http://www.ubuntumini.com](http://www.ubuntumini.com)

You can perform the install without usb-creator or an external CD drive by using a thumb drive and a handy little program called Unetbootin:

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Good luck whatever you decide... and be very cautious of advice from readers who don't have direct experience with this special "Dellbuntu" as there are many differences from "regular" Ubuntu. :)

---


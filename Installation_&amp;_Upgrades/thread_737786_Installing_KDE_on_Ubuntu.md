---
title: "Installing KDE on Ubuntu"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by chip616 on 2008-03-27
OK, I've been to the page at:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

which tells me that I need to install some meta packages in order to get KDE installed on top of Ubuntu.  I've looked through the package manager, and tried to select a package called "kubuntu-desktop" like it says in the above link, but no such package appears in the package manager.  So, lets pick one of the the following:

1)  I'm not understanding something

2) I need to have another repository added

3) The instructions are wrong

Any help appreciated.  7.10 is freshly installed on my testbed machine downstairs, and is presently doing a full update of some 200 + packages.  :)

Thanks.

Frank.

---

### Post by tubasoldier on 2008-03-27
its all in the same repository, but I do not reccomend installing "Kubuntu-desktop". It will load all the KDE packages, most which you may not use.

I would reccomend the following:

Open a terminal and copy/paste the following:
```
sudo apt-get install kdebase kde-core
```

After that you can select KDE from the sessions menu on the login screen. You can also browse through Synaptic or Add/Remove programs to install anything you like. All Gnome applications and all KDE applications will be available. 

Good Luck.

---

### Post by chip616 on 2008-03-27
tubasoldier:

> I do not reccomend installing "Kubuntu-desktop". It will load all the KDE packages, most which you may not use.

Thanks.  I wondered about that.  As you say, I sure don't need all those KDE apps!

So, the metapackages are only installable from the command line with apt-get?  Would have been nice if they had mentioned that in the instructions that I linked to in my opening post.

In any case, as soon as the update finishes, I'll go your route.

Thanks for the reply.

Frank.

---

### Post by balagunner on 2008-03-27
> **chip616 said:**
> tubasoldier:



Thanks.  I wondered about that.  As you say, I sure don't need all those KDE apps!

So, the metapackages are only installable from the command line with apt-get?  Would have been nice if they had mentioned that in the instructions that I linked to in my opening post.

In any case, as soon as the update finishes, I'll go your route.

Thanks for the reply.

Frank.

Yeh thats true, there are some stupid games and some other media players that we won't use.


anyways if u want to install just do:
**sudo apt-get install kde**

---

### Post by dlevans on 2008-03-27
I am doing this as well I had Ubuntu installed after wiping out vista and then started using kubuntu on an Acer 5610Z laptop I like the way KDE feels and looks alot better than Ubuntu but my SD/MMC reader didn't work so I put in my Ubuntu 7.10 live CD and viola the card reader started working so my "workaround" will hopefully be this...
1. Install Ubuntu (downloading the 200+ updates as I type)
2. Install the Kubuntu-Desktop (I didn't read the post soon enough I just included it with the updates)
3. Follow the Ununtu directions for getting the dreaded Broadcom Wireless Card working agin using the Ubuntu directions

hopefully my laptop will work 100% the only thing I would have left is to get the Orbi-Cam working :) any comments/tips/tricks would be helpful as I am still kinda new to this whole Linux thing

---

### Post by tubasoldier on 2008-03-28
Kubuntu-desktop metapackage is hard to clean up after. If you install the Kubuntu-desktop meta package it is best to install it with aptitude instead of apt-get. That way when you remove it, with aptitude, it will remove everything that was installed with it.

"apt-get install kde" does not work. There is no package named kde. But there are two packages, one named kdebase, and one named kde-core.

---

### Post by dlevans on 2008-03-28
I'm installing it with synaptic and if the whole kit comes with games and media players then thats fine all i do on my laptop is play games and watch movies. so is there a way to uninstall Kubuntu-Desktop with synaptic then install it your way... this always happens to me I do research then try something and a few seconds after or during I find some more research that would have helped a lot

---

### Post by dlevans on 2008-03-28
IT WORKED!!!! Installing Ubuntu first, then Kubuntu makes my wireless card work, and the card reader work. Plus I get to use the KDE (which is my personal choice) and everything works!! I'm so happy it works now  :) oh by the way I have an Acer Aspire 5610Z Laptop.

---

### Post by tubasoldier on 2008-03-28
> **dlevans said:**
> IT WORKED!!!! Installing Ubuntu first, then Kubuntu makes my wireless card work, and the card reader work. Plus I get to use the KDE (which is my personal choice) and everything works!! I'm so happy it works now  :) oh by the way I have an Acer Aspire 5610Z Laptop.

Glad to hear it. I've personally always had issues connecting nm-applet. Knetworkmanager has always worked better for me. I'm curious if it is just a hardware issue or something with using madwifi drivers?

---

### Post by dlevans on 2008-03-28
I have no idea but I've tried every ndiswrapper thing I could find to make this laptop wireless and nothing worked I knew ubuntu worked from past experiences but I didn't like the way it looked and I guess I never put two and two together (ubuntu being the basis for kubuntu) same for the card reader but I still have a couple questions:
if Kubuntu is based on/uses Ubuntu but gnome why didnt it work with just Kubuntu?
how can I burn what I have on my laptop to a cd if something goes bad?

---

### Post by chip616 on 2008-03-28
tubasoldier:

> I've personally always had issues connecting nm-applet. Knetworkmanager has always worked better for me. I'm curious if it is just a hardware issue or something with using madwifi drivers?

I've had nothing but grief with nm-applet under Fedora 8 running KDE.  Apparently, knetworkmanager does not like the current version of Fedora 8 KDE, and is effectively broken, so they substituted nm-applet.  nm-applet is just plain and simply a royal pain.  It is slow to connect to a wireless network, and gives you precious little information about any networks around you.  For mine, for instance, it seldom showed MY network as being available for connection, but showed me instead the neighbors network (which is locked).  And I constantly have to re-key my strong password, even though the keyring applet is supposed to supply it.

Note that this is on my Dell Vostro laptop with intel wireless chipset as well as on my daughter's Dell C840 with atheros-based PCMCIA wireless card.  The atheros card uses the madwifi drivers, but I think my onboard Intel uses a native Linux Intel driver (not certain, however).

By the way, it looks like the Ubuntu install, then add the KDE stuff works much better than the KDE liveCD.  I installed the two meta packages you suggested with apt-get, then picked the KDE pieces I wanted with Synaptic.

Once I had Synaptic up, there is a metapackage in the "Metapackages" section called "KDE" that can be installed.  This is the package with ALL the KDE stuff in it, and the one you suggested I avoid.  However, it is there in Synaptic if anyone DOES want to install it.

So far I'm favorably impressed with this install.  Xandros was too conservative (and is pretty much a dead product at this point anyway), Debian etch is plenty conservative and hard to work with as you have to do so much yourself to get the system you want, and Fedora 8 is WAY too bleeding edge for my taste.  I'm hoping that Ubuntu/KDE is going to be the middle ground that I have been looking for.

Frank.

---

### Post by sstusick on 2008-04-24
Is there a list of packages that come with KDE-core?

Nevermind, I found out: 

> The following extra packages will be installed:
  kappfinder kate kcontrol kdebase kdebase-bin kdebase-data
  kdebase-kio-plugins kdelibs kdelibs-data kdelibs4c2a kdepasswd kdeprint
  kdesktop kdm kfind khelpcenter kicker klipper kmenuedit konqueror
  konqueror-nsplugins konsole kpager kpersonalizer ksmserver ksplash ksysguard
  ksysguardd ktip kwin libkonq4
Suggested packages:
  kate-plugins kde-i18n kdebase-doc-html mtools fam efax hylafax-client
  mgetty-fax menu htdig kicker-applets gij-4.1 libgcj7-awt libjessie-java
Recommended packages:
  kregexpeditor pmount libarts1-mpeglib

---


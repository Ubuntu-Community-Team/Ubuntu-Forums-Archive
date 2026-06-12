---
title: "upgrading all packages..?"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by questionasker on 2005-04-27
i just got my new comp running, but i dont have my 5.04 CDs yet, so i used the 4.10 ones to install. is there a way to completely upgrade everything and make it seem as just a regular 5.04 install? i mainly want this because ive read that KDE 3.4 is only available for 5.04, and if im gonna use KDE, i wan the latest...

and by the way, the firefox and gaim packages are a couple of versions out of date. is there a newer/better up to date repository somewhere that has the newer version, or do i just need to compile them from source??


thanks for the help.

---

### Post by Eproxus on 2005-04-28
Changing your repositories to hoary in Synaptic to hoary should do the trick.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kate /etc/apt/sources.list

See [ubuntu guide]("http://ubuntuguide.org/#extrarepositories") for more information.

---

### Post by az on 2005-04-28
Yes, it is most deffinitely possible.

sudo apt-get dist-upgrade

after having changed "warty" to "Hoary" in your sources.list.

---

### Post by Preacher on 2005-04-28
Hi folks. I am so new to Linux that I do not even qualify as a newbie :)

I have just gotten my CD for 4.1. I installed it and now I am trying to connect to the internet.
I configured my modem but she dials in and then hangs up. I cannot even get the browser to work. I am now using w**XP to connect to check my e-mails etc.

Another thing. How do I upgrade to 5.4 as I am using a 56k modem (dialup)

Any support here would be greatly appreciated.
Kind regards
Preacher

---

### Post by az on 2005-04-28
[QUOTE=Preacher]Hi folks. I am so new to Linux that I do not even qualify as a newbie :)

I have just gotten my CD for 4.1. I installed it and now I am trying to connect to the internet.
I configured my modem but she dials in and then hangs up. I cannot even get the browser to work. I am now using w**XP to connect to check my e-mails etc.

Another thing. How do I upgrade to 5.4 as I am using a 56k modem (dialup)

Any support here would be greatly appreciated.
Kind regards
Preacher[/QUOTE]

Welcome.

Please start a new thread concerning your modem issues.  As for upgrading, you can use a Hoary cd to upgrade.  Downloading something like 500 megs of packages can take a few days over modem.

---

### Post by questionasker on 2005-04-28
[QUOTE=azz]Yes, it is most deffinitely possible.

sudo apt-get dist-upgrade

after having changed "warty" to "Hoary" in your sources.list.[/QUOTE]
 that did the trick, thanks alot. now i get the little 5.04 splash page when i start firefox...

---

### Post by new2lnx on 2005-05-06
[QUOTE=azz]Welcome.

Please start a new thread concerning your modem issues.  As for upgrading, you can use a Hoary cd to upgrade.  Downloading something like 500 megs of packages can take a few days over modem.[/QUOTE]

The PC I wanted to upgrade to Hoary is not connected to the web, so I tried to do it via a Hoary cd.   But I got stuck in the process of upgrading.

First I did apt-cdrom add -d /mnt/cdrom.
Then within Synaptic I pressed the button with Mark All for Upgrade or something like that.  Synaptic identified the packages to be removed, to be updated, and to be added.  Next, I pressed the Apply button, but then a dialogue box appeared that asked me to insert the disk labeled Ubuntu 5.04_Hoary Hedgehog_-Release i386 (20050407) in drive /cdrom/.  This is where I got stuck.  No matter how many times I did eject-insert the dialogue box won't go away.

I tried apt-get upgrade but then I also got stuck with a similar message.

Where did I go wrong?  Please help.

---


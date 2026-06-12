---
title: "installing dapper 606"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by unisol on 2006-06-28
i am getting nowhere with installing dapper i did a server install and then tried sudo-apt install x-window-system-core gdm ubuntu-desktop but i get an error message saying E: Sub-process /usr/bin/dpkg returned an error code(1) i about at my wits end with dapper i dont want to give up on it but i am getting nowhere

---

### Post by aysiu on 2006-06-28
What happens if you do ```
sudo apt-get -f install
```?

---

### Post by az on 2006-06-28
Try logging in and running

sudo apt-get -f install

it sounds like you have some broken packages that did not finish installing.


If that doesn't work, are you sure the install happened without any other errors?

You are not supposed to get that error.

Also, what repositories are you using?

---

### Post by epicadop on 2006-06-28
I did as follows, and work for me in a notebook:

1) Install a Server Distro.
2) Change the /etc/apt/source.list to    [http://de](http://de).
3) Type sudo apt-get install ubuntu-desktop
4) Wait for 1 1/2 hour.
5) Volia...

---

### Post by aysiu on 2006-06-28
[QUOTE=epicadop]2) Change the /etc/apt/source.list to    [http://de](http://de).
[/QUOTE] You live in Costa Rica but use German repositories...?

---

### Post by unisol on 2006-06-28
[QUOTE=azz]Try logging in and running

sudo apt-get -f install

it sounds like you have some broken packages that did not finish installing.


If that doesn't work, are you sure the install happened without any other errors?

You are not supposed to get that error.

Also, what repositories are you using?[/QUOTE]
im only using the cdrom as of now

---

### Post by epicadop on 2006-06-28
U know...

I found some differences between mirrors, beleive it or not....

incredibly i said.

I update a computer with repositories in gb,   and can't start the X server.

Change to the de,   and works fine.    (have to reinstall...)

I don't know why.

---

### Post by az on 2006-06-28
[QUOTE=epicadop]
I update a computer with repositories in gb,   and can't start the X server.

Change to the de,   and works fine.    (have to reinstall...)

I don't know why.[/QUOTE]
It may be that the binaries for a new kernel were uploaded to the repos before the corresponding linux-restricted-modules package finished compiling.  This has been known to happen.

Probably had you waited a little longer and updated from the original repositories, you would have gotten the missing packages and not borked your X server.

---

### Post by unisol on 2006-06-28
well i did what younsaid now i get a message failed to open /varlib/dpkg status read-only file system so i remount drive then when i try sudo apt-get -f install i have to reconfigure dpkg then i try install -f and i get sub-process returned an error code (2) what now im lost

---

### Post by unisol on 2006-06-28
well i finally got xserver to load however when gnome loads im told that the human theme is broken no icons or menus yet

---

### Post by az on 2006-06-28
Your system seems borked.  Can you just start off fresh again?

You are getting too many different kinds of errors.

---

### Post by unisol on 2006-06-29
good idea ill  doit when im off yesterday i had xserver running when i rebooted fsck came up and said my file system was corrupt so it deleted some inodes and next thing i know xserver is gone. amyway i have a p3 384mb mem, 250gighd nvidiafx5500 hda1 winxp(86g) hda2 extended partition hde6=root(30g), hde5 swap 1G when i try to install with the livecd it crashes about 70% thru when i use the alternate install cd it crashes a selecting and installing software 30% so i do a server install and try to build it up from there but it doesnt always work any thanks much for your help ill get to it as soon as time allows

---

### Post by unisol on 2006-07-01
azz i tested the harddrive with maxtor's powermax 4.2 and it said 5the drive was fine does the software check just the windows partition or the whole drive

---

### Post by unisol on 2006-07-03
im off today and i will try to do a fresh install i really miss having ubuntu as it is a awsome os do you think they released it too soon

---

### Post by Skeptik on 2006-07-03
If all the negative comments are to go by, they gave this release :rolleyes: to a beginner.

---

### Post by unisol on 2006-07-04
thanks for your most helpful answer

---

### Post by jsimmons on 2006-07-04
I've been waiting for four days for some help.  The level of support here has dropped to almost nothing.

---

### Post by houstonbofh on 2006-07-04
[QUOTE=jsimmons]I've been waiting for four days for some help.  The level of support here has dropped to almost nothing.[/QUOTE]
Not really.  It is just the level of demand has grown!  I try when I get on, but I don't get on 3 times a day, so I will miss stuff.  Reply to your thread with things you are trying to keep interest up, and to bump it.  Also, help all the new users you can with what you have discovered so far.  That is the only way we will get more help helping... :D

---

### Post by aysiu on 2006-07-04
[QUOTE=jsimmons]I've been waiting for four days for some help.  The level of support here has dropped to almost nothing.[/QUOTE]
First of all, four days is not the norm, but it can happen.

Sometimes if your post is on an obscure topic, has a misleading subject title, or is posted at the wrong time of day, it can be easily missed.

We're all volunteers here--other users. The amount of help you get is the help you get.

---

### Post by unisol on 2006-07-06
well i finally received my cds from conical today i did a fresh install 5 times (p3,384mb mem 250 gighd hda1 win xp 86gb, hde6 root ubuntu 30gb, 1gb swap hde5, nvidia fx 5500) i used the alternate cd twice no luck itried the server install then tried to install ubuntu-desktop which failed i dont know what else to try

---

### Post by unisol on 2006-08-05
i finally found the problem i have an old p3 750 384 mb the problem was the ultra-ata hd 250gig was not working in my system it let me install windows xp but not dapper so i put the old 20 gig back in and dapper installed without a hitch so i guess its out to find a 100gig hd pci-ide or eide thanks everybody for your help and support. iwent out and bought a 80gb pci-ide hd (5400rpm)and installed winxp and ubuntu with no problem.i  think the 250gb hd (ultra-ata caused a hardware incompatibility with linux, but not with windows. anyway i use ubuntu most of the time now. again thanks for all your help

---


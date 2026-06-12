---
title: "Update???"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by ZuruxKakyn on 2008-03-10
in gutsy gibbon, update is already part of the installation.

i remember last time after i set up ubuntu, get my connection established, then only i update.

now, since update is part of installation and my modem is usb dial up modem, i can't update during installation.

after installation and setting up my connection, i can't seem to find update manager.

also, i used 
```

sudo apt-get update
```
 
and i get
```

Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US

```

please help me, i need to keep my machine updated.

any help is appreciated.

thanks in advanced

---

### Post by Oldsoldier2003 on 2008-03-10
> **ZuruxKakyn said:**
> in gutsy gibbon, update is already part of the installation.

i remember last time after i set up ubuntu, get my connection established, then only i update.

now, since update is part of installation and my modem is usb dial up modem, i can't update during installation.

after installation and setting up my connection, i can't seem to find update manager.

also, i used 
```

sudo apt-get update
```
 
and i get
```

Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US

```

please help me, i need to keep my machine updated.

any help is appreciated.

thanks in advanced

system>Administration>Software Sources
make sure the first 4 boxes are selected and then select the download server.
then you can go into synaptic and update it or do:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ZuruxKakyn on 2008-03-10
what if i'm using kubuntu?

sorry not not stating well

---

### Post by Oldsoldier2003 on 2008-03-10
> **ZuruxKakyn said:**
> what if i'm using kubuntu?

sorry not not stating well

you should be able to do the same thing in whatever package manager is installed in Kubuntu.

---

### Post by ZuruxKakyn on 2008-03-10
i mean the  alternative for

system>Administration>Software Sources

---

### Post by zvacet on 2008-03-10
I don´t use Kubuntu but I supose you will find answer in Adept.Second option is 

```
kdesu kate /etc/apt/sources.list
```

and remove # sign from all lines start with **deb**.

Save and close.

```
sudo apt-get update && sudo apt-get upgrade
```

Or you can use this list 

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by ZuruxKakyn on 2008-03-25
sorry for late reply.

well thanks, it helps :)

here comes another problem i'm facing:

i can't connect to the net via konqueror and kopete (browsing and chatting software for kubuntu), i can only access the net via firefox.

another question i would like to ask is about GRUB.

i notice that if i install kubuntu after windows, everything's fine.but if i'm gonna install windows after kubuntu, i'll boot into windows without having a choice to boot kubuntu.

* i ask this question because i wanna reinstall my windows without affecting my kubuntu

---

### Post by Het Irv on 2008-03-25
2. You will have to restore GRUB to your MBR, when you install windows it overwrites GRUB. 

Steps:
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---


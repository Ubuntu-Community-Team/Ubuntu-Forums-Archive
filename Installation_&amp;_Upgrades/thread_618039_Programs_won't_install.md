---
title: "Programs won't install"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Felin_Greenleaf on 2007-11-20
I've tried the Synaptic installer, and the apt-get for XMMS, Firefox can't even get plugins installed.

When I installed Gutsy I was unable to get internet and it said something about not being able to get security updates.

Also, here's what was said when I tried to terminal install XMMS.
> 
felin@Fenix:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmms


---

### Post by MrFSL on 2007-11-20
Do you currently have internet?

Can you ping something?```
ping www.google.com
```

What is the output of:
```
sudo apt-get update
```

---

### Post by Felin_Greenleaf on 2007-11-20
> felin@Fenix:~$ sudo apt-get update
[sudo] password for felin:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


And yes, Google pings.

---

### Post by MrFSL on 2007-11-20
> was unable to get internet and it said something about not being able to get security updates.

It looks like you aren't getting security updates because you only have the installation cdrom as a source. Software sources (or repositories) can be added by going to:

System > Administration > Software Sources

You can then navigate through the tabs selecting the updates and sources you want. You can then fetch updates (like security updates for instance) by typing in a terminal:
```
sudo apt-get update
sudo apt-get upgrade

```

Other then that it seems that you have all your network settings working and dns resolving etc. Is it just firefox that has problems loading web pages?

---

### Post by Felin_Greenleaf on 2007-11-20
Oooh, thank you. ^_^

It's not that it's not loading things, it's that it won't install things like Flash.

---

### Post by MrFSL on 2007-11-20
It is quite possible that the packages that you want to install are not located on the cdrom. You will have to add additional repositories.

For instance to install flash you probably have to enable the multiverse repo.

Then you can bring your computer up to date from the terminal using:
```
sudo apt-get update
sudo apt-get upgrade
```

Then you can install flash using:
```
sudo apt-get install flashplugin-nonfree
```

If this doesn't work then please post your output.

---

### Post by Felin_Greenleaf on 2007-11-20
xD The upgrade is taking years to finish, but when it's done I'll post it.

---

### Post by Felin_Greenleaf on 2007-11-20
Thanks everyone! It works now.

One last question, hos do I go about setting VLC Player as my default Video player and XMMS as my defaul music player?

---

### Post by firefoxdl on 2007-11-20
ping [www.msn.com](www.msn.com) -t

---

### Post by MrFSL on 2007-11-21
> One last question, hos do I go about setting VLC Player as my default Video player and XMMS as my defaul music player?

It would be good to search for this answer first. Then if you can't find it, then start another thread related to that particular problem.

---

### Post by gnurunam1986 on 2007-11-23
I've tried the Synaptic installer, and the apt-get for vlc,
When I installed Gutsy I was unable to get internet and it said something about not being able to get security updates.

Here's what was said when I tried to terminal install vlc

Could not mark all packages for installation or upgrade
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

can anybody help me... i am a newbie...and my english is not so good...so i copy what felin wrote...sorry...please help me

---


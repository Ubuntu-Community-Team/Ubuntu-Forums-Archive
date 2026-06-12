---
title: "Upgraded to 11.10 from 11.04 and system hangs during Boot"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by unc0nn3ct3d on 2011-10-18
I've been trying to figure this out all day and I'm not finding anything anywhere.

The boot sequence goes dandy, hard drive is working away and then as soon as it gets done Checking battery state and goes to Stopping System V runlevel compatability the hard drive activity stops immediately.  Nothing happens after that.  It will sit there for around 60 seconds and then go to Stopping read required files in advance and sits there for minutes on end.


I've checked all the logs I could get my hands on and nothing is showing up in there.

I can alt-f1 into another tty and when I do the hung boot screen goes on to Starting NetBIOS name server, then does a starting/stopping Mount network filesystems and hands there

Can anyone point me in a direction where I can start troubleshooting this? My system is bunkiss until then.

---

### Post by 23dornot23d on 2011-10-18
Check the list below ..... in the upgrade failures ..... look for solved the error you have
has been reported before .... there may already be a solution for it ....

---

### Post by unc0nn3ct3d on 2011-10-18
thanks for the links man, that's impressive an amazing that you've gone to the trouble of organizing them like that.  there wasn't a fix in any of them but one of them led me to the idea of trying to run

sudo service gdm start and wouldn't you know it gnome started up.. now i have to figure out why it isn't started in the boot sequence

---

### Post by 23dornot23d on 2011-10-18
Ok good to see you found some help there ..... you could try lightdm if gdm is giving you trouble

---

### Post by unc0nn3ct3d on 2011-10-18
I've given up on getting gdm to work properly and just reconfigured xorg to load lightdm instead of GDM and it no longer hangs during boot.

I chronicled my journey through this first stage of the hellish 11.10 upgrade here: [http://blog.netflowdevelopments.com/2011/10/18/ubuntu-11-10-upgrade-hell-part-1-boot-hangs/](http://blog.netflowdevelopments.com/2011/10/18/ubuntu-11-10-upgrade-hell-part-1-boot-hangs/)

---

### Post by 23dornot23d on 2011-10-18
I use kdm - but it adds loads of packages ..... not too bad if you run kde-full as well

These are all the kde packages .. but its quite good a bit heavy on resources though.

---

### Post by unc0nn3ct3d on 2011-10-23
> **23dornot23d said:**
> I use kdm - but it adds loads of packages ..... not too bad if you run kde-full as well

These are all the kde packages .. but its quite good a bit heavy on resources though.

One of the first things I did when switching to linux from windows many eons ago was to test out both gnome and KDE before making my choice and I quickly settled on gnome after the filthy windows-esque feel of KDE popped up on my screen :)  But now ubuntu is trying to jam this unity stuff down our throats and alas I fear I'll be moving off to debian for the same reason I chose gnome over KDE.  If I wanted a windows experience(either aesthetically or fundemantally in the sense that someone else is dictating how I am supposed to use my OS) then I'd use windows.

---


---
title: "vmware dependencies issues"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by blu.gecko on 2005-05-16
I am trying to install vmware to run a 2000 pro and some childern games for my daughter I installed libgtk1.2 and libgtk1.2 common and now my graphical interface to login is gone, what command do I run to log into my graphical?

---

### Post by codejunkie on 2005-05-16
if it boots up in console mode only no gui you could use startx and see if this works it should start the gui if it doesn't those packages might have broken the xserver if this is the case do sudo apt-get install ubuntu-desktop this should repair the xserver problems hope this helps keep me posted on your results.

---

### Post by mkg on 2005-05-17
[QUOTE=blu.gecko]I am trying to install vmware to run a 2000 pro and some childern games for my daughter I installed libgtk1.2 and libgtk1.2 common and now my graphical interface to login is gone, what command do I run to log into my graphical?[/QUOTE]

I do not offer help, but I need an answer how to install vmware on my Kubuntu 5.04. Please if you have time to explain how to do that, starting from adding repositories etc. it would be great. Thank you in advance. :grin:

---

### Post by mrbass on 2005-05-17
Install VMWare 5.0

uname -a
Linux hostname 2.6.10-5-386

sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc

Now your ready to install VMWare with the script

---

### Post by mkg on 2005-05-18
[QUOTE=mrbass]Install VMWare 5.0

uname -a
Linux hostname 2.6.10-5-386

sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc

Now your ready to install VMWare with the script[/QUOTE]

Thank you for your support. I'll try right now.  \\:D/

---

### Post by mkg on 2005-05-18
[QUOTE=mkg]Thank you for your support. I'll try right now.  \\:D/[/QUOTE]

It start, but it would be nice someone to make some installer for this. It would be very easy to isntall it :-P

---

### Post by SNo0py on 2005-05-18
[QUOTE=mkg]It start, but it would be nice someone to make some installer for this. It would be very easy to isntall it :-P[/QUOTE]
It is easy - everything is described on the Ubuntu-Homepage and on the vmware-homepage... so there is no need for a graphical installer, that does only work with Gnome but not with KDE and only if the library XYZ is installed.... This Perl-Script is fine.

---

### Post by mkg on 2005-05-19
[QUOTE=SNo0py]It is easy - everything is described on the Ubuntu-Homepage and on the vmware-homepage... so there is no need for a graphical installer, that does only work with Gnome but not with KDE and only if the library XYZ is installed.... This Perl-Script is fine.[/QUOTE]

It works. I managed to install vmware and win98 in it, but still think that graphical installer ... probably I'll use to it.

 :-P

---


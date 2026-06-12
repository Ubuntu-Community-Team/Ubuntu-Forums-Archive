---
title: "Wpa problems"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by crash75uk on 2005-04-02
Hi all,
Just installed Hoary and come across my first major stumbling block.  I have a wireless network that uses wpa encrypton.   I'm really stuck trying to install the wpa supplicant stuff, i've gone through 2 support docments neither of which work....

I tried using this guide "http://www.ubuntulinux.org/wiki/WPAHowto" but can't get past the 1st line:

$sudo apt-get install wpasupplicant  

as it errors, saying it staating that it can't find the repository

Not entirely sure what the repository stuff is but get the impression its an online collection of stuff..   Which if it is, is absolutely no use as am trying to configure my wireless card so i can get the bloody internet.

Have got another version of the guice which includes the comand

$sudo apt-get install  gcc gmake

and amazing it can't find gmake.

Can anyone help me set this up?????

---

### Post by microsome on 2005-07-22
I have the same problem.

---

### Post by matthew on 2005-07-22
Read these threads, they should help you out. 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) 

[http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10)

---

### Post by MrCheese on 2005-07-22
Desperate times call for desperate measures........assuming you have a working Windoze system on your wi-fi rig, go to the repository sites listed in your /etc/apt/sources.list or as detailed in the ubuntu guide ([www.ubuntuguide.org](www.ubuntuguide.org)) pages and copy the files to your hdd. 

From there you can either copy the files over to your ubuntu system hdd or burn a cd. You can then add the folder/cd as an extra repository source. Again, see [www.ubuntuguide.org](www.ubuntuguide.org) for details of adding extra repositories.

As I lifeline I always install package "mc" - the Midnight Commander file manager, this allows you simply to select a .deb package to install from any readable filesystem, so even if you can't get online and you can't add the required to source to apt/Synaptic you can still install packages, albeit without taking proper care of the dependencies. Of course, Catch-22 is that you have to get mc online.......

Hope this helps.

---


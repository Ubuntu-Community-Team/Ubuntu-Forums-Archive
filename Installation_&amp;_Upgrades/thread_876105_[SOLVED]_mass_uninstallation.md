---
title: "[SOLVED] mass uninstallation"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by ChaoticMind on 2008-07-31
Hey, 

I recently installed the KDE interface for Ubuntu to check it out. It, of course, came with a lot of prerequisites which were also installed. I now want to get rid of them, but simply removing the main package that I installed (kubuntu-kde4-desktop from this rep: "http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main" as per [http://tombuntu.com/index.php/2008/07/30/install-kde-41-in-ubuntu-and-make-gtk-applications-look-good/](http://tombuntu.com/index.php/2008/07/30/install-kde-41-in-ubuntu-and-make-gtk-applications-look-good/)) doesn't uninstall all the other programs, because they were "suggested" and not really prerequisites, according to synaptic.  

Can anyone think of a way to uninstall all these kde programs that I do not want on my standard Gnome Ubuntu installation? I have all the .deb files for the programs, and if I sort them by modification date, I can isolate them. Maybe there is a way to uninstall all the deb files from the terminal? (maybe using dpkg?). Any ideas?

---

### Post by Potatoj316 on 2008-07-31
if you installed with aptitude it would automatically remove the un needed ones.  Its not removing the other ones because its not smart enough to know it does not need them anymore, aptitude is.  You can remove them with sudo aptitude remove or sudo apt-get remove then list the packages butyou have to know what they are.

There are a bunch of programs that can remove unneeded packages but I dont know what they are.

---

### Post by mattduckman on 2008-07-31
shouldn't "sudo apt-get autoremove" work?

if not, you could always try gtkorphan

---

### Post by ChaoticMind on 2008-07-31
That didn't work, I think it's because they're listed as suggested installations instead of prerequisites. I uninstalled using Synaptic, which is supposed to be smart enough I believe. 

There is a dpkg --remove command that I could use I guess, but that would only work on file at a time. Is there a way to apply it to "next possible file in a folder?"

---

### Post by Potatoj316 on 2008-07-31
synaptic is not very smart, it does what its told, thats it.  If you try to remove one package it will remove just that package.  I thought the apt-get autoremove worked though

---

### Post by ChaoticMind on 2008-07-31
Nope, it doesn't. I'm talking about programs like "konqueror", "kopete", etc...


Apparently, there is something wrong with my uninstallation, since I can still select KDE from the login screen. hmm, my problem just got more vague and probably in the wrong section, should I post it somewhere else?

---

### Post by mattduckman on 2008-07-31
weeellll

i happened to see that you could pick out all the deb files, so you could put them all into in folder, cd to it, and use "sudo dpgk -r *.deb"

that may or may not work

---

### Post by .nedberg on 2008-07-31
Have a look [here]("http://psychocats.net/ubuntu/puregnome").

```
sudo apt-get autoremove kubuntu-kde4-desktop
``` should work, or if you uninstalled kubuntu-kde4-desktop in synaptic, just issue```
sudo apt-get autoremove
```

---

### Post by ChaoticMind on 2008-08-01
thanks for the link .nedberg, but if i run this command, it would remove all the packages, and if i have some packages already installed from before, and apps already depending on those, they'll be removed without prompt. So, I'm manually filtering what needs to be removed, and i'm almost done, it's working fine but it's time consuming. 

Cheers.

---


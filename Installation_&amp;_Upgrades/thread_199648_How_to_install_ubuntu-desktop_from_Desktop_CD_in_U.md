---
title: "How to install ubuntu-desktop from Desktop CD in Ubuntu 6.06 Server?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by vlad.dumitrescu on 2006-06-19
I've downloaded both Server CD and Desktop CD of Ubuntu 6.06, but I've installed the Server Edition on my computer (it will be a web server and a router for the local network). 

How can I install ubuntu-desktop from the Desktop CD? (I'm just curious to see the desktop edition without downloading approximately 400MB or installing Ubuntu all over again and, also, I'll be more comfortable setting my firewall with firestarter :p).

I tried adding the Desktop CD to the repositories, but apt-get doesn’t find ubuntu-desktop.

Thank you and excuse me if this topic has been discussed before. I couldn't find anything.

---

### Post by ajgreeny on 2006-06-19
If you have not yet spent time configuring your computer as a server but have simply installed the server edition of Ubuntu, I think the easiest way is possibly to just start again with the desktop live CD and install the full desktop.
Alternatively, if you have the machine connected to the internet and do not want to start from the beginning, just login and then type *sudo aptitude install ubuntu-desktop*.  If you use *aptitude* instead of *apt-get* you will find it much easier to remove the ubuntu-desktop later if you need to or want to.

---

### Post by vlad.dumitrescu on 2006-06-19
Thanks for the advice about aptitude.

If I install the Desktop Edition I will install a lot of things that I don't use. I just wanted to see the desktop, set the firewall with firestarter then uninstall ubuntu-desktop.

Also aptitude starts downloading ubuntu-desktop and I have a 256 kbps internet connection, so I thought I'll save some time if I could install from Desktop CD that I've already downloaded.

---

### Post by linuchsan on 2006-06-19
It is apt-cache search ubuntu-desktop
You will get the following output:

edubuntu-desktop - edubuntu desktop system
kubuntu-desktop - Kubuntu desktop system
ubuntu-desktop - The Ubuntu desktop system
xubuntu-desktop - Xubuntu desktop system

---

### Post by vlad.dumitrescu on 2006-06-19
Yes, it is in the cache, but on the internet repositories. If i sudo aptitude install ubuntu-desktop it starts **downloading** all the packages needed.

I tried leaving only the Desktop CD in /etc/apt/sources.list and sudo aptitude install ubuntu-desktop says <<Couldn't find any packages whose name or description matched "ubuntu-desktop">>.

---

### Post by nejode on 2006-06-19
It doesen't work with the Desktop Live CD, you need the alternate Install CD.  Then you add it to the repositories through Synaptic or apt, and comment out all other repositories.  It worked for me.

---

### Post by rcarring on 2006-06-19
Thats correct. the alternate cd can be used as a repo for ubuntu-desktop. I guess the Live CD isn't that flexible.

---

### Post by vlad.dumitrescu on 2006-06-19
Thank you. I hope it will work (I'm downloading now :cool:).

---


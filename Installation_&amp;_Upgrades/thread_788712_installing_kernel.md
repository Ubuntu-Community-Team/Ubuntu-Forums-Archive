---
title: "installing kernel"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by digitalspy99 on 2008-05-10
I just started working on ubuntu because i wanted to install AODV-UU on wireless router WRT54GL... I am a beginner. Now, i got help from the site "my.opera.com/subjam/blog/show.dml/472834?cid=4808543".. I have downloaded AODV-UU now i want to install the kernel... but from my cd of ubuntu. can anybody please help me that how can i give my CDROM path in /etc/apt/sources.list so that the installation process is carried out from the same cd from which i have installed my ubuntu???
Please help me... I ll be really thankfull....

---

### Post by Partyboi2 on 2008-05-10
To add the ubuntu cd to your sources.list you can open "Software Sources" (System>Admin>Software Sources) and on the 2nd tab  press  add cdrom, making sure you have the ubuntu disk in the cdrom

You can also use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find the needed packages you need to install.

Edit: The above is for hardy. If you are using gusty open Software Sources and on the first tab tick the add cdrom under "Installable from cd-rom/dvd"

---

### Post by Jamin3D on 2008-05-10
What should I do if when clicking the link for "Software Sources" it doesn't open?  Locks up... I guess?  The black-circle cursor goes for a while, then disappears.  Other items won't open either, like the Synaptic Package Manager.  I've tried rebooting.

(8.04)

[COLOR="Blue"]edit: fixed that problem (turned out to be a hostname issue)by following the instructions here:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=783734]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=783734")[/COLOR]

---

### Post by Thanoulis on 2008-05-10
Open your /etc/apt/sources.list and add: (or something like that-depends on your version and/or architecture)
```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
```

---

### Post by zvacet on 2008-05-10
```
gksudo gedit /etc/apt/sources.list
```

remove # at the begining of line **Thanoulis** posted.Save and close file.

```
sudo apt-get update
```

This way synaptic will ask you to put CD in the drive and that is what you want.

---

### Post by digitalspy99 on 2008-05-12
Thank you so much...

---

### Post by digitalspy99 on 2008-05-16
hey guys... i hust wanted to help you regarding running any installation from cdrom.... just type...
apt-cdrom add
and the path of cd-rom will automatically be added in the sources.list file....
Thankyou all for helping....

---


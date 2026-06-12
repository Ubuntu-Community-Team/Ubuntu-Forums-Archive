---
title: "No menu coming up for new installation of Ubuntu Mate 20.04"
date: 2020-07-02
forum: Installation &amp; Upgrades
---

### Post by sighthnd2 on 2020-07-02
I recently installed Ubuntu Mate 20.04 on a second partition on my computer. I am able to login, however, none of the menuing comes up when I do so. The only applications I am able to access from the screen are the file manager, Terminal, and a web browser. Previously, it brought up a warning about some applet not being available and asking if I wanted to skip, which I eventually clicked yes to. I cannot even get at the application for selecting wireless networks, so I cannot get online in Linux.

I have attached a log of my last linux login, truncated so as to fit within the limits of what is permitted here. I have not modified any files from the default installation under /etc/X11 and I do not believe I have any dotfiles related to xsession logins (no .Xsession or the like, but I don't know the full list of files I should check for). Any help or link to a thread that discussed something related would be appreciated.

---

### Post by ActionParsnip on 2020-07-03
Open a terminal and get fully updated with
```

sudo apt update 
sudo apt -y upgrade 
sudo apt -y dist-upgrade 
sudo apt clean
sudo reboot 

```

If the system is a laptop then move it near your router to use a wired connection and get the new packages in. Should help a lot

---

### Post by sighthnd2 on 2020-07-07
I followed that procedure.

First pass I got through sudo apt -y upgrade during which it crashed and I was unable to see what it was doing and all I could do was power cycle. Second pass, I completed sudo apt -y upgrade successfully. I then tried sudo apt-y dist-upgrade to which it said that there was nothing that needed to be done and did the remaining two steps.

 It still does not bring up the menuing system. Anything else to try?

---

### Post by sighthnd2 on 2020-07-28
I tried following the instructions you gave, but it still does not bring up the menuing. Attached is the error log from my most recent attempt.

---

### Post by pbear42 on 2020-07-28
My advice would be to start over and redo the installation.  Start by confirming the [[COLOR=#ff0000]checksum [/COLOR]]("https://ubuntu-mate.org/download/amd64/focal/")of the ISO file.  Burn the ISO to flash drive, preferably using [Etcher]("https://etcher.io/") or [Rufus]("http://rufus.akeo.ie/") (do not use LinuxLive USB Creator, which was last updated five years ago).  Be sure to use a good flash drive, preferably a new one (trying to eliminate all potential sources for error). Give the live session a good test drive, opening files, accessing the internet, etc.  Then install again.  Be sure to reformat the partition.  Good luck.

---

### Post by sighthnd2 on 2020-08-14
I did a new installation, albeit with keeping non-system files. One item I did notice is that it seems to have problems when it comes to pcloud. On a prior installation, I had put it on and I use it for online storage/backup. I had not yet installed pcloud with my new setup, but I copied my old home directory, which is probably where it's getting whatever is trying to get it to launch pcloud. Does that seem like a possible issue?

---


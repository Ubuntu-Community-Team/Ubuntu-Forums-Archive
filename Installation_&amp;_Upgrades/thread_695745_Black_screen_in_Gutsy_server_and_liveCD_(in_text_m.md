---
title: "Black screen in Gutsy server and liveCD (in text mode)"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ioannis on 2008-02-13
I installed gutsy server on a dell with ATI Radeon X1300 pro but I get only a black screen. I don't even get the GRUB countdown or anything after booting starts (after the DELL graphics). The server is working because I can ssh to it very quickly after boot up. All the solutions I have found are X related, but my problem is in text mode. I also want to point out that I couldn't see anything when I booted the liveCD, until I pressed ENTER, which took me to the first text mode installation screen.
Any ideas?
Thanks!

---

### Post by zvacet on 2008-02-13
You will see grub if you press Esc button when it start to boot.You have black screen because you installed server edition wich comes without GUI.If you want to add GUI then 

```
sudo nano /etc/apt/sources.list
```

ans add this line 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

Crtl+o and Ctrl+x

```
sudo apt-get update && sudo apt-get upgrade
```

For GNOME

```
sudo apt-get install ubuntu-desktop
```

KDE

```
sudo apt-get install kubuntu-desktop
```

Xfce

```
sudo apt-get install ubuntu-desktop
```

---

### Post by ioannis on 2008-02-13
Thanks for the response. I understand that server has no GUI, and that is fine. But I get no text output either. 

For example, in another computer that I installed the same gutsy server, when I boot it up I see:

- a grub countdown for a couple of seconds that says that I have to press escape to get the grub menu
- then, a whole bunch of text lines with [ OK ] on the right hand side that shows the booting process
- when it's done booting, I get a "Ubuntu 7.10 <servername> tty1" and "<servername> login:" prompt so that I can login locally.

With the server I am having problems with, I get none of this!

Thanks for the help

---


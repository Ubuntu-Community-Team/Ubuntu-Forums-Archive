---
title: "White and Black Screen After Running Startx for Ubuntu Server 14.04.3 i386"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by Jerry_W_Hegwood_II on 2015-10-20
I have an IBM Blade Server with dual Xeon 3.0Ghz processors, 1Gb of RAM, and two 32Gb hard drives. I am pretty sure that I have a 1 dead hard drive but it doesn't effect much since this thing is intended to be a VPN server and possibly small file server. So here is my problem... I Installed Ubuntu Server 14.04.3 i386 . After the install was completed I ran the update and upgrade commands. I then installed Lubuntu so I can have a GUI as a last resort for troubleshooting a problem. I have a SSH tunnel and Webmin setup so I can run it more securely headless. So I was prompted to to install the Startx command the first time I went to use that command line. I did that but when I run Startx I get this black screen with a white box in the upper left side of the monitor. In that box it shows:

```
root@servername:~#
```

I cannot do anything once this box appears not even CTRL, ALT, DELETE. Any help is definitely much appreciated.

---

### Post by mastablasta on 2015-10-21
how did you install lubuntu? shouldn't lubuntu already install startx as well as desktop manager? is desktop manager installed and configured to run?


what is the graphics card/chip?

---

### Post by Jerry_W_Hegwood_II on 2015-10-21
> **mastablasta said:**
> how did you install lubuntu? shouldn't lubuntu already install startx as well as desktop manager? is desktop manager installed and configured to run?


what is the graphics card/chip?


I used the command line that only installed the core of Lubuntu on top of the Ubuntu server install for my GUI. I saw where some sites recommended installing LDXE first and others that didn't. When I had it running 12.04 I had it running the full Ubuntu desktop GUI. This time I didn't want the security risk. Yes I thought Startx should have been installed too. What do you mean by desktop manager? I guess I have never had to deal with that before.

The graphics card is a Planar add on card and I don't remember what it runs at. I know it ran the full desktop environment on 12.04 with no problems at all. No lag or anything. That is why I chose Lubuntu do to it saying it supported older systems. I also just installed Ubuntu Desktop on an older Dell running a Pentium 4 and I had to downgrade the GUI to the 12.04 GUI do to the on-board graphic card not being able to run the new GUI at all.

---

### Post by mastablasta on 2015-10-22
try

```
sudo service lightdm start
```

desktop manager is the thing that runs just before the desktop (the screen where you put in your username).

---

### Post by Jerry_W_Hegwood_II on 2015-10-22
> **mastablasta said:**
> try

```
sudo service lightdm start
```

desktop manager is the thing that runs just before the desktop (the screen where you put in your username).

```
lightdm: unrecognized service
```

---

### Post by Jerry_W_Hegwood_II on 2015-10-23
> **mastablasta said:**
> try

```
sudo service lightdm start
```

desktop manager is the thing that runs just before the desktop (the screen where you put in your username).

I installed the LXDE core on top of the Lubuntu and I used ```
sudo startx 
``` but it brought me to the LXDE desktop GUI.

---


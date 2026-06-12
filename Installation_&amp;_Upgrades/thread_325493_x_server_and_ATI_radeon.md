---
title: "x server and ATI radeon"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by eruheru on 2006-12-25
hey all
I've been trying to install 6.1 but am having troubles with the x-server not starting. I have researched and linked it to the lack of ATI Radeon drivers. Everytime I try something suggest to different people it doesnt work. Anyone know a remedy to this? Thanks!

---

### Post by Patrick-Ruff on 2006-12-25
system specs please?

---

### Post by eruheru on 2006-12-26
AMD Athlon 64 3800+ processor
ATI RADEAN x850 graphics card
ASUS A-8NE motherboard
1024 corsair TWINX DIMM RAM

---

### Post by Kubunteando on 2006-12-26
Can you attach the file on /var/log/Xorg.0.log

That way we can see what are the errors reported when the Xserver is started, and you may get more accurate help.

---

### Post by eruheru on 2006-12-26
> **Kubunteando said:**
> Can you attach the file on /var/log/Xorg.0.log

That way we can see what are the errors reported when the Xserver is started, and you may get more accurate help.

Its denying me access to the log file. I also tried to find the configuration 
```
/etc/x11/xorg.conf
``` but it comes back that it doesnt exist. 

just as a side note, when its booted in safe graphics mode I can hear it start up, but the monitor is blank.

Thanks!

---

### Post by Kubunteando on 2006-12-26
Try to use a recent copy of the 6.10 version. If you have an early copy there may be some issues. You can also try Kubuntu instead of Ubuntu.

---

### Post by eruheru on 2006-12-27
I tried installing Kubuntu, however when it loaded it went directly to a command screen. There was no message box about x server.

---

### Post by Kubunteando on 2006-12-28
1- What do you get if you type "startx" from the console?

2- Can you still get the /var/log/Xorg.0.log? That can give some hints.

3- Do you have now /etc/X11/xorg.conf?

---

### Post by eruheru on 2006-12-28
> **Kubunteando said:**
> 1- What do you get if you type "startx" from the console?

2- Can you still get the /var/log/Xorg.0.log? That can give some hints.

3- Do you have now /etc/X11/xorg.conf?

when I used "startx" it came up with 
 
```

Fatal server error
no server found
XI0: Fatal IO error 104 (connectionreset by peer) on x server ":0,0"
after 0 requests (0 known processed) with 0 events remaining
```

still not getting access to the "/var/log/Xorg.0.log" or " /etc/X11/xorg.conf"
hopefully that will help.
thanks!

---

### Post by Adapted.Cat on 2006-12-28
If you're having trouble getting X started, try "sudo <command>" to run commands as root, or "sudo -s" to get a root shell (enter your own password when prompted, though you can set it up with a different password later).

X windows depends on a working /etc/X11/xorg.conf - in earlier releases this had other names. A good starting configuration file should have been installed for you, but that may not have happened for you. First of all, make sure you have the server and all driver components installed:

```
apt-get update
apt-get install xserver-xorg xserver-xorg-core xserver-xorg-driver-all
```

Now if that didn't bring up a configuration menu, try this:

```
dpkg-reconfigure xserver-xorg
```

This will set up a configuration file for you. It may need some tweaking, but it should be a start. Then run "startx" to see if it brings up X windows.

Now your graphics card may cause problems. I've had endless trouble with Radeon cards on linux. If you choose the "ati" driver, you'll get a basic working environment with no 3D acceleration and, to be honest, pretty poor 2D performance. I don't think the open source drivers support acceleration on your card. If you go with the ATI binary drivers (fglrx) then - if you're lucky - you'll get accelerated 3D graphics that's still much slower than you get from Windoze but still games will be playable. Do a search for the Ubuntu fglrx HOWTO and you'll get plenty of instructions on how to get there, which may or may not work for you.

If none of this works, download the live/install CD, boot from it, and see if it brings up X windows. If that doesn't work then you it's an Ubuntu problem and you can report the bug on launchpad. If it does work then there's something terribly wrong with your installation, and you may wish to consider a fresh install or something like the following:

```
apt-get --reinstall install $(dpkg --get-selections | awk '{if ($2 == "install") print $1}')
```
That should force a reinstall of all your packages, provided you have space enough for the download!

---


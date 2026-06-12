---
title: "X-Server Failure on Boot"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by niglch on 2006-02-24
Ok, I just finished installing Ubuntu from the CD. However, now that I've resolved all of my will-not-boot-at-all issues, now I have another one. Basically what happened was I rebooted my computer and Ubuntu started up and went into a first time boot setup configuration and started installing some more packages. However, the progress bar started hanging really long on the "preparing to configure ubuntu-desktop" which usually means there is a problem :mad:. Sure enough, soon after I got a message saying, "one or more packages failed to install ... ", and another saying, "failed to start x-server ... would you like to view the x-server output to diagnose the problem?" I then got this output:
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523
root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux Komputer 2.6.12-9-386 #1 Mon Oct 10
13:14:36 BST 2005 i686
Build Date: 10 October 2005
Before reporting problems, check http://wiki.X.Org
to make sure that you have the latest version.
Module Loader persent
OS Kernel: Linux version 2.6.12-9-386 (guildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu) #1 Mon Oct 10
13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting
```
The last message I get is one saying "The X Server is now disabled. Restart GDM when it is configured correctly." Then I get into a command-prompt asking me to login.
This problem seemed very similar to the one in [this thread.]("http://ubuntuforums.org/showthread.php?t=134683")
My video card is a GeForce FX 5200 w/ 256mb ram (pci). However, this might be the source of the problem because this isn't the card that came with my PC (originally it was one of those Intel Integrated graphics ones and I added the Nvidia card later).
I tried the "sudo dpkg-reconfigure xserver-xorg" command, and it seemed to recognize the intel integrated card rather than my GeForce one because that's what appeared in that second reconfigure prompt box. Basically I'm totally confused on how to reconfigure x-server properly to get it to work!!!

AGH! I'm sick of technical diffuculties! I'm going to sleep and praying for some kind soul to end these problems when i get up. lol.

---

### Post by ssam on 2006-02-24
sounds like maybe the install did not complete.

can you run
```
sudo apt-get update
sudo apt-get upgrade
```

you may need to install cd in the drive, if you are not connected to the internet.

---


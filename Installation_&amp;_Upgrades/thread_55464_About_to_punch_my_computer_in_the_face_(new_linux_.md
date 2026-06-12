---
title: "About to punch my computer in the face (new linux user)"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by Dizzle84 on 2005-08-09
Okay, so I've had a fair amount of success installing ubuntu and getting all the packages I need to go with it like Flash, Macromedia, etc... but I can't for the life of me get my USB to read my digital camera's USB reader.  My camera is an OLYMPUS STYLUS and I am using the Olympus CAMEDIA USB reader/writer MAUSB-10.  When I place my memory card in there, the green light comes on but nothing flashes on Gnome (err my desktop) and I don't get a verification sound telling me that the computer recognizes the reader.

I was told to enable the universe respitories... but the problem there is that I don't know how to that either  ](*,)   Yeah, I am a complete noob here.  Ubuntu is my first linux experience, and the reason why I chose it, was because I could no longer stand Windows and all the spyware and insecurities.


Any help would be much very appreciated.  And for the record, I did use google to look around to see what I could do.  That's actually how I came about this site.  I searched and searched this site to see if anyone else had the same problem as me, but I couldn't find it... so I registered and created this thread.


Thanks to anyone who helps this new guy out  \\:D/

---

### Post by Rule on 2005-08-09
to enable the "universe respitorie" in the terminal type in "sudo gedit /etc/apt/sources.list" and uncomment (remove #) deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

---

### Post by Dizzle84 on 2005-08-09
Ok.  So I attempted to do that, and this is the message I get now..  Oi, :|  :| 



W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Lord Illidan on 2005-08-09
Number 1.

What computer do you have? 64 bit AMD? Or is it an Intel Pentium 2, 3, 4?

Number 2.

Check out the ubuntu guide : [www.ubuntuguide.org](http://www.ubuntuguide.org)

Number 3.

After you have done the repositories, you have to enter in the terminal

```
sudo apt-get update
``` 

Number 4.

If you want your system to be more automated, maybe I could recommend Kubuntu..

---

### Post by wellery on 2005-08-09
You could also try using gThumb to import the photos. That may work. I have a camera that I must use gThumb to import it.

---

### Post by Dizzle84 on 2005-08-09
Okay.  So I did the command "lsusb" in the command terminal and got the following:

Bus 002 Device 002: ID 077b:08b8 Linksys
Bus 002 Device 001: ID 0000:0000
**Bus 001 Device 003: ID 07b4:010a Olympus Optical Co., Ltd**
Bus 001 Device 001: ID 0000:0000


I made bold the thing I've been trying to get working.  Any ideas on how one would be able to reach it?




Ps.  Thanks for everyone's help this far.. been a great help
PPs.  I even tried Kubuntu but when installing the packages, it didn't give me a description, so it was like installing them blindly. :-|

---

### Post by WillFull on 2006-11-05
Been over a year since this thread was active, I know, but I was hoping to find out if anyone has been able to find a solution for this.  There are two threads (including this one) that mentions lack of support for the MAUSB-10, which I find odd, because according to the project webpage on SourceForge, the author stated that the MAUSB-10 driver (aka Alauda) was to be merged into the Linux kernel (v2.6.16) -- Kubuntu 6.10 has a newer version, so I was assuming that support would already be included?  Maybe not.  How would I find this out?!?!??!

thanks in advance.

---


---
title: "Gutsy Install halts at Scanning Mirror"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by CaesarLike on 2007-10-31
HI All,

I am trying to install 7.10 (freshinstall), but the process simply stops a the Scanning Mirror stage.  It has frozen 4 times now at this point.  anyone know how to fix it?

---

### Post by brdavs on 2007-10-31
I have exactly the same problem

---

### Post by BlueSkyNIS on 2007-10-31
I had exactly the same problem, but to install it I have had to unplug the ethernet cable. So the solution is to temporary disable internet during install. Install process my ask some questions about internet settings, but just use defaults. You can install internet connection once the system is set up. :)

Sorry for my english :(

---

### Post by BlueSkyNIS on 2007-10-31
I think the problem is in local servers for Ubuntu update (not sure). 
After the system was set up I had to set: "Download from: Main server" in System -> Administration -> Software Sources.

Picture attached. :)

---

### Post by brdavs on 2007-10-31
I installed the desktop version in the end (instead of server, which was always stalling at "Scanning Mirror" point) and that was successful. But, I had to do it  twice  because of problems with Grub (initially I did not know, that hda5 translates to hd(0,4) in "Grub language"). Now the system is working except for the "Out of range" message on the CRT monitor, which is displayed after the boot, before I get to the GUI login prompt. Ugh, it was so much easier with Mepis.....

---

### Post by CaesarLike on 2007-10-31
Hi BlueSkyNIS,

You were right, when I unplugged the internet cable Ubuntu installed no problem.
I think where the problem may be is that the installation may be trying to download from the Ubuntu Main Server.  After installing Ubuntu, and resetting the software sources to Main Server, I was unable to download any updates, as the server was very slow.  The download rate was measured in bits, not even Kbs.  If this is what is happening during the installation, then it explains why the install stops at the scanning mirror process, as it either cannot connect to the server, or the server is so slow it could take hours for the data to be downloaded.  When I set the software sources to my local country, the updates (16 Megs) came down in less than a minute.

---

### Post by walshtj on 2008-03-05
Same problem. 
I was installing Gutsy in VirtualBox on an XP host. 
However if you wait for something like 10-15 mins it eventually gives up and continues the installation.

---


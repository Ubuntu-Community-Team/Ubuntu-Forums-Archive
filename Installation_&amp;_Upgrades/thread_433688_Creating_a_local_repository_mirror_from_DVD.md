---
title: "Creating a local repository mirror from DVD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by ranarion on 2007-05-05
Hello everyone,

I'm trying to set up a local mirror of the Ubuntu repositories for use on a LAN. I'd like to save myself (and the Ubuntu servers ;-)) the large download and use an installation DVD that I already have here as the basis for my mirror. However, all apt-mirror guides out there are based on downloading everything -- can I simply copy the DVDs file structure to my harddisk? Or should I give apt-mirror the path to the DVD as a package source?

Many thanks in advance!

---

### Post by aysiu on 2007-05-05
Read [this post](http://ubuntuforums.org/showpost.php?p=2595774&postcount=2).

---

### Post by ranarion on 2007-05-05
Hm, using a loop device is a nice and unusual idea, but wouldn't I be cut off from all updates? As far as I understand this, apt-mirror will create the local repository once and is then able to keep it synchronized with any changes going on upstream.

---

### Post by aysiu on 2007-05-05
I'm sorry... so what would be the benefit then of having a local repository as opposed to using the online one?

---

### Post by ranarion on 2007-05-05
No need to apologize, I'll gladly keep your idea in the back of my head for other installations :-)

The system I'm currently installing serves a LAN in a remote location where higher bandwith connections are not available, so I'd like to pack as much as possible on the server. This, I hope, will greatly reduce online costs.

Well, and I can't take the machine to my place and "fill it up" here because I pay my broadband connection by data volume...

EDIT: Right after I posted this, I (probably) found a solution: apt-proxy is a caching proxy that is designed for serving debs to several machines in a LAN, and its cache can be filled with packets from local drives.

---

### Post by jdeisenberg on 2007-07-28
I would like to do this exact same thing. I copied the DVDs to my server, but I get authentication errors, as I don't have the Release and Release.gpg files.

Are there any instructions on how to create these? This: [https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto) comes close, but doesn't seem to be what I need.

---

### Post by BobSongs on 2007-09-16
[FONT="Verdana"]You can check out my tutorial on [repositories]("http://ubuntuforums.org/showthread.php?t=352460"). I cover most bases. Hope it helps.[/FONT]

---


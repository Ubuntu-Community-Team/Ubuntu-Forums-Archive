---
title: "Openoffice via NFS: always write protected"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by KursKu on 2007-05-03
I recently upgraded my Desktop and my Laptop to Feisty Fawn (7.04) from 6.06. Since then I have a strange Problem:
Using OpenOffice 2.2.0, I'm not able to save files directly to my NFS shares! When I open files from my NFS share, they are always write protected.
This is really anoying, I didn't change anything on my server, which is running Debian Sarge by the way. 

What went wrong here in this Ubuntu release? Any hint how to solve this?

By the way, other applications such as AbiWord don't have this problem, I can save, open, edit asf.

Thank you

---

### Post by KursKu on 2007-05-08
Okay Folks, I solved the problem. The solution was to install nfs-common, which is not installed by default.

Still some problems might occur, but in general, save works now on NFS shares.

---

### Post by Mr_Arne on 2007-05-16
Hi, I'm just struggling with the same problem, the difference in my situation is that I'm trying to save edited OO-files to a maxtor NAS, on which I have activated NFS. I wonder if you mean that nfs-common is to be installed on client or server, might be a silly question but... I ask it anyway!! :D
Edit: I just checked my status regarding NFS on client; ...nfs-common is already the latest version...
It seems that I have a similar - but different - problem.

---

### Post by hg42 on 2007-12-14
I recently learned that getting only write protected access via nfs may be caused by having an unknown option in /etc/exports

In my case it was the "nohide" option, which isn't known by nfs-user-server.
 I used unfs3 before and had tested some options when switching the nfs server.

Such an error is logged in the logs, but I didn't look there, because I had read access...so I looked at other places  first.

Perhaps this helps...

---

### Post by Mr_Arne on 2007-12-14
Hi,
This was quite a time ago, I found a solution here:
[https://bugs.launchpad.net/bugs/40537](https://bugs.launchpad.net/bugs/40537)
According to this bug and its solution you could interprete it as an OO bug, but after a quick brief and some reflection over hg42's post this might be a better, more sustainable and more correct solution. I might be able to test it some day. The most annoying point with the solution in the bug report is that one must repeat the action after every OO upgrade...
I might come back about this some day, dunno when though :)

/ola

---


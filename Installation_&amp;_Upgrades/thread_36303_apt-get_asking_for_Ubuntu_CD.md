---
title: "apt-get asking for Ubuntu CD?"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by veraction on 2005-05-22
Ok, I just did a fresh install of Ubuntu 5.04 the other day on my second box. I've had Ubuntu 5.04 on my main box for a while now.

Anyways, on this new installation, when I try to apt-get install anything, It prompts me to insert my Ubuntu CD. When I do this, it works fine, but I'm just wondering why I need to do it. I must've messed up the install since my other Ubuntu computer doesn't do this.

Any Ideas?

P.S. ```
sudo apt-get install samba
``` is freakin annoying. I hate working out dependencies

---

### Post by Sam on 2005-05-22
Comment out the first line of /etc/apt/sources.list and apt-get will find the packages on the web repositories.

---

### Post by veraction on 2005-05-22
Ok, I just uncommented the two lines from that file, but it still asks for CD. Do I need to reload something before I apt-get install again?

[edit] I don't understand why two duplicate installs of Ubuntu have different behaviors. Cause both were installed from the same CS -- unless I messed up some option someplace

---

### Post by Sam on 2005-05-22
[QUOTE=veraction]Ok, I just uncommented the two lines from that file, but it still asks for CD. Do I need to reload something before I apt-get install again?

[edit] I don't understand why two duplicate installs of Ubuntu have different behaviors. Cause both were installed from the same CS -- unless I messed up some option someplace[/QUOTE]
Use```
$ sudo apt-get update
```to apply the changes.

---

### Post by veraction on 2005-05-22
well, I already did the update thing, but it still asks for the CDs.

Anyways, I think I'm just gonna reformat that computer. It's always been acting strangely. Now its logging me out randomly for no reason.

---

### Post by jeremy on 2005-05-23
Are you sure that you commented oput the correct lie? It's the one that begins with deb cdrom...

---

### Post by mrtaber on 2005-05-23
Make sure you *commented out* the line mentioning "cdrom."  That should take care of it whining for the CD.

Mark :)

---

### Post by hantms on 2005-05-23
[QUOTE=jeremy]Are you sure that you commented oput the correct lie? It's the one that begins with deb cdrom...[/QUOTE]
 Thanks, that worked for me.. Strange, because it never asked for a CDROM before, but suddenly started. (Been trying to install LimeWire..)  (Which doesn't work, then I thought maybe should get Sun's Java, but installin that didn't work either..  (but I'll start a separate post on that)

---


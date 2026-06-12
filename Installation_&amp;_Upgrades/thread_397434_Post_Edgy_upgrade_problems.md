---
title: "Post Edgy upgrade problems"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by mac71 on 2007-03-30
Hi guys. I seem to have a problem. Against judgment and advice, I upgraded to Edgy yesterday. since then, whenever i go for an upgrade i get this script in the terminal:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up and (1.2.2-1.1) ...
Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
dpkg: error processing and (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 and
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on how to resolve this would be greatly accepted.

---

### Post by mac71 on 2007-03-30
Hi, its me again :(  
I've just found that i also get this in synaptic when i install or remove packages:

E: and: subprocess post-installation script returned error exit status 1

I have no idea how to resolve these issues. Any help will be greatly appreciated.

---

### Post by zvacet on 2007-03-31
**synaptic>edit>fix broken packages**

---

### Post by mac71 on 2007-03-31
Hi, tried that - it took about 2 seconds (dunno if thats about right, or not). I still have the same problems. :confused: 
 Any other ideas, or are my only options to live with it, or do a fresh install?

---

### Post by rsambuca on 2007-03-31
What method did you use to upgrade?  From Dapper I presume?

---

### Post by mac71 on 2007-03-31
Hi, I used:

gksu "update-manager -c"

---

### Post by rsambuca on 2007-03-31
Sorry, I don't know how to help you with this one.

---

### Post by mac71 on 2007-03-31
Yeah, its a bit of a head scratcher. Thanks for your help anyway.

---

### Post by LukeCarrier on 2007-04-01
Hi there,
I have also had problems since upgrading from Dapper to Edgy. I have lost the ability to scan for and connect to wireless networks, I have recently posted about this elsewhere, no replies :( .
Because of that I don't know of any problems with the package manager, I've bought an ethernet cable and I'll post back here on whether I have the problem or not as soon as I'm connected to the net again.
Best of luck,
Luke.

---

### Post by mac71 on 2007-04-02
Thanks Luke, I've now taken the step of backing up all my important stuff and going for a re-install:( . Now back to good ol' dapper :) . All's working well, just need to modify and update things to my liking.

Thaks to all for their input.

---


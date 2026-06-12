---
title: "Apt-get install problem"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by fnando on 2005-07-17
I'm trying to use apt-get to install some programs (mplayer, ...) but I'm receiving the following message:

> Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occured while processing apache2-mpm-prefork (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

No matter what package I try to install receive the same message!!! Any ideas?

**UPDATE:** I tried using the Synaptic and I receive this message when opening it!!!

---

### Post by dave9191 on 2005-07-17
Apt-get broke somehow (and since synaptic is just a front end to apt-get it will have the same errors). 

Try 

sudo apt-get -f

to get apt-get to fix itself.

Dave

---

### Post by fnando on 2005-07-17
[QUOTE=dave9191]Try 

sudo apt-get -f

to get apt-get to fix itself.[/QUOTE]

Dave... this command is showing the apt-get help... I think I need to pass some other parameter... Can you help me?

---

### Post by dave9191 on 2005-07-17
oh, my mistake, havent done this is a while, try

sudo apt-get -f check

Dave

---

### Post by fnando on 2005-07-17
Great! Is working now!!! Thanx Dave!

---

### Post by dave9191 on 2005-07-17
Cool :) no probs. 

Dave

---


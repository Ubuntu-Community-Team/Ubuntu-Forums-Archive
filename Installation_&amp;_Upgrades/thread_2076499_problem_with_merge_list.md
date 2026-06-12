---
title: "problem with merge list::::"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2012-10-26
Hi, this whole issue started when I was trying to update with an intermittent wifi connection. I got a bug report and the following:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I reported the issue and cut and pasted the above to Launchpad. But there hasn't been any movement on the issue, from what I can tell. 

Is there some way i can fix the problem myself, or, that failing, is it possible to do a reinstall  without losing any data/ presently installed applications? (I'm asking because I'm traveling and don't have my backup drive)

thanks

---

### Post by dino99 on 2012-10-26
simply delete the borked package list inside /var/lib/apt/lists/...

---

### Post by arnicainthemembrane on 2012-10-26
delete the borked package list? what does that mean? and how do i do it? thanks!

---

### Post by grahammechanical on 2012-10-26
Open a terminal and run these two commands.

```
sudo rm /var/lib/apt/lists/* -rf
```

That command removes/deletes all the scripts in the lists folder. This command replaces them.

```
sudo apt-get update
```

That is what worked for me when I had this problem. Actually this is the only script that has the problem:

> archive.ubuntu.com_ubuntu_dists_precise_restricted _binary-i386_Packages

So just removing that would work just as well.

Regards.

---

### Post by arnicainthemembrane on 2012-10-26
brilliant. thank you.

---


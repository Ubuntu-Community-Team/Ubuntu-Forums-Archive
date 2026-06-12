---
title: "Disk space highly similar 32-bit &amp; 64-bit versions"
date: 2017-06-19
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2017-06-19
I am installing Kubuntu 14.04 on a 64-bit machine.  For the last few years, I have been using Kubuntu 14.04 32-bit on another PC.  The two systems are 95% identical in software packages installed.

For the 64-bit installation, I started with a 1 Tb drive which I resized using Gparted after carrying out most of the software install.

  For both, the home directory is physically on another hard drive.  Doing a Clonezilla backup, I am surprised to see that the 64-version occupies around 102 Gb while the older 32-bit version occupies just 17 Gb.  Does this make sense?   Is there a point to redoing the software installations on the 64-bit?  Or will a 64-bit version  always take about 4 times the space of a 32-bit install?

---

### Post by Autodave on 2017-06-19
My 64 bit Xubuntu takes about 5 gig. 102G sounds more like Windows than Ubuntu.

---

### Post by deadflowr on 2017-06-19
Sounds more like you've got something eating up disk space on the 64-bit side.
A couple good ways to check here:
[https://askubuntu.com/questions/36111/whats-a-command-line-way-to-find-large-files-directories-to-remove-and-free-up]("https://askubuntu.com/questions/36111/whats-a-command-line-way-to-find-large-files-directories-to-remove-and-free-up")

---

### Post by dwlamb on 2017-06-19
> **Autodave said:**
> My 64 bit Xubuntu takes about 5 gig. 102G sounds more like Windows than Ubuntu.

That is what I was thinking.:P

---

### Post by dwlamb on 2017-06-19
> **deadflowr said:**
> Sounds more like you've got something eating up disk space on the 64-bit side.
A couple good ways to check here:
[https://askubuntu.com/questions/36111/whats-a-command-line-way-to-find-large-files-directories-to-remove-and-free-up](https://askubuntu.com/questions/36111/whats-a-command-line-way-to-find-large-files-directories-to-remove-and-free-up)


Thanks for the suggestions.  I will run ncdu and share my findings.

Have a great day

---

### Post by dwlamb on 2017-06-20
I had a duh moment.

I have been working on the transition to the 64-bit machine for about a week.  Early in the process, I didn't have an external immediately available for backups so I directed Simple Backup to save them in a sub-directory of /var.  I have since attached an external drive for those backups and copied the backups from /var/ to the external.  But I failed to delete the backups under /var and forgot all about them.  I ran Clonezilla over the weekend and 70 Gb of backups became part of the Clonezilla snapshot.


](*,) Dang memory

---

### Post by Autodave on 2017-06-21
We have all had those moments. Especially when dealing with computers. :-)  Please rememebr to mark the thread as "closed" using the *Thread Tools* at the top.

---


---
title: "Having problems installing..."
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by sharar on 2008-05-12
im having a lot of problems installing. I was under the impression that there was a guided partitioned install. But the only guided install is full drive. i want to keep windows for certain things so could someone give me step by step guide on how to install ubuntu on a 50gb partition:guitar:

---

### Post by Sef on 2008-05-12
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by zenwalker on 2008-05-12
Hey Ubuntu isntallation via Gparted partition tool is the easiest of all i have found so far. I dont know why u say that. 

Just partition one more drive or split the existiing and mount point it as / and one more for SWAP. VOILA, u r done.

---

### Post by sharar on 2008-05-12
Thats what i was trying to use but Guided resize and use freed space isnt one of the options as i stated in first post
Edit: In response to sef

another edit: I am trying to make a partition using gparted and it wont let me...theres an error symbol next to the hdd. Im just going to give up for the night and keep at it tomorrow i guess

---

### Post by housam on 2008-05-12
Try to partition your HDD manually before installing ubuntu using the Gparted tool ( on the live CD - or download the [[COLOR="Red"]_newer version_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") and burn it to a cd to make a bootable live cd of it ). then start the installation and choose the manual way when it comes to partitioning and assign the already created partitions .but First of all you have to back-up your data - just in case. Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side. This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.

---

### Post by sharar on 2008-05-12
I'm trying to use Gparted, but theres a ! mark in a triangle next to the hdd and it wont let me partition...im getting tempted to just kill windows and go full ubuntu, but windows is always there for me and in case i need it i still want it. WHen i manage to get back on my laptop ill try and find the error message thats next to my hdd.

---

### Post by housam on 2008-05-13
> **sharar said:**
> I'm trying to use Gparted, but theres a ! mark in a triangle next to the hdd and it wont let me partition

Try to use the Gparted live CD not the one on ubuntu live cd.

---


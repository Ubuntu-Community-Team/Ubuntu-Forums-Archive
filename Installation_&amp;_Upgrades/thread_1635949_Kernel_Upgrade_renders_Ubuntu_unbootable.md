---
title: "Kernel Upgrade renders Ubuntu unbootable"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by milk131 on 2010-12-02
Hey all,

I did a routine update of my ubuntu 10.4 (in wubi vista) to the latest kernel (something -26) and installed a java plugin for firefox. After a reboot, i open up the "Ubuntu" entry and i see a message flash accross the screen (something about hda,0,0 or sda im not sure) then it just reboots the PC. No command line or anything. No need to say im pretty screwed

My question is, is there any way to get my files off of wubi? Or even better can i restore Ubuntu to working again?

P.S for some reason the two times i have tried to run a live CD on this laptop, it has corrupted vista.

Thanks in advance

---

### Post by Rubi1200 on 2010-12-02
Hi and welcome to the forums :)

To read the files from within Windows:
To recover files from within windows use [ext2read]("http://ext2read.blogspot.com/"). It can give you readonly access if you point it at the \ubuntu\disks\root.disk file

To repair the Wubi install:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by milk131 on 2010-12-02
OH god thank you, saved me a panic attack there. ext2read is a great program, but mostly im just glad to be back on linux.:KS

Just one last question, for some reason on two separate occasions, booting my laptop into a live CD has caused vista to corrupt. Have you ever heard of anything like this?

Thanks so much:D

---

### Post by Rubi1200 on 2010-12-03
No problem, you are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page so that other users in a similar situation can also find a fix for their problems.

As far as your question is concerned, without knowing more details about what exactly happened it would be hard to answer such a thing.

However, since a LiveCD runs entirely from RAM it should not affect the hard-drive or whatever is installed on it.

In general, Windows issues are caused by Windows problems and not other operating systems or LiveCDs.

---


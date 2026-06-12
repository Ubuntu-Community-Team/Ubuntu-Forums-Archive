---
title: "Ubuntu (ghost) instalation on different systems"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by elfuego on 2007-08-04
Hi!

I am happily using upgraded, updated, completely installed Ubuntu FF on my laptop. The thing is, I would like to install exactly the same Ubuntu also on my desktop system that has no internet connection. I read about downloading packages first and then dpkg installing them, but why would I do that, when I have all the packages I need on my Laptop?

I also read about ghosting the entire partition and then copying it to another system... But the two systems (laptop & desktop) are totally different - laptop is an old P4-M with ATI Radeon mobility (without "restricted" ATI driver, but with XGL) and desktop is based on a C2D with P35 Intel MB and a GF 8800gts (+ many other things as well).

I noticed that Ubuntu does not like changing systems much (unlike Mandriva, for example) and when I tried this once, the X Server didn't start as it should and I got no login screen. Is there a way to make things work?

10x! :)

---

### Post by Pumalite on 2007-08-04
You could try AptOn CD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by elfuego on 2007-08-05
WOW!!! Great! Thanks! That's exactly what I have been looking for!!!! :KS

---

### Post by Pumalite on 2007-08-05
Glad it worked for you. Enjoy!

---

### Post by elfuego on 2007-08-05
Well... Now I tried it and it didn't work :(

The fact is, that program collects archived packages from var/cache/apt/archives and it seems that only archived packages can be written to a medium. This folder is empty in my case, and the program doesn't detect a single installed package, as none of them are archived (well, maybe, but they are not there) :( 

Can aptoncd find the *installed* packages instead of the archived ones? :confused:

---

### Post by Pumalite on 2007-08-05
Absolutely. It worked fine in my system. Double check the documentation. I'm sure it works.

---

### Post by elfuego on 2007-08-05
I triple checked the documentation and also searched the whole file system for *.deb files - and I found none (well, I did found one: aptoncd_0.1-1_all.deb). But I do have 1578 packages installed in synaptic package manager. How can I save these 1578 packages and where can I find them? :(

---

### Post by Pumalite on 2007-08-05
You save them to a CD. You have to install in your system. Then tell it to make you a CD with all your programs. They are kept in the CD. You are then able to install a new system and copy your programs from the CD.

[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

---

### Post by elfuego on 2007-08-06
Thanks for trying, but, really aptoncd doesn't detect a single package. And after reading some other threads pointing to aptoncd from this forum I found out that I have had to have "store every downloaded package locally" (or similar) option selected in synaptic package manager in order for aptoncd to work. It doesn't detect installed packages, but only the ones that had backup in /var/cache/apt/archives/ and therefore it's useless in my case. 

Looks like my best bet is to download a complete ubuntu 4 DVD's and forget about this. :(

Thanks anyway :popcorn:

---

### Post by elfuego on 2007-08-10
OK, here's what I did:
I made a download script from synaptic package manager on my laptop, re-downloaded all the packages, put them on a CD and used synaptic manager to install them (add CD). No aptoncd, no partition copying, no nothing - just plain old re-download and re-install with good old synaptic.

Problem solved! :KS

---

### Post by Rick Z on 2007-08-31
I am a newbie... could you tell me how you finish up in details?  I am trying to do the exactly the task.  use all the main desktop ubuntu and distribute out to other pcs.  Thanks!

---


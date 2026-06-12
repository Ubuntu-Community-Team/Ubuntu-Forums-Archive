---
title: "Interrupted dpkg run"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by gerrymike on 2010-10-10
Hi all!
From the Ubuntu repository I downloaded upgrades for my installed software. While dpkg was installing these there was an electrical storm & a power cut. Now I cannot install or remove any software. 
I am prompted to run a partial upgrade followed by: sudo apt-get install- f.
On running Synaptic Package Manager I am instructed to enter command: sudo dpkg --configure -a.

This results in the message that file: /var/lib/dpkg/updates/0183 has a parse error near line 0 in that ;, should be followed by a colon. 
I have tried to edit this file using VI (VIM) but, not being proficient with this, I am wary of doing further damage.
I would be most grateful for advice & help.
Regards,
Gerard

---

### Post by dino99 on 2010-10-10
well if you have not a package error name, you need to download again

sudo rm -f /var/lib/dpkg/updates/*

---

### Post by gerrymike on 2010-10-10
The suggested fix has worked perfectly, many thanks,
Gerard

---

### Post by mörgæs on 2010-10-10
Good, please mark the thread 'solved'.

---


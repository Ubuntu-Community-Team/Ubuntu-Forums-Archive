---
title: "Grub problems with upgrade"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by sroberts82 on 2008-05-17
I have just upgraded from 7.10 to 8.04. Everything seemed to be going fine until I was asked to reboot. I hit grub and go straight to the grub console which I thought was strange. So I looked in my menu.lst file (I unfortunately hadn't backed up my old one :( ) and everything was just commented out. So I look in my /boot/ directory, and I can see my old kernels and the new one from the upgrade too. So I tried loading my old kernel to get things up and running again, but the kernel paniced because I hadn't entered a root=/blah/blah when I loaded it. Fair enough, but how do I find out what I am supposed to put here? And why did the upgrade make a mess of my menu.lst??

---

### Post by logos34 on 2008-05-17
I had kernel panic happen when I upgraded to gutsy from feisty. For some reason it left out the 'initrd' line in menu.lst.

---

### Post by sroberts82 on 2008-05-17
Thanks for your response. It didnt remove your whole file did it? Also, Im not sure what it should look like really so how can I fix the problem?

---


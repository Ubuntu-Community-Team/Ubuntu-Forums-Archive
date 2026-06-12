---
title: "Video driver upgrade problem"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by short circut on 2008-11-13
So I am using ubuntu studio and i did the upgrade to 8.10. When i reboot X will not start. I was having the same problem as this guy->[here]("http://ubuntuforums.org/showthread.php?t=980905"). Well i triied what was in here and it didnt work. I did some snooping around and it turns out that the problem is not in the xconfig files. the nvidia driver module does not exist. So i looked around. I have it installed and i have the other nvidia stuff installed, but nothing seems to work. Would some one please help me. I really need to use that computer.

---

### Post by oldsoundguy on 2008-11-13
terrible issues with the current crop of Nvida drivers.  Most work, but not completely.  I had to install the legaacy 96 driver on one machine to be able to get wide screen off of a 5500 card.  The word from NVidia and from Envy and hints dropped here "we're working on it".

And forget trying to make sense of the xorg.conf file!  The driver chews that one up really bad!!

---

### Post by short circut on 2008-11-13
Ok I will try that. I dont know why they would upgrade me to a non working version. YOu would think the upgrade scripts would try to avoid taht kind of thing. i will let you know what happens in a few minutes

---

### Post by short circut on 2008-11-13
Well i cant actually download the 96 drivers.  apt cant find them.

---

### Post by short circut on 2008-11-13
Does any one have anymore ideas

---

### Post by oldsoundguy on 2008-11-13
open synaptic and type nvida into the search box.  The 96 (and all others) should show up there. (they were in my 8.10 on three boxes.)

---

### Post by short circut on 2008-11-13
I will try that again, but it didnt work the first time. The problem wasnt that it wasnt in the list. the problem was that it was not properly linked.

---

### Post by oldsoundguy on 2008-11-13
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

You need to get the non-free repositories up and running especially!

---


---
title: "Cannot boot when installing Edgy with SW-raid"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by Erik-NA on 2006-12-02
I am trying to install Edgy with software raid om my two 250Gb hard discs. I followed this tutorial 

[http://users.piuha.net/martti/comp/ubuntu/raid.html]("http://users.piuha.net/martti/comp/ubuntu/raid.html")

with the following changes:

Swap raid1 partion is the first 
Root raid1 partion is the second
Two raid1 partions as third and fourth

The installation woorks well, but when I reboot I get the following error.


Error 17: Cannot mount selected partition.

I cannot verify the installation accordning to chapter 2 in the tutorial, since it is not possible to boot.

What is wrong, and what can I do?

Thanks

/Erik-NA

---

### Post by Erik-NA on 2006-12-02
I found the problem

I read this thread [http://ubuntuforums.org/showthread.php?t=260625&highlight=Error+17%3A+Cannot+mount+selected+partition](http://ubuntuforums.org/showthread.php?t=260625&highlight=Error+17%3A+Cannot+mount+selected+partition)

And checked which partition grub wanted to boot on. It was on (hd0,0) and changing to (hd1,1) worked

---


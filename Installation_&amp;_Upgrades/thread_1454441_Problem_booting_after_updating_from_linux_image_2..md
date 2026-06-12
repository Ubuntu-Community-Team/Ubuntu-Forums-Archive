---
title: "Problem booting after updating from linux image 2.6.31-14 generic to 2.6.31-20"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by shaquille on 2010-04-14
Hello there, I am new to Ubuntu Forum. I am using Ubuntu 9.10 for some time and comparatively new to Ubuntu. When I install Ubuntu, I saw in the update manager there are many things to update. I was updating  all of them. As linux image 2.6.31-20 generic was the biggest file and some other files was associated with it, I kept it to update last. When I finished updating this I was prompted to restart. I restarted my PC. But I cannot boot ubuntu. There is a message saying
 
"GNU GRUB 1.97 Beta" 

and below some line. After that there was

"sh:grub>"

and nothing. 
I cannot just boot.
I have installed ununtu in my windows xp, and I didn't do any change of xp after installing ubuntu.

Computer confuguration:
Intel Celeron 2.13 gigahertz processor, MSI P4 via motherboard, 480MB ram, 320gb HDD. 

I have to face this problem third time this year. That means I have installed Ubuntu several times before and faced the same problem. And I had no way other than reinstalling Ubuntu after this problem. Please help me. 

Thanking
Shaquille

---

### Post by oldfred on 2010-04-14
When you say in windows XP is this a wubi install?

There is a known bug in wubi.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by shaquille on 2010-04-14
> **oldfred said:**
> When you say in windows XP is this a wubi install?

There is a known bug in wubi.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Thanks 
Thanks a lot!!
It worked.

---


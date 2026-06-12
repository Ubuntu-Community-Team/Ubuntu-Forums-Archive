---
title: "Help: Uninstalling Ubuntu (dual boot)"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by laklive on 2007-01-12
Hello, 

First and foremost, I want to thank everyone in these forums for all of your helpful advice. They are making my switch to linux as smooth as it can be.

Here is my issue. I currently dual boot ubuntu 6.10 and windows xp using different partitions in my drive. I am now planning to install a second drive which I will use linux in. Now I want to uninstall ubuntu from my current drive and restore that space for windows. 

Now I've read different discussions about how I can first fix the MBR in the Win XP recovery console using a windows cd. My computer came pre-installed with xp so I don't have any window cd's. I've also tried booting windows with F8 but I really couldn't find any recovery console there. Are there other methods I can use without screwing up my windows system?

Also, if I am able to fix the MBR and delete the partitions, will that automatically restore the hard drive space for windows?

Thanks everyone.

---

### Post by Irony on 2007-01-12
Don't uninstall ubuntu. First install your second hard drive then copy ubuntu over to it;

[http://www.pclinuxos.com/forum/index.php?topic=13404.0](http://www.pclinuxos.com/forum/index.php?topic=13404.0)

This way you won't have to install ubuntu.

You then change grub to point at the second hard drive.

Fixing your MBR doesn't affect the partitions.

---


---
title: "Reinstall with existing /home partition"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by covert215 on 2008-05-25
I first installed Ubuntu on my main workstation at 6.04 and I have been continuously updating without ever reinstalling.  I've used bleeding/alpha releases in this span (yes, I know its stupid), so I've messed with a lot of settings and utilities.  I've decided that I want a fresh install.

I had the foresight to place my /home directory on its own partition, but I'd like advice for reinstalling.  How do I tell Ubuntu to recognize the existing partition as /home and be certain not to overwrite it?

Thanks in advance.

---

### Post by Pumalite on 2008-05-25
Go Manual choose the partitions. When you choose /home; DO NOT FORMAT

---

### Post by &amp;wP*!) on 2008-05-25
> **covert215 said:**
> I first installed Ubuntu on my main workstation at 6.04 and I have been continuously updating without ever reinstalling.  I've used bleeding/alpha releases in this span (yes, I know its stupid), so I've messed with a lot of settings and utilities.  I've decided that I want a fresh install.

I had the foresight to place my /home directory on its own partition, but I'd like advice for reinstalling.  How do I tell Ubuntu to recognize the existing partition as /home and be certain not to overwrite it?

Thanks in advance.

Ubuntu installation gives you chance not to format the partitions created before.

Run the installation. When it comes to partitioning phase, choose custom partition/expert/advance mode. I have forgotten which of them but I did 4 installations of Ubuntu and in all of them I kept my home in that way.

In this case, Ubuntu install will ask you which partition must be mapped to which one. Choose your /home and set disable format. You will get home then. But don't forget that some config settings about desktop or any other application stored in /home might be not compatible to newer versions any more.

---


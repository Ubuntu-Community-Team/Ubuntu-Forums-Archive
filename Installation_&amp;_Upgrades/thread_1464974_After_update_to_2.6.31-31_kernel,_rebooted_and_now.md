---
title: "After update to 2.6.31-31 kernel, rebooted and now faced with grub command line"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by traductionbiz on 2010-04-28
Hi, 

After the running of an automatic update, the kernel was updated to 2.6.31-31, but when I reboot the system I'm left faced with the grub command line, but Ubuntu is not loading.

I've got 9.10 installed using Wubi on top of a Windows partition.

What can I do to get back to my Ubuntu desktop?

Any help much appreciated. :-)

---

### Post by smellyman on 2010-04-28
I had this issue a lot with wubi which made me go to dual booting rather than wubi.
 
I think post 10 in [this thread]("http://ubuntuforums.org/showthread.php?t=1339203&highlight=wubi+kernel+upgrade+grub") is the usuall fix.

---

### Post by oldfred on 2010-04-28
In smellyman's link above see post 30 not post 20.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by smellyman on 2010-04-28
> **oldfred said:**
> In smellyman's link above see post 30 not post 20.
 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
 
whoops...thanks Fred

---

### Post by traductionbiz on 2010-04-29
Thanks, guys, :-)

The solution at 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

fixed the problem. By copying the suggested file into the root of C:/ I could boot properly into Ubuntu from the Windows boot loader.

---


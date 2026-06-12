---
title: "Grub2 Problem"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Uzumaki on 2010-04-14
I've been through a lot of the posts already, but nothing seems to solve my problem.

I have Ubuntu 9.10 and Windows 7 dual installed (Windows was installed first). Everything has been working fine until a few weeks ago when I accidentally left a USB drive plugged in when I restarted my computer from Windows.

Ever since then, whenever I have restarted my computer from Windows grub2 has failed (it does not fail when I restart from Ubuntu). I get a varying message like...

**[SIZE=1]Grub loading. The symbol ' ' not found. Aborted. Press any key...[/SIZE]**

...where the part between the single quotes is usually different each time. When this happens I have to reinstall Grub2 from a live disk, which is becoming a bit of a pain. 

I've been reading around, but I don't really have a great understanding yet of how hard drives and partitions work in general, and so I haven't been able to work out what the source of this problem is. 

Can anybody give me any advice or point me in the right direction?

---

### Post by oldfred on 2010-04-14
Welcome to the forums.

Windows has some software that writes into the MBR and corrupts grub2. Confirmed with HP and Dell, but some other systems have a variety of things that seem to do the same thing.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by Uzumaki on 2010-04-14
Tanks oldfred!

Those links were really helpful. 

I'll start by taking off the Dell backup software and see how that goes.

Thanks again.

---


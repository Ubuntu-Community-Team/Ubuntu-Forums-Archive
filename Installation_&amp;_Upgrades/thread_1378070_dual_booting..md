---
title: "dual booting."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Tadcrazio on 2010-01-11
I was successfully dual booting vista and Ubuntu.. I upgraded to windows 7 and now when my computer starts i don't even have the option to pick my operating system. Any suggestions?

---

### Post by lisati on 2010-01-11
What version of Ubuntu are you using?

If you are using 9.04 or earlier, you will need to restore grub. See here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

9.10 uses grub2, which needs a different approach. See here: [http://ubuntuforums.org/showthread.php?t=1295297](http://ubuntuforums.org/showthread.php?t=1295297)

---

### Post by sumedh.deb on 2010-01-11
u have to repair GRUB.

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)
here it is.Hope it helps...

---

### Post by Tadcrazio on 2010-01-11
thanks will do! btw 9.10

---

### Post by Sef on 2010-01-11
When you upgraded to Windows 7, Windows overwrote grub; hence, you have to put it back in.

---


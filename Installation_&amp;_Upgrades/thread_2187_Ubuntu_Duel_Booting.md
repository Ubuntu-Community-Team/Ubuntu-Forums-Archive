---
title: "Ubuntu Duel Booting"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by jcscar on 2004-10-26
I have Ubuntu and a windows installation on the same drive
Windows is on the first partition and ubuntu the next.  There is only one drive at the moment.  This is cut and paste from my menu.lst in the folder /boot/grub

title		Windows
rootnoverify	(hd0,0)
makeactive
chainloader	+1
savedefault

When trying to access windows it just sits there wit that on the screen. I believe the hd0,0 is correct from reading other boards.  I have the minor rearrangement in from a post about windows 2000 but none of that seems to work.  Ubuntu is running great, using it at the moment to post this thread.  Please help.

---

### Post by FLeiXiuS on 2004-10-26
[QUOTE=jcscar]
title		Windows
rootnoverify	**(hd0,0)**
makeactive
chainloader	+1
savedefault
[/QUOTE]

Where does this menu boot?

---

### Post by wiraone on 2004-10-26
I guess the CHS/LBA bug got into your PC during ubuntu installation. It did on mine just now and I couldn't boot my WinXP partition tho my Fedora partitions left intact. Go to your BIOS, change the HD setting from Auto or CHS to LBA and try again.

---

### Post by jcscar on 2004-10-26
[QUOTE=FLeiXiuS]Where does this menu boot?[/QUOTE]
It is suppose to boot WIndows XP Pro

---

### Post by jdong on 2004-10-26
(that's when the two OS'es draw their swords and engage in violent combat)

it seems like a case of CHS fever... see [http://www.broadbandreports.com/forum/remark,10472664~mode=flat](http://www.broadbandreports.com/forum/remark,10472664~mode=flat) this thread for info on fixing it.

---

### Post by jcscar on 2004-10-26
[QUOTE=wiraone]I guess the CHS/LBA bug got into your PC during ubuntu installation. It did on mine just now and I couldn't boot my WinXP partition tho my Fedora partitions left intact. Go to your BIOS, change the HD setting from Auto or CHS to LBA and try again.[/QUOTE]
This fixed it, Thanks!!!

---


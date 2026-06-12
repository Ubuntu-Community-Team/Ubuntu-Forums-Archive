---
title: "Editing menu.lst (Dual booting 2 distros)"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by Hex_Mandos on 2007-07-20
I recently installed PCLinuxOS on a separate partition. I tried adding Ubuntu to GRUB via PCLOS' graphical GRUB editing tool, but the results were terrible. I'm going to edit menu.lst manually. Can anyone post Feisty's menu.lst entry? Is something other than adding/editing that entry necessary?

---

### Post by confused57 on 2007-07-20
> **Hex_Mandos said:**
> I recently installed PCLinuxOS on a separate partition. I tried adding Ubuntu to GRUB via PCLOS' graphical GRUB editing tool, but the results were terrible. I'm going to edit menu.lst manually. Can anyone post Feisty's menu.lst entry? Is something other than adding/editing that entry necessary?
You could probably use a configfile entry to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You could also use the live cd to install Ubuntu's grub IPL to the mbr, then add an entry to boot PCLinux:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by Hex_Mandos on 2007-07-20
Man, am I an idiot. I just copied the entry from my Ubuntu partition, adjusting for details. Works perfectly now. Thanks.

---

### Post by confused57 on 2007-07-20
> **Hex_Mandos said:**
> Man, am I an idiot. I just copied the entry from my Ubuntu partition, adjusting for details. Works perfectly now. Thanks.
If you have a kernel update in Ubuntu, you'll need to copy the new boot entry to PCLinux's menu.lst.  With configfile, you don't have to do this, you're booting directly into Ubuntu's grub boot menu...although, some people prefer not to have to boot into another grub boot menu...

---


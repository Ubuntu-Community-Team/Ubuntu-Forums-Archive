---
title: "Ubuntu/Kubuntu, whatever strange boot problem."
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by Peyj on 2007-06-27
Ive tried enough now. Every singe version of Ubuntu/Kubuntu or whichever ubuntu-based linux distrubution does the same to me. Grub error 18. After a lot of googling I've understood that it has to do with BIOS and 1024 first cylinders. What I think is strange is that a fresh standard Kubuntu Fiesty install don't fix this automaticly. For example do Fedora always boot properly with default options, same thing with Zenwalk, openSUSE, Debian, you name it.But not Ubuntu. I would like a simple fix, please. I'd really like to test out Kubuntu since ubuntu/Kubuntu is so popular and I want to know what the fuss is all about ;) :popcorn:

Ive also recognized that there is no /etc/grub.conf? Wierd for me as 1year fedora user :P May it has to be with that? Oh well, Im only guessing...

---

### Post by OzzyFrank on 2007-06-27
Hi. Not sure what the error 18 is, but if it had anything to do with the BIOS, installing an OS wouldn't fix it, I'm pretty certain of that. But if you run other Linux distros, it probably isn't your BIOS, so I suggest looking into your grub setup. The file is /boot/grub/menu.lst.

If all seems OK, maybe a manual GRUB restore is in order (I find it's just the quickest way to get around errors like #17 where the partition apparently isn't found... even though GRUB gets its menu from it, hehe). To manually restore grub, boot with the live CD and type grub (or sudo grub) at the command prompt, and when at the grub prompt (substitute your drive):

root (hd1,0)

setup (hd1) - [to put grub in mbr of the drive]
or
setup (hd1,0) - [to put it on the actual partition, which is my preference]

Note that in grub, (hd1,0) is the same as /dev/hdb1.

Hope this helps. Best of luck.

---

### Post by Peyj on 2007-06-27
Hmm... I've tried looking in menu.lst and so but I dont think that has to do with the problem since this "bug"'s consitency. It ALWAYS happen all Ubuntu- or Ubuntubased- distrubutions and on NO OTHER distrubutions.. Well, Ive come up with a half-dirty fix that is installing Fedora beside Kubuntu overwriting MBR with fedora-grub and then copy from menu.lst on the Kubuntu partition. Strange problem thou, and it is something about Ubuntu's GRUb that isn't alright, oh well... :P 

And thanks fo the tips in case I need them later on.. ;)

---


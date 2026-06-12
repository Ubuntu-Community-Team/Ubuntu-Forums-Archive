---
title: "Another Dual Boot GRUB problem"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by Ampsonic on 2005-03-04
I've looked high and low, and I can't find an answer to my particular problem. Sorry if this is a repeat.

I've got a winxp machine, 2 hard drives. I installed ubuntu to the 2nd drive. It installed grub to my first hard drive. When I rebooted the machine, grub came up, and then just sat there without any options. I couldn't boot anything.

Ran fixmbr off my winxp cd and I could get back to my windows system.

Anyway, formated the 2nd drive, reinstalled ubuntu, but this time I didn't install grub.  

Can I use the windows boot loader? I read this article:
[http://bratlady.com/linux_boot.shtml](http://bratlady.com/linux_boot.shtml)

but I don't know how to do, well, any of that with winxp and ubuntu. 

What should I do?

---

### Post by Ampsonic on 2005-03-05
Bump. Sorry, I just feel like this topic may have gotten lost in the sea of other topics. Is there a simple line I can add to my windows boot.ini to make linux an option?

---

### Post by MetalMusicAddict on 2005-03-05
Try setting the access mode in the BIOS to "LBA" on the HDs. Not "Auto".

---

### Post by pigpen on 2005-03-05
Yeah I read a couple articles that use the winxp/win2k boot loader to dual boot linux, but it seemed a bit complicated.

If I were you, I'd just let GRUB install into the MBR and try to figure it out that way, and try out MetalMusicAddict's suggestion about the BIOS.  This explains it a bit more in detail about the BIOS GRUB error 18 message, if thats the problem.
[http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes)

If that doesn't work, since you are using dual hard drives, maybe its a hard drive "virtual swap" issue. Look here at the section about swapping hard drives.
[http://www.gnu.org/software/grub/manual/grub.html#DOS%2fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS%2fWindows)
I didn't have to do this solution, but you can do a search in the forums and several people had to edit GRUB's menu.lst file to fool windows into thinking it was the 1st partition.

---


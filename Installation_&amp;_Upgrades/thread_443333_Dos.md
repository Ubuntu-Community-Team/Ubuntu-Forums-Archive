---
title: "Dos?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by jemmess on 2007-05-14
I managed to make a bootable CD, using a freeware program I found, as the software linked to did not seem to like my Windoze ME system, but when I boot from it after modifying the BIOS, I don't go to a GUI environment, but a sort of DOS line that I am unfamiliar with. What should I do? The system is a Dell Dimension 4100 (I think)- it has P3 866MHz, 384MB RAM, and a 20GB HDD.

---

### Post by hartz on 2007-05-14
Hi jemmess

What CD did you create?  Is it one of the ubuntu/kubuntu disks?  Did you perhaps get the "alternate install" disk?

I know that several of the bootable "rescue" CD images that you can download actually do not contain a GUI, only a console interface which, because it is simple text that scrolls past, reminds a lot of the old DOS command-line interface.

Could you enter these two commands at the shell prompt and tell us what you get:

```
uname -a
```
```
cat /etc/issue
```

Also tell us what the prompt looks like, often something like
```
guest@ubuntu:~$
```

---

### Post by jemmess on 2007-05-16
It's Caldera DR-DOS, but I found the problem. I transcribed the files from the ISO file, hen burned them, rather than buring the ISO file straight. Problem fixed. :guitar:

---


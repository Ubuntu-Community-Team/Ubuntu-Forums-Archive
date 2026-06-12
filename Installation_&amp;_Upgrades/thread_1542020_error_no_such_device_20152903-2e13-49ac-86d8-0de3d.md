---
title: "error no such device 20152903-2e13-49ac-86d8-0de3dbbe67ff"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by shinigami13 on 2010-07-29
Just installed Ubuntu netbook 10.04 on my lenovo s10 using wubi i have a xp OS installed. it was working find until i updated it using the update manager. it updated the grub and after restarting. after the bios it shows error no such device 20152903-2e13-49ac-86d8-0de3dbbe67ff and it has a command line that says grub rescue>

i'm practically new in linux and want to try it out.

BTW my HD was partition into two parts C: (where the xp is) and D:(where the ubuntu was installed).

---

### Post by P4man on 2010-07-30
If you are using a seperate partition for ubuntu there is no point in using wubi. It just causes problems. Your problem is probably fixable but I would strongly urge you to do a regular (native) install. Boot from an ubuntu USB stick and install from the livesession.

Anyway, to fix your problem ad interim, perhaps try this (although the fix is for 9.10 i suspect its the same problem):
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by bcbc on 2010-07-30
> **shinigami13 said:**
> Just installed Ubuntu netbook 10.04 on my lenovo s10 using wubi i have a xp OS installed. it was working find until i updated it using the update manager. it updated the grub and after restarting. after the bios it shows error no such device 20152903-2e13-49ac-86d8-0de3dbbe67ff and it has a command line that says grub rescue>

i'm practically new in linux and want to try it out.

BTW my HD was partition into two parts C: (where the xp is) and D:(where the ubuntu was installed).

You've installed grub to your hard drive MBR (it's been happening with the latest grub updates). With wubi you need the windows bootloader. Either replace it with your windows repair cd/dvd or install a comparable bootloader such as lilo using the ubuntu live cd:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by shinigami13 on 2010-07-31
> **P4man said:**
> If you are using a seperate partition for ubuntu there is no point in using wubi. It just causes problems. Your problem is probably fixable but I would strongly urge you to do a regular (native) install. Boot from an ubuntu USB stick and install from the livesession.

Anyway, to fix your problem ad interim, perhaps try this (although the fix is for 9.10 i suspect its the same problem):
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


Just want to try out ubuntu. so i decided to install it on a free partition .. in fear of doing something that may corrupt my other OS.ehehe.. but i will be installing it side by side with xp... 
about the problem i encountered. i did some research and found out about super grub disk and use it to fix the bootloader..   Thanks for the advice .eheh.

---


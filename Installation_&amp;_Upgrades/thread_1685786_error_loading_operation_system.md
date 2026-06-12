---
title: "error loading operation system"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by mateofalcone on 2011-02-11
i have asus eee pc 701 and i had xp on it. then i made live cd copy of ubuntu on my flesh and boot it. i install ubuntu 7.3. and i was thinking everything is ok and unplug flesh and reboot it. but there was a problem it did not boot. there was written in black screen: error loading operation system. i tried to load from flesh again but there is the same problem, it says the same error. please help,i can do nothing with it. waiting for replies.

---

### Post by ajgreeny on 2011-02-11
Does the live USB flash still work without problem?  If so can you boot to that and then in terminal rub command ```
lspci
``` and report the output back here, please.  I suspect that you have a problem with the graphics card, which is not displaying properly when installed; this command will tell us what you have, I hope

---

### Post by mateofalcone on 2011-02-11
USB works on another PC,but it cant be booted on my asus netbook, so i cant test command lspci. in any case i am trying to install any version of ubuntu or other os(like xp) it does not boot anything, not from USb neither from HD. its awful, practicaly i lost my netbook. still waiting for your help :)

---

### Post by Quackers on 2011-02-11
Have you set the bios to boot from the usb flash drive first?

---

### Post by mateofalcone on 2011-02-11
sure, i did it, also i push Esc and choose from their booting device

---

### Post by Quackers on 2011-02-11
I presume that by pressing Esc you can choose a bootable device on a per-session basis. That means that you will have to do that every time you want to boot from anything other than your hard drive. Are you doing that when trying to boot from the flash drive, and is the flash drive a boot device option?

---

### Post by mateofalcone on 2011-02-12
problem is not in this. i have set my USb flash drive as primary booting device but still the same error.

---


---
title: "Can't reboot after restart: Couldn't get size: 0x80000000000000e"
date: 2020-01-03
forum: Installation &amp; Upgrades
---

### Post by itsx on 2020-01-03
Hello Ubuntu friends. 
Today I encountered a problem, which I am not able to solve. After Ubuntu restart I am not able to boot the system. 

I get to an emergency mode, and when I type: `journalctl -xb` I see the red error:

`kernel: Couldn't get size: 0x800000000000000e`

I googled extensively, found out probably a same problem on CentOS forums, but I am still not able to solve it.

I have:
- Ubuntu 18.04
- 4.15.0-72-generic
- dual boot
- Secure boot in bios disabled (when enabled no effect)

HW:
- motherboard: Lenovo SDK0J40697 WIN
- BIOS: 2WCN29WW 
- HD Graphics 620 (Intel)


Please any help is very appreciated.

---

### Post by yancek on 2020-01-03
Take a look at the link below, post #6 with a possible solution.  Make a note of what you do if it fails so you can go back to the original settings.

[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

---


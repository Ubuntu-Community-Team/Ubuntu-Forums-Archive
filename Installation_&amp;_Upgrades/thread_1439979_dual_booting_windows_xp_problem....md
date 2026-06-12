---
title: "dual booting windows xp problem..."
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by jupdown on 2010-03-26
I apologize in future in case this is a really newbie mistake, I have a Compaq mini 110c 1100ca netbook and I installed Ubuntu 9.10 on it. during installation i split the hard drive in half ( 2 partitions ) and then gave myself 2GB of swap space. I formated and installed Ubuntu on one of the partitions but I left the other one empty so I could dual boot XP and Ubuntu in the future.

now i was going to install windows XP and I inserted my flash drive and had the pc boot from it but instead of booting from the flash drive it says the following :

Remove disks or other media.
Press any key to restart
_

when i press enter it boots into my Linux partition
It wont boot the XP installer from my flash drive. anyone have an idea whats going wrong?

---

### Post by byStanderone on 2010-03-26
...not sure if this will do the trick, while in karmic, keep your live usb in place and do a sudo update-grub, then reboot.

---

### Post by jupdown on 2010-03-26
what does it mean to be in karmic? :P sry im a complete noob..

---

### Post by wilee-nilee on 2010-03-26
Do you know that this USB is a bootable installer for sure.

---

### Post by jupdown on 2010-03-26
Cant say 100% for sure.... it should be. I used a program called Pe to USB that was said to work. I also used a modified version of windows xp (windows xp Xtream edition) instead of a regular edition but the modified one is known for working.

---

### Post by wilee-nilee on 2010-03-26
> **jupdown said:**
> Cant say 100% for sure.... it should be. I used a program called Pe to USB that was said to work. I also used a modified version of windows xp (windows xp Xtream edition) instead of a regular edition but the modified one is known for working.

I tried several methods that were said to work, with a XP slipstreamed acer reload ISO, and could never get it to work on a USB, Try another computer, I believe just starting it wont mess with the MBR of another. The acer xp burned fine to a cd and installed with no problems.

---

### Post by jupdown on 2010-03-26
ok just tested it... usb flash drive doesnt work properly... problem solved...

---


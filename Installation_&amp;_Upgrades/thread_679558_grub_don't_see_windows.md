---
title: "grub don't see windows"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by steve984 on 2008-01-27
Hi I installed ubuntu on c: drive and I have windows ON d: drive and the grub don't see the windows drive I have tried super grub but that didn'tt seem to help.  Windows isnt even on the menu thanks steve

---

### Post by kellemes on 2008-01-27
Can you please post the contents of the following file?
/boot/grub/menu.lst

---

### Post by steve984 on 2008-01-27
I changed the menu.lst and it showed windows but it wouldnT boot up, so I tried fixmbr on windows and there was something wrong with the drive so what I ended up doing was reinstalling windows to c: and I kept ubuntu on d: drive and if I want to boot to ubuntu I can do it thru the bios.  I think the problem was I had windows on d: to begin and there was no mbr for that drive. it seems to work though I ubuntu and windows I just have to stay at the computer to get it to boot up.

---


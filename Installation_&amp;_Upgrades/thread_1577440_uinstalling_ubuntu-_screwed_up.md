---
title: "uinstalling ubuntu- screwed up"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by helldemon80 on 2010-09-18
Hello

I installed Ubuntu 10.04 on my laptop and afterwards didn't feel the need for it. So i decided to uninstall it to get more space for my windows 7 partition. So i deleted the partition for Ubuntu 10.04 and restarted my computer and now im stuck in the Grub rescue and cannot boot any OS. 

Please Help, how do i uninstall grub or do i need to reinstall Ubuntu with live cd and restart? Thanks.

My bad, "Uninstalling Ubuntu", sometimes i really don't notice my spelling

---

### Post by bcbc on 2010-09-18
You just need the windows bootloader to replace the grub bootloader in the MBR. You can boot from a windows disc, select repair and run "fixmbr" for XP, or "bootrec.exe /fixmbr" for vista/7.

You can do it from a live CD as well if you don't have a windows disc.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by helldemon80 on 2010-09-18
> **bcbc said:**
> You just need the windows bootloader to replace the grub bootloader in the MBR. You can boot from a windows disc, select repair and run "fixmbr" for XP, or "bootrec.exe /fixmbr" for vista/7.

You can do it from a live CD as well if you don't have a windows disc.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```


How do i do this with a live CD, i don't have the windows disc.

Thanks so much

---

### Post by uRock on 2010-09-18
Boot the LiveCD, come to this age, copy, paste and run the commands in a terminal one at a time.

To get a terminal, Go in the menus to Applications> Accessories> Terminal

---

### Post by helldemon80 on 2010-09-18
Sigh...thanks so much for your help guys.. Windows 7 Finally booted.

Problem Solved.

---


---
title: "Dual boot issue with IDE and SATA drive"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by luckyaba on 2007-01-07
I had to reinstall my windows on the SATA drive and when i boot i am unable to boot into windows through the Grub list. I have linux on the IDE which is set to boot first and  windows on the SATA. 

(hd0)   /dev/hdc
(hd1)   /dev/sda

those are the drives and now here is my menu.lst entry for windows

title		              Microsoft's P OS's:
root

title     	               Windows XP Pro
root 		             (hd1,0)
makeactive
chainloader +1

whenever i try and boot to windows i get something that says unknown filesystem. I could be wrong but i think my computer is straight BSing me. 

SOLUTION:

I had to map the drives in the menu.lst for grub

title     	               Windows XP Pro
map                        (hd0,0), (hd1,0)
map                        (hd1,0), (hd0,0)
root 		             (hd1,0)
makeactive
chainloader +1

---

### Post by geek_Man on 2007-01-07
Could you tell me your setup, please? Like anything that could be related to GRUB (on your system). I can't get GRUB to work with my external SATA drive. I use Super GRUB Disk, but I'd like to use GRUB.

---


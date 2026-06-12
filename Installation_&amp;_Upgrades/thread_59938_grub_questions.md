---
title: "grub questions"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by occy8 on 2005-08-25
Hello, I had to reinstall windows and of course it replaced the mbr and I couldn't get into Ubuntu anymore....
I ran the Ubuntu install cd again but now I have many Ubuntu entrys in Grub.

Questions 
How do I edit grub or at least the boot list?
I didn't find any function like create boot disk, is there any or is there a way to back up the mbr and restore it from a boot disk?

---

### Post by amohanty on 2005-08-25
[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

HTH
AM

---

### Post by occy8 on 2005-08-27
yes thats what I did, just thought there would be another way
I tried smartbootmanager but it only boots windows or at least I couldn't figure out how to boot linux with it

I managed to get grub on floppy but vmlinuz doesn't fit.
I remember ages ago Mandrake had a boot disk...  that was lilo though I think

---

### Post by amohanty on 2005-08-27
> How do I edit grub or at least the boot list? 

in terminal type
visudo /boot/grub/menu.lst

HTH
AM

---


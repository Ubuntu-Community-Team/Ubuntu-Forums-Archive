---
title: "Un-Installation"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by rgoode on 2007-12-10
I have a computer with two hard drives. One of them was for gusty and the other one was for windows. I soon realized that my windows hard drive was almost full. I installed Partition Magic and reformatted the gusty drive so i could use it for storage. When I rebooted the computer it tried to load the GRUB1.5 manager, but it couldnt because gusty was gone. Now my computer won't boot at all it tries to load GRUB1.5 then it says "ERROR 17". is there any way to remove the GRUB program so my computer will automatically boot into windows?

---

### Post by Partyboi2 on 2007-12-10
You will need to restore the mbr for windows.
you can fix that by using the windows disk
Boot from the XP cd, get to the recovery console and enter "fixmbr".

---


---
title: "Failed to restore Grub2; workaround?"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2011-10-16
I had to set up two identical computers. I set up one of them, then used CloneZilla to copy its root partition to the second computer. Being a good boy, I reset the UUID of that new partition to a new, random UUID.

As the UUID was different, I followed the instructions to [reinstall Grub2 from the Live CD]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files") as follows:

[LIST=1]
[*]Boot from the Live CD.
[*]```
sudo mount /dev/sda7 /media/annroot   # sda7 contains the restored Ubuntu
```
[*]```
sudo grub-install --boot-directory=/media/annroot/boot /dev/sda
```
[/LIST]
 
Curiously, Grub2 still failed because /boot/grub/grub.cfg still contained the original UUID. I managed to get it working by editing that file (from the Live CD) to use the new UUID (in 12 different places).

So, obviously, I failed to do something. For future use, please would you let me know what I needed to do differently?

---

### Post by zvacet on 2011-10-16
Boot from live Cd and follow [this]("https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Use_Boot-Repair_Graphical_Tool") instructions.You will have to add PPA to get that tool,but I tried it once and it worked for me.

---

### Post by Paddy Landau on 2011-10-16
Thank you. I have noted it in my documentation, and next time I have this situation I shall try it.

---


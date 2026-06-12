---
title: "Strange error 15 on Grub"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by mschievano on 2006-06-18
Hello,
I know what's the meaning of the error 15 on Grub, but this time is very strange.
I see an error 15 after flashing my motherboard bios (asus a8n-e sli).
Even if i reinstall grub, and reinstall dapper, the error won't disappear.

But...

If i place the CD on dapper 6.06 on drive, boot from Cd, and select booot from HD, the Grub menu magically appear!!

Can someone tell me how can i fix this?

Thanks! :lol:

---

### Post by zxee on 2006-06-18
It seems like your master boot record is snafued. Have you tried to clear it?
 in dos the command is fdisk /mbr (all lower case and a space after the fdisk.
From the ubuntu live cd enter a shell and do sudo install-mbr /dev/hda
or use the correct hd designation if your primary drive isn't hda. Hope that helps.

---

### Post by mschievano on 2006-06-19
[QUOTE=zxee]It seems like your master boot record is snafued. Have you tried to clear it?
 in dos the command is fdisk /mbr (all lower case and a space after the fdisk.
From the ubuntu live cd enter a shell and do sudo install-mbr /dev/hda
or use the correct hd designation if your primary drive isn't hda. Hope that helps.[/QUOTE]

if i have only the 6.06 ubuntu install cd?

---

### Post by mschievano on 2006-06-29
[QUOTE=mschievano]if i have only the 6.06 ubuntu install cd?[/QUOTE]

I boot in graphics mode whit the ubuntu 6.06 CD, and run 
sudo install-mbr /dev/hda

but nothing... when I boot : error 15

so, I put the Xp home edition CD and try to use the recovery console. I fix the mbr, reboot... error 15

I don't know how to do. I didn't want to format all the HD, then format in low level mode and reinstall winn and ubuntu, and i don't have the floppy drive.

Ideas?

---

### Post by mschievano on 2006-07-02
[QUOTE=mschievano]I boot in graphics mode whit the ubuntu 6.06 CD, and run 
sudo install-mbr /dev/hda

but nothing... when I boot : error 15

so, I put the Xp home edition CD and try to use the recovery console. I fix the mbr, reboot... error 15

I don't know how to do. I didn't want to format all the HD, then format in low level mode and reinstall winn and ubuntu, and i don't have the floppy drive.

Ideas?[/QUOTE]

no one?

---

### Post by andreas72 on 2006-08-18
Maybe it's too late.. anyway i think you should check whether the partition you want to boot it's BOOTABLE.
I suggest to use cfdisk and put it as bootable (remember to use sudo).

In fact if the partition is not bootable, then even if mbr is correctly compiled, the information cannot be use unbootable partition...

Hope this can be of somewhat help..

Andrea

---


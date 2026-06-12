---
title: "Grub won't allow Win7 boot after 11.10 upgrade"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by language4u on 2011-10-20
Hi all - 

I had a 11.04/Win7 dual boot which was working fine. 

Just upgraded to 11.10. 

Now I can't get into Win7. Since 11.10 is the default OS, it will boot into 11.10 if I just leave it alone, but the arrow keys don't let me select another OS. It feels as though the keyboard isn't being recognized, but when I get into the 11.10 login screen, I can type away. 

Any help?

Thanks

---

### Post by oldfred on 2011-10-21
Have you checked BIOS settings. I had the same issue several versions ago & had to change BIOS to allow USB keyboard & mouse. Both Windows & Ubuntu seem to install own drivers but grub does not  have any extra drivers.

Some also have had issues with a BIOS setting of quickboot or fastboot.

---

### Post by language4u on 2011-10-23
Thanks, will try. Oddly, another keyboard worked. It never occurred to me that grub would have a problem with particular keyboards, but there you go.

---


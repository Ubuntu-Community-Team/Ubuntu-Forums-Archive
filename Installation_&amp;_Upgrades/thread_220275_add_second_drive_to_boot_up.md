---
title: "add second drive to boot up"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by Bukunut on 2006-07-21
Hello

Wanting to try Fedora I loaded Fedora to a second drive (unplugging 1st drive to ensure nothing got munged!)
The problem is now is that I did the installation forgetting to stop Fedora adding a boot area on the second drive.

How is the best way now to add the second drive to the boot sequence of the first drive (or remove the boot area from the second drive?) 
so that it will be 1. XP 2. Kubuntu 3. Fedora (2nd Drive)

Thank you for any help (Always learning) 

Bukunut

---

### Post by OpsVentus on 2006-07-21
You can add Fedora in the menu.lst of grub.
If you've got grub on the second drive aswell, you can check the /boot/grub/menu.lst on the second drive how it wants to start Fedora. Then add these lines in /boot/grub/menu.lst of the first drive.
You have to make sure you replace any 'hd(0,0)' to 'hd(1,0)'.

If you have some doubt how to do this, post here both the menu.lst file's. Then we can tell you what to do.

Cheers,
Bart.

---

### Post by Bukunut on 2006-07-24
OpsVentus

Sorry for the delay and thank you for your help. 

Bukunut

---


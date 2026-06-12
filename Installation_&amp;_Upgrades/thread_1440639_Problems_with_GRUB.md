---
title: "Problems with GRUB"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by loon_zoldik on 2010-03-27
hi, well i used to have Windows XP Professional on my computer, then i decided to install Ubuntu but it didnt work for me it gave me really weird errors, i thought i uninstalled it, and then i installed Debian on my computer, Debian ran smoothly but when i tried to start Windows the GRUB from ubuntu appeared and when i tried to start windows again it showed and that the hal.dll was missing, i reinstalled Windows but still the same error appeared, this also affected my Debian GRUB so i had to install it again, i dont know what i should do in this case, can somebody help me? how can i delete ubuntu's GRUB for good? ive already formatted my windows partition but it keeps using Ubuntu's GRUB

---

### Post by MichaelSammels on 2010-03-27
Hey Loon,

If you have a LiveCD with Ubuntu on it, boot your computer from the LiveCD. Once in Ubuntu's Live Environment, browse to System -> Administration -> GNOME Partition Editor (gparted).

Using this, fully delete the disc which you want to put Windows XP on. If you use gparted to format this disc (erase the partition), it will also remove GRUB from the MBR.

Insert your Windows XP disc and when it asks how you wish to format it, please be sure to select "NTFS" and not "Quick Format". Hope this helps.

---

### Post by Herman on 2010-03-28
Your problem might not have anything to do with GRUB.

The Windows XP error message,
```
Windows could not start because the following file is missing 
  or corrupt:
  <Windows root>\system32\hal.dll.
  Please re-install a copy of the above file.
```Is usually caused by having the wrong partition number in boot.ini file.
You should check whether your Windows partition number has been changed somehow and if boot.ini needs editing.
I don't know why re-installing Windows didn't fix it thought, Windows should at least be smart enough to know what partition it's being installed in.

---

### Post by loonzoldik on 2010-03-28
well i think my computer has issues with ubuntu cuz it freezes when i try to run the CD from boot, i had to install it through Windows, i think that was the thing screw the whole thing, but yeah i dont know why the formattin didnt work, i didnt use the quick format cuz i know how dumb windows is

---


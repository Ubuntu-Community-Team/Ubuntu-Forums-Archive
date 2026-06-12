---
title: "Need help to restore grub"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by supravat on 2010-07-13
I have two operating systems installed in my computer. one is Windows XP( sp2 ) and another is Ubuntu Linux 10.04Lts. I reinstalled Windows XP. After rebooting, the grub menu is not displaying, only windows is booting, there is no sign of Ubuntu. Is there any way to restore the Ubuntu or I have to freshly install Ubuntu again ??

Please help me ...

---

### Post by wojox on 2010-07-13
Try and reinstall from a [LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

After you boot back into Ubuntu run 

```
sudo update-grub
``` 

and it should find Windows.

---

### Post by supravat on 2010-07-13
in that cas emy old Ubuntu will be deleted ... is there any way get it back ???

---

### Post by wojox on 2010-07-13
It won't delete Ubuntu. It will just reinstall Grub2 to the MBR.

---

### Post by supravat on 2010-07-14
can you tell me the exact sequence of commands..please

---

### Post by confused57 on 2010-07-14
See part #13 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---


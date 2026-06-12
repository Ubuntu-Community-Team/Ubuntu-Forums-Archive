---
title: "After using wubi it cant find .iso"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by kingdavidd on 2011-01-08
Hey guys im completely new to ubuntu my problem is i am running win7 and i used wubi and installed ubuntu 64 bit when i reboot to finish installation it says it can find the .iso and to chkdsk /r so i do that and check to make sure that it is there and the .iso is the right spot and it still doesn't work. Can someone please help me?

Thanks in advance.

---

### Post by bcbc on 2011-01-08
Place the wubi.exe and the .iso (unexpanded) in the same folder. Run wubi.exe from there. Don't install to a dynamic drive.

Once installed, don't update packages grub-pc and grub-common after installing (when Update Manager prompts you to install updates, check the "Recommended" list and uncheck these if you find them).

---

### Post by kingdavidd on 2011-01-08
> **bcbc said:**
> Place the wubi.exe and the .iso (unexpanded) in the same folder. Run wubi.exe from there. Don't install to a dynamic drive.

Once installed, don't update packages grub-pc and grub-common after installing (when Update Manager prompts you to install updates, check the "Recommended" list and uncheck these if you find them).
all i have done is ran wubi then it downloaded it then installed then it asked to reboot i did then selected ubuntu instead of win7 and it said can find the .iso any know its there.

---


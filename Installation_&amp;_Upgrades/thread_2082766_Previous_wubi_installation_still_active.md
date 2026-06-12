---
title: "Previous wubi installation still active"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by Ballaw on 2012-11-10
I was running Windows 8 prerelease and wubi. When windows 8 was released I upgraded. The wubi installation was having a lot of problems so I attempted to remove it. I couldn't uninstall wubi from "Add and Remove Programs" because it did not appear as an installed program. 

So I downloaded the Uninstall-Ubuntu.exe on the wubi website and ran it. It seemed to work but I still had to manually delete the C:\ubuntu folder. I installed wubi again, but the problem is that now two ubuntu installs appear on the boot menu. These don't appear as partitions so I'm not how to remove the old one.

I can't find any info at all about this. Any help or advice would be appreciated. 

Thanks!

---

### Post by darkod on 2012-11-10
That is the windows bootloader you are talking about, so you might find better information on windows forums or tutorials.

Basically you only need to remove the older entry (which you should have done before starting the second install so there would be no confusion).

I don't know in detail how editing the windows bootloader goes, especially for the new win8.

On another topic, wubi is just for a quick try, which more or less you can do with the ubuntu cd. Once you decide you like it, it's recommended to make a dual boot. I wouldn't have bothered with wubi at all. Being a linux inside windows will bring issues like this to you.

---

### Post by Frogs Hair on 2012-11-10
I don't know if this is helpful for Win 8.[http://askubuntu.com/questions/3257/how-do-i-remove-the-ubuntu-boot-option-created-by-wubi](http://askubuntu.com/questions/3257/how-do-i-remove-the-ubuntu-boot-option-created-by-wubi)

For future reference if you are unable to remove Wubi from add and remove programs, the uninstall- Wubi .exe is in the Ubuntu folder in Windows .Just  open the the folder and run it.

---


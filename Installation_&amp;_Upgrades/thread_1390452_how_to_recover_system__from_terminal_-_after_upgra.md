---
title: "how to recover system  from terminal - after upgrade to 9.10"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by doron387 on 2010-01-25
yo,
it's quite urgent.
i upgraded my system from 9.04 to 9.10 today.
it seemed fine but then i started to do some nonsense and messed up my system.
first, i opened the drivers updater and chose to activate the nvidia (183) - i think it was 183, for sure it was the new one.
since then i can't enter to my system, just have black screen with terminal in it.
how can i recover the whole installation from the terminal ?
what is the command (something that will compare my broken system with the newest kernel and distro and will fix all the mess that i did but without deleting my /home info and settings ?)

---

### Post by luks911 on 2010-01-25
Maybe you only have a problem with the graphics. To recover the graphic configuration, you have to go into the GRUB menu. For this, hold press the Shift key during the boot, then in the menu select the Recovery Mode, and finally choose an option to Reconfigure the X Server (I don't remember exactly how is called). After that, you will be able to use your Ubuntu, but without the Nvidia driver. All your data and configurations are there.

---

### Post by doron387 on 2010-01-25
thnx
i have just gave up and installing my customiso dvd of the old good 9.04
i hope that the installaion will work well and then i will upgrade to 9.10 again.
trynig to avoid doing nonsense as i did before.

so this thread is closed !

doron387

---


---
title: "boot-repair on a wubi install and now only windows 7 boots"
date: 2016-11-06
forum: Installation &amp; Upgrades
---

### Post by gingram on 2016-11-06
grub is messed up.  Ran default boot-repair and now only windows 7 is booting.

here is the details that boot-repair makes post attempted fix.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Suggestions on how to get things back to dual boot?

thanks

---

### Post by sudodus on 2016-11-07
Welcome to the Ubuntu Forums :-)

Please notice that wubi is no longer supported. When it was, it was made for ***testing*** Ubuntu. Wubi systems were never as stable as standard installed systems with Ubuntu.

One important reason why it was abandoned is that wubi does not work with preinstalled newer Windows versions, 8 and 10, which are installed in UEFI mode.

See this link: [Forums Staff recommendations on WUBI](https://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by yancek on 2016-11-07
> Never try to correct Wubi boot problems by reinstalling Grub2. This will prevent Windows from booting and will not fix the Wubi install. 

The quote above is from the official Wubi Guide at the link below.  When a wubi install is done, it creates an entry in the "windows" bootloader and adds the Ubuntu entry to it.  So you are booting from windows bootloader to Ubuntu.  Perhaps if you had indicated what the initial problem was someone could help.  Also, if you ran boot repair and selected the option to Create BootInfo Summary and posted a link to the output it might have helped.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by oldfred on 2016-11-07
Post the link to the Create BootInfo summary report. Is part of Boot-Repair (you posted link to Boot-Repair).
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by hakuna_matata on 2016-11-07
> **gingram said:**
> Suggestions on how to get things back to dual boot?

Theoretically, you can follow [this how-to]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/") . But probably, there are more issues than just a missing boot menu.

---


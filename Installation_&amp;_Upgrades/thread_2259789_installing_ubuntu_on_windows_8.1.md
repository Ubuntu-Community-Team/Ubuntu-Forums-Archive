---
title: "installing ubuntu on windows 8.1"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by deepika5 on 2015-01-07
[FONT=arial]i am unable to solve problem of boot repair while installing ubuntu on windows 8.1.when try code from internet on terminal windows. it shows recommened boot repair option. after clicking on that it shows a window in that it is written:[/FONT][FONT=arial]current session is in legacy mode. plese reboot the computer and use this software in an EFI session. this will enable this feature.[/FONT]
[FONT=arial]please help me installing ubuntu on windows 8.1pratform.[/FONT]
[FONT=arial]thanks [/FONT]

---

### Post by yancek on 2015-01-07
You say you are trying to install Ubuntu 'on' windows 8.  Does that mean you are using the wubi installer to install Ubuntu inside windows?  That won't work, see the link below.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you are trying to install Ubuntu on its own partition on a computer which has windows 8 software, your next step is to post the output you got running the boot repair, selecting the option to Create Bootinfo Summary.

---

### Post by oldfred on 2015-01-07
Pre-installed Windows is in UEFI boot mode.
You should always boot flash drive in UEFI mode, not BIOS/CSM boot mode.
Then you can install or run fixes to Ubuntu in UEFI mode.

UEFI should give two boot options for flash drive. You may have to turn secure boot off and enable USB port boot. Some systems require passwords to let you change those settings. But never lose that password if yours requires that.

What brand/model system? And what video card/chip?

---


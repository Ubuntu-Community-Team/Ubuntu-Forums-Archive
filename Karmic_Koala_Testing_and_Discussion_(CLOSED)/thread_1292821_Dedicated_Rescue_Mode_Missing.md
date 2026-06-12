---
title: "Dedicated Rescue Mode Missing"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rykel on 2009-10-16
Hi all,

I upgraded my Karmic and suddenly I cannot boot up my EeePC anymore.

The error is

> error: invalid environment block
Failed to boot default entries.
Press any key to continue,..


I tried using a Karmic USB disc to rescue the system, but it says

> There is no dedicated rescue mode on this disc. However, since the disc provides a complete user environment, it is possible to use the commandline and/or graphical tools provided to rescue a broken system...


So now I am stuck.. please help?

---

### Post by tekstr1der on 2009-10-16
Search forum?

[http://ubuntuforums.org/showthread.php?t=1285098&highlight=environment](http://ubuntuforums.org/showthread.php?t=1285098&highlight=environment)

---

### Post by rykel on 2009-10-16
Hi all,

Thanks!

Managed to solve my own problem...

[LIST=1]
[*]Write down the location of grub config file.. /boot/grub/grub.cfg
[*]Boot into a live CD environment;
[*]Open up /Computer/(disc)/boot/grub folder;
[*]Ctrl-L to highlight the actual location.. /(disc)/boot/grub/grub.cfg
[*]Open up Terminal;
[*]sudo chmod +w /(disc)/boot/grub/grub.cfg
[*]gksudo gedit /(disc)/boot/grub/grub.cfg
[*]Cross out "save_env recordfail".. # save_env recordfail
[*]Save File; and
[*]Reboot
[/LIST]

Yes, it is a hassle, but at least now the problem is SOLVED.

Hope that helps!

---


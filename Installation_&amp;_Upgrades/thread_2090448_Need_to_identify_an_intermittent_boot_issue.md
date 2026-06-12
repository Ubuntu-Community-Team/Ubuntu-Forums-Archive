---
title: "Need to identify an intermittent boot issue"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Skibicki on 2012-12-02
I would like help looking at a problem before making a new bug report.  This is the report from a Xubuntu 12.10 boot issue.  The report is sloppy and possibly miscategorized under 'xorg'.  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1081819](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1081819)
> Ubuntu 12.10 (Xubuntu)
HP p2-1033w - AMD E-300 with Radeon 6310 integrated graphics
My pc sometimes will not boot properly and will stay at a black screen with blinking cursor. It usually displays GRUB bootloader and boots normally. After disconnecting and reconnecting power, I am able to boot Ubuntu but the intermittent booting problem continues.

edit - log from Boot-Repair
[http://paste.ubuntu.com/1378561/](http://paste.ubuntu.com/1378561/)

Note I fully formatted the HDD and switched to Windows 7 Ultimate due to buggy HP Recovery software.

---

### Post by dino99 on 2012-12-02
you can remove "quiet splash" from the boot line :

sudo gedit /etc/default/grub

then

sudo update-grub

you will get all the verbose comments while booting, so its easier to identify an issue; but dont forget to glance at dmesg.log (/var/log/) and .xsession-errors into your /home (ctrl+h to unhide it)

---

### Post by Skibicki on 2012-12-02
Thanks. Xubuntu is not installed yet, if anyone has more tips to for booting please let me know. Could 'nomodeset' help?

---

### Post by Bashing-om on 2012-12-02
Skibicki; Hi ! Welcome to the forum.

Another thing you might do is edit /etc/init/tty1.conf to see boot messages: change is to /etc/init/tty1.conf. By default the virtual console logins clear the screen when they start; on tty1, this has the effect of erasing the last screen's worth of boot-time messages. To tell getty not to do this, we add --noclear to the exec line:

    exec /sbin/getty --noclear -8 38400 tty1
Remember: Make a backup of the current file prior to making the edit !

ctl+alt+f1 to get to tty1 login screen.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---


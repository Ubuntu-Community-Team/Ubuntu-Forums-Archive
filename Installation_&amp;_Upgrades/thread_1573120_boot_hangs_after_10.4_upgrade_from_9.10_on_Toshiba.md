---
title: "boot hangs after 10.4 upgrade from 9.10 on Toshiba laptop"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2010-09-12
I just used Update Manager to upgrade to 10.4 and all I get is the Ubuntu logo screen with the dots and then the screen goes black and there's no other response.  This happened after the upgrade completed installing and I received the message to restart the computer.  I have never been able to get it to boot.

I can boot fine by selecting the next older kernal although I do get some messages that I don't understand.  It all works so I presume it's OK.

The kernal that was installed with the upgrade is 2.6.32-24-generic and I've seen other posts about boot problems with it.  The laptop is dual boot with Windows XP and Windows boots normally.

I saw a suggestion on another thread about booting into an older kernal and then issuing the sudo update-intramfs -u -k  command.  I tried it and it didn't help.

Next I tried 2.6.32-24-generic recovery mode and I tried the option to fix damaged packages.  It seemed to do something although I saw error messages about not being able to find various software sources.  I tried a normal boot afterwards and same problem.  Recovery mode has another menu option about repairing grub but I don't want to try that.

I'm not a power user and this is all over my head.  Before I turn the laptop into an unusable door stop, can anyone help?

Thanks!

---

### Post by bob12564 on 2010-09-12
After hours of reading I found my solution here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---


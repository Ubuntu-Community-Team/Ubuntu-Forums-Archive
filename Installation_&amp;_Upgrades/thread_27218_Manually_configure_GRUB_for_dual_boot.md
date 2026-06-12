---
title: "Manually configure GRUB for dual boot?"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by [censored] on 2005-04-15
Hi. It appears I must have screwed up during the install process. I still have my windows partition, but grub doesn't recognise it.  That is, when I reboot and press ESC or ENTER (or whatever it is) at startup, the only options given to me are to boot up in linux.

How can I manually configure it so that I can boot into Windows?

---

### Post by andvaranaut on 2005-04-15
Hi censored,

If your Windows was installed as 99% of the people do (in the first partition of the first hard drive), a quick solution is to edit /boot/grub/menu.lst (ie. sudo gedit /boot/grub/menu.lst) and add the three following lines to the endo of the file:

title Windows
rootnoverify (hd0,0)
chainloader +1

Save and reboot. There should be a new option Windows in the menu.

If Windows refuses to boot, then you don't have windows installed in the first partition of the first hd (/dev/hda1). Ask again if you don't have any luck ;) and tell us where your windows is (HD and partition).

Cheers

---

### Post by [censored] on 2005-04-15
[QUOTE=andvaranaut]Hi censored,

title Windows
rootnoverify (hd0,0)
chainloader +1

Cheers[/QUOTE]

Thanks. Should that be

"rootnoverify (hd0,0)"

or 
"root noverify (hd0,0)"

---

### Post by andvaranaut on 2005-04-15
Hi censored,

it's rootnoverify - at least I have it this way here at home. It's got something to do with the fact that Grub is able to perform some tasks on behalf of the OS it is booting, such as loading an initrd (a special filesystem which is automatically loaded in memory when you boot Linux). The rootnoverify option essentially means 'boot the OS in this partition the exact way I tell you to and don't do anything special'. The 'chainloader +1' line tells Grub which bootsector to read and execute to boot up the system. As far as I know it is always +1 for the various Windows flavors.

If it's still not working, ask :) Maybe you have Windows installed elsewhere, or the Windows bootup sector has been damaged (it's easy to restore, though, but you need to set up Grub again after that).

Cheers

---

### Post by [censored] on 2005-04-15
thanx. All works better than a bought one.

---


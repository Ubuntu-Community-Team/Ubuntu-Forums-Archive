---
title: "new install puzzle"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by sprightlyone on 2008-05-17
hi i have placed my newly d/loaded in machine it loads to a window with **(initramfs)** +cursor what happens next???? obiviously a command of some kind .  is there some plain english step by step for new chums tahat don`t know any linux commands
thanks lyle

---

### Post by iaculallad on 2008-05-17
Trying to install Ubuntu in your PC? Normally, when you have a valid Ubuntu CD installer, it boots you to the option screen. From there, you have the option of trying the LiveCD or direct installation.

If you downloaded the ISO file, try checking its MD5 hash first before burning it using lower (4x) speed just to make sure that data is not corrupted.

Use this [Guide]("https://help.ubuntu.com/community/Installation")

---

### Post by Aearenda on 2008-05-17
Sounds like you need to try the all_generic_ide kernel parameter - see
[http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15)

Note that to do this on the liveCD you need to do this:
Accept your language
Press F6
Go to the very end of the line after "--" and add all_generic_ide after a space
Press Enter.

EDIT: I should add, there are other reasons why this may happen - if all_generic_ide does not fix it, search in the forums for "hardy busybox" and see if any of the other suggestions help.

---


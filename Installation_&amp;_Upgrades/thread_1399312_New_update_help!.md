---
title: "New update help!"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Ttomato13 on 2010-02-05
Hi everybody, I am new to using Ubuntu and love it very much, but the automatic update happened this morning. I let it do its thing, and then it needed to restart. After the restart the computer did not load Ubuntu, but went to a command prompt. Nothing I could think of helped to get it going into the OS. Is there something wrong with this update, or something I need to manually type at the command prompt to get this update to complete. Thank god for my lap top, I hope I didn't brink my desktop! Any help would be greatly appreciated!

---

### Post by Sef on 2010-02-05
1) What version of Ubuntu are you using?

2) What are your system specs?

---

### Post by andrewdvalles3 on 2010-02-05
I have the same issue.  I am using 9.10 (Karma Koala).

---

### Post by Cabs21 on 2010-02-05
try typing ```
startx
``` into command prompt

if that does not work try typing ```
login
``` then your username and password then try ```
startx
```

Last ditch effort idea I had is that you are in a CLI (Command Line Interface) not the GUI (Graphical User Interface) pres Ctrl+Alt+F7 or F8 or F9 to see if it brings you back to the GUI.

---

### Post by Ttomato13 on 2010-02-05
> **Sef said:**
> 1) What version of Ubuntu are you using?

2) What are your system specs?

I'm using Ubuntu 9.10, have it burned to a cd, but installed it through windows xp, and have a dual boot.

My system specs are a amd athelon 2.33ghz i beleive, with 1.5 gigs of ram. Its an older computer, but still runs great. Nvidia graphics card, onboard sound system. Usual stuff.

---

### Post by Ttomato13 on 2010-02-05
Cabs21, thanks for that try, but no dice, didn't work. If I typed login or startx it said missing file.
command prompt reads sh:grub>

I guess I can just uninstall it through windows and reinstall, but then when updated, the same issue will occur I feel.

---

### Post by Cabs21 on 2010-02-05
use your Live CD to boot and check your grub files on your HDD.  This sounds like a GRUB issue from the update.

---

### Post by Ttomato13 on 2010-02-05
yes it might, be while I am a new user, and really don't know how to mess with the os through the command prompt and such, I do not feel like really messing my computer up by doing something wrong as I have very important files through windows and such. Thanks for your help but I am just going to uninstall Ubuntu and try again from scratch. I'll ignore the updates for a while until this problem is fixed or new updates come out.

I am running an older lap top with the same version of ubuntu, and its the only OS on the lap top. No dual boot and no windows. Will this issue occur with the lap top as well?

---

### Post by Silvertones on 2010-02-05
If it's a WUBI install
[http://ubuntuforums.org/showthread.php?t=1398910](http://ubuntuforums.org/showthread.php?t=1398910)

---

### Post by Ttomato13 on 2010-02-06
Thank you, I will try it when I reinstall ubuntu another time, and if this happens again.

---


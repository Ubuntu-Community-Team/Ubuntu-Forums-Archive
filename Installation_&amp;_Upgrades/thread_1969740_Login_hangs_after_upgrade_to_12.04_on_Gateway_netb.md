---
title: "Login hangs after upgrade to 12.04 on Gateway netbook"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by DavidRonis on 2012-04-30
I upgraded my netbook to 12.04 this weekend.   It seemed to go without trouble and after rebooting I get the expected login screen.   However, when I entered my username/password (I also tried root's) and pressed login, nothing happens other than getting a rotating cursor.   Pressing esc gets me back to the blank login screen.    I've waited ca 1/2 hr to see if something would time out, but nothing did.

I can get to a terminal via crtl-alt-f#,   login  works just fine and the system seems stable otherwise.   I also tried reinstalling the gdm package, but that didn't help.

Any suggestions?

---

### Post by zdeuyo on 2012-04-30
> **DavidRonis said:**
> I upgraded my netbook to 12.04 this weekend.   It seemed to go without trouble and after rebooting I get the expected login screen.   However, when I entered my username/password (I also tried root's) and pressed login, nothing happens other than getting a rotating cursor.   Pressing esc gets me back to the blank login screen.    I've waited ca 1/2 hr to see if something would time out, but nothing did.

I can get to a terminal via crtl-alt-f#,   login  works just fine and the system seems stable otherwise.   I also tried reinstalling the gdm package, but that didn't help.

Any suggestions?

Hello,

I had the same problem, with a different laptop.

This seems to be a bug that the developers are working out.

The only solution I have found is boot for the Live CD or USB and reinstall 12.04 from there. Make sure to install updates while installing and third party. Also make sure while doing the reinstall, make sure to have it plugged in via ethernet if possible to prevent corrupted files.


_Here is the link for the thread I posted._

Link: [http://ubuntuforums.org/showthread.php?t=1967267]("http://ubuntuforums.org/showthread.php?t=1967267")


Also, if you have problems with grub after the install please use Boot-Repair.


_Guide found here,_

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")


Please let me know if this solves your problem.

All the best.

---

### Post by mskrzypczak on 2012-05-03
A link to a bug report:
[https://bugs.launchpad.net/lightdm/+bug/986967](https://bugs.launchpad.net/lightdm/+bug/986967)

---

### Post by DavidRonis on 2012-05-04
I found a work around.   Switching to kdm works (both lightdm and gnome do not).

Moreover, with a successful login other problem (e.g., loosing the ability to suspend/resume properly) seem to have vanished.

---


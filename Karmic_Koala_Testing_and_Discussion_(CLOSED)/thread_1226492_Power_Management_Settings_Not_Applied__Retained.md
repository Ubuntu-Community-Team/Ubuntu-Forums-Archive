---
title: "Power Management Settings Not Applied / Retained"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-29
Filed [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/406599](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/406599)

After today's updates to gnome-power-manager and devicekit-power settings found under System>Preference>Power Management are ignored after being set. After exiting Power Management, immediately opening it again will show the customizations just made, however, enacting a power event such as closing laptop lid will not only ignore the setting (does not suspend, though the option is selected), but will revert all settings back to default (check power management and see all settings reverted).

I was had hoped this update would have had the opposite effect and would fix suspend when laptop lid closed [Bug #44058]("https://bugs.launchpad.net/bugs/44058") Unfortunately, now the only way to suspend my system is through the battery applet or the shutdown menu. Keyboard (Fn-F1) and lid-closed are both broken.

Anyone else getting this?

---

### Post by cdEWoozy on 2009-07-29
> **tekstr1der said:**
> Anyone else getting this?

I just updated to g-p-m 2.27.2+git20090729-0ubuntu2 and don't have any problems changing settings, they are saved and applied.

---

### Post by lonniehenry on 2009-07-29
I can no longer suspend or hibernate and the choices are no longer offered in shutdown script.  still offered in power icon but doesn't suspend.  Lid close has no effect except to log off screen.

---

### Post by papangul on 2009-07-29
Same thing ^^ happened here also after today's update!

---

### Post by ghindo on 2009-07-30
> **lonniehenry said:**
> I can no longer suspend or hibernate and the choices are no longer offered in shutdown script.  still offered in power icon but doesn't suspend.  Lid close has no effect except to log off screen.Same here.

---

### Post by jppr on 2009-07-30
i doing... sudo aptitude update && sudo aptitude full-upgrade that remove devicekit and upgrade devicekit-power and gnome-power-manager

---

### Post by tekstr1der on 2009-07-30
If any of you confirming this on the thread could do so in the bug report as well with specific details or set "this affects me too", I'd appreciate it as the developer is saying he cannot reproduce this issue.

---

### Post by ghindo on 2009-07-30
> We have some more commits coming through over the next week (I believe 2.27.3-0ubuntu1 will be officially released Monday on Ubuntu). Let's try to test again once it is released. I'll leave it incomplete for now until we try against the newest release.Sounds like we just need to sit tight till Monday.

---

### Post by raronson on 2009-08-02
I had this problem and deleted the files in ~/.gconfd/, which reset my gnome power management preferences back to default.  From there I updated my preferences and restarted gdm.  Haven't seen the bug in a few days now.

---

### Post by ghindo on 2009-08-04
I'm still affected by this bug, even after the latest round of updates.  The bug can now be followed here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/407491](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/407491)

I haven't tried raronson's workaround, but I may just wait for this to be fixed upstream.

---


---
title: "Lost Hibernate/Suspend abilities"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aries K on 2009-06-27
Hi, has anyone else lost the option for the Hibernate, Suspend, etc.? When I click the red power icon all I see is Guest Session, Lock Screen, Log Out, Restart, and Shutdown. There are no options for putting the computer to sleep. Thanks in advance

---

### Post by zika on 2009-06-27
> **aries k said:**
> hi, has anyone else lost the option for the hibernate, suspend, etc.? When i click the red power icon all i see is guest session, lock screen, log out, restart, and shutdown. There are no options for putting the computer to sleep. Thanks in advance+1

---

### Post by Vanishing on 2009-06-27
> **zika said:**
> +1
There's another way to hibernating/Suspend.
If you enabled the little power management icon on the gnome bar, and you can click on the icon, you will see the two options.:D
As in for the quick-user-switch applet, the 2 options are still there for me..

---

### Post by tekstr1der on 2009-06-27
Not only are hibernate and suspend missing from my shutdown options, but the last few times I forced a suspend by using the keyboard shortcut, the notebook went into suspend mode, but would be a black or corrupt screen upon waking up. Unable to log back into session or do anything. Can't get to a virtual terminal from there and need to hard power-off system to reboot.

---

### Post by scradock on 2009-06-28
Confirm both the (new) loss of suspend/hibernate options in fast-user-switcher and the failure to resume from suspend even with correct video quirks, which has been going on for several days. ATI Radeon Xpress 200m (5955) video, AMD 64-bit.......

---

### Post by neferty on 2009-06-28
+1 confirmed. on a sony vaio vgn laptop.

---

### Post by durand on 2009-06-28
Confirmed on a Dell Vostro 1710 :(

---

### Post by lonniehenry on 2009-06-28
updates to acpi-support,libdevkit-power-gobject1, and devicekit-power should restore suspend/hibernate, power applet showing state problem.  Came through earlier today in the repos

---


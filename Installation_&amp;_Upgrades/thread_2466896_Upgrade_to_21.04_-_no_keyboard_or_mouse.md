---
title: "Upgrade to 21.04 - no keyboard or mouse"
date: 2021-09-09
forum: Installation &amp; Upgrades
---

### Post by garrickstaples on 2021-09-09
Hi All,

I did the upgrade on my Intel PC with an nvidia card from 20 to 21.04 last night. When it boots to the DM, the keyboard and mouse don't work (normal USB keyboard and mouse). I can't even switch to a VT and see what's going on. I was able to boot normally after purging all nvidia packages and booting to the previous 5.8 kernel.  Booting the new 5.11 kernel gets me a DM with no mouse or keyboard.

---

### Post by MAFoElffen on 2021-09-09
At BIOS Post, start hitting the left-shift key, so that the Grub Menu Displays...

When it comes up, press <E> key to edit the Grub Boot line. Use the down arrow until you get to the line that start's with "linux"...

Use the right arrow, until the cursor is where it says "quiet splash". Delete "quiet". Arrow right of "splash" and add "nomodeset"... 

Press <Cntrl><X> to boot...

You can either do this, or select and earlier kernel... At the Desktop, "Activities", type "Software & Updates"... Select it. Additonal Drivers Tab > Nouveau Driver...

Yesterday there was a Kernel Update for 5.11.0-34. It doesn't seem to want to play well with NVidia drivers, touchpads, keyboards, etc. My main desktop (with NVidia) is one of these also. Reinstalling the 3rd party NVidia driver with this Kernel does not seem to bring it back.

I'm sure they will have this sorted out soon. (Hopefully)

---

### Post by monkeybrain20122 on 2021-09-09
> **MAFoElffen said:**
> 
Yesterday there was a Kernel Update for 5.11.0-34. It doesn't seem to want to play well with NVidia drivers, touchpads, keyboards, etc. My main desktop (with NVidia) is one of these also. Reinstalling the 3rd party NVidia driver with this Kernel does not seem to bring it back.



Didn't work well with some intel machine either, kernel update had no problem on my Toshiba labtop, but touchpad behaved strange (can't move horizontally) on an old Inspiron laptop (also intel), so I just booted into the previous kernel and delete the updated one, problem solved. On my Nvidia laptop I have 5.11.0-7633 from system76's ppa and I guess it is really 5.11.0-33, no problem there.

---

### Post by garrickstaples on 2021-09-09
Thank you for the reply. As I said in my post, I was able to boot normally on the old kernel and nv driver.

I guess I just wait for a new kernel that hopefully works?

---

### Post by Frogs Hair on 2021-09-09
Normally the old kernels are deleted at the cleanup stage of the upgrade process if you follow all the upgrade steps. The fact that you have the old kernel indicates the the process maybe incomplete in some way.

---

### Post by monkeybrain20122 on 2021-09-09
> **Frogs Hair said:**
> Normally the old kernels are deleted at the cleanup stage of the upgrade process if you follow all the upgrade steps. The fact that you have the old kernel indicates the the process maybe incomplete in some way.

It will keep two kernels, the current one and the last one. If you have more than two then either you configure it that way or you don't run autoremove (AFAIK Ubuntu doesn't remove old kernels automatically like other distros such as Fedora or Arch, hence people with a /boot partition running out of space) or something is wrong. But two is normal.

---

### Post by Frogs Hair on 2021-09-10
> **monkeybrain20122 said:**
> It will keep two kernels, the current one and the last one. If you have more than two then either you configure it that way or you don't run autoremove (AFAIK Ubuntu doesn't remove old kernels automatically like other distros such as Fedora or Arch, hence people with a /boot partition running out of space) or something is wrong. But two is normal.

Auto-remove  is a choice offered during the cleanup part of the upgrade and is optional if upgrading from the GUI . I preformed the same upgrade a few weeks ago. The system should boot and run from the latest kernel if all went well during the upgrade.

---


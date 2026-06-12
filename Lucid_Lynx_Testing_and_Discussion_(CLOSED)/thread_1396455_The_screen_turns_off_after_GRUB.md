---
title: "The screen turns off after GRUB"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NCLI on 2010-02-02
Anyone with me on this one?
[URL="https://bugs.launchpad.net/ubuntu/+bug/515732"]
Bug report[/URL]

---

### Post by lucazade on 2010-02-02
You can try adding "acpi=off" to the kernel entry in grub.

---

### Post by amsterdamharu on 2010-02-02
I will post some more info from your bug report to make this thread a bit more informative than "it doesn't work-help me"
Ubuntu-Netbook-Remix 9.10 "Karmic Koala" - Release i386
This happens with kernels 2.6.32-11-generic, and 2.6.32-12-generic(The  latest kernel at the time of writing). It does not happen with kernels  2.6.32-10-generic and earlier, though it should probably be mentioned  that nothing but VESA has been able to get me to a GUI so far.


In /boot/grub/grub.conf remove the quiet splash from the kernel parameters and while the screen is black see if any of the other tty work control + alt + F1 through F7 or 8 (not sure because I skipped Ubuntu 9)


The grub.conf will be re-written when you run update-grub in a console.


Did you ever try to run xfix in recovery mode (the menu item under normal boot, one for every kernel version)? or X -configure, are there drivers available for your videocard under system -> administration -> hardware drivers?

---

### Post by jfernyhough on 2010-02-02
Sounds like an Intel graphics driver issue. Try booting with nomodeset.

---

### Post by NCLI on 2010-02-03
Nomodeset worked, thankfully. The bug still stands though.

> **amsterdamharu said:**
> I will post some more info from your bug report to make this thread a bit more informative than "it doesn't work-help me"
I would have thought posting the link to my bug report would be enough to disqualify a thread as one of those.

---

### Post by amsterdamharu on 2010-02-03
> I would have thought posting the link to my bug report would be enough to disqualify a thread as one of those. 	

You are right, sorry. I meant to say it would be easier to read if all the info was on one page.

Can you still only run vesa or is that solved too?

---

### Post by NCLI on 2010-02-03
> **amsterdamharu said:**
> You are right, sorry. I meant to say it would be easier to read if all the info was on one page.

Can you still only run vesa or is that solved too?

True, should've done that myself, but I was lazy >.>

Anyway, yes, the VESA thing is fixed too, it works perfectly, though the Netbook Launcher is still useless(Waaaay too slow).

---


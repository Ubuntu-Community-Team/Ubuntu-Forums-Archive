---
title: "Cannot boot windows XP after istalling ubuntu 8.04"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by sh4dyPT on 2008-10-25
Hello, I have installed ubuntu, and I think that MBR was installed in the same drive as windows XP.
Now when grub loader appears, after choosing windows Xp professional, it's return to grub loader again without showing any error. 
I'm new in Linux, and only know a few things about it.
Please help me, I really need both OS.


Any help will be appreciated.

---

### Post by ByteJuggler on 2008-10-25
When you choose to boot XP, do you see any indication at all that XP starts to boot before it reboots again?

---

### Post by sh4dyPT on 2008-10-25
Hi ByteJuggler,
No, I can't see indication that Xp start's.

Edit: the only thing I can see after choosing Xp, appears something like 
[B]Starting up.... 
Grub loader.... [/B]
after this it's return to grub loader. :s

---

### Post by caljohnsmith on 2008-10-25
If booting Windows sends you back to the Grub menu, that typically happens when Grub is accidentally installed to the boot sector of the Windows partition. If that is your case, you'll need your Windows Install CD to repair it; boot your Windows Install CD, go to the "recovery console", and run:
```
fixboot
```
If that doesn't work, it could be that Grub is not booting the correct partition or something like that. But give the above command a try and let me know if it makes any difference. :)

---

### Post by sh4dyPT on 2008-10-25
> **caljohnsmith said:**
> If booting Windows sends you back to the Grub menu, that typically happens when Grub is accidentally installed to the boot sector of the Windows partition. If that is your case, you'll need your Windows Install CD to repair it; boot your Windows Install CD, go to the "recovery console", and run:
```
fixboot
```
If that doesn't work, it could be that Grub is not booting the correct partition or something like that. But give the above command a try and let me know if it makes any difference. :)

I have used fixboot command but after this, error appears saying **NTLDR is missing**. I have reinstalled ubuntu, windows Xp drive is mounted, but has nothing there. Seems like I lost everything on that drive!

Thanks anyway ;)

---


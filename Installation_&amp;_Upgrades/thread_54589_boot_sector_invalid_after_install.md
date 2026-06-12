---
title: "boot sector invalid after install"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by illuminatus on 2005-08-05
hi guys,

i installed kUbuntu on my laptop as a second OS, but after installing grub i can't start because the boot sector is now invalid "Hard disk boot sector invalid" what can i do now?

How to reinstall grub?

XP and kubuntu should work properly.

thanks in advance.

cu Illuminatus

---

### Post by kosmic on 2005-08-05
[QUOTE=illuminatus]hi guys,

i installed kUbuntu on my laptop as a second OS, but after installing grub i can't start because the boot sector is now invalid "Hard disk boot sector invalid" what can i do now?

How to reinstall grub?

XP and kubuntu should work properly.

thanks in advance.

cu Illuminatus[/QUOTE]

If you have a LiveCD start it and go to a shell prompt :

then do fsdisk -l (has root)

and find the root partition (/) of the system instaled. lets supose it is /dev/hda5

then do

grub install --root-directoy=/dev/hd5 /dev/hd0 to install it to the MBR

---

### Post by bjpeters on 2005-10-19
howdy,

i have the same problem wih normal ubuntu and attempted to rectify this as per the instructions above. however, i'm new to any form of linux and was hoping you'd be able to spell out the instructions so i can copy them directly.

thanking you,

bill

---


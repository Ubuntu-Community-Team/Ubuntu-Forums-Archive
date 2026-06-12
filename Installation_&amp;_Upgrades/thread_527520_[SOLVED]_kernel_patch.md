---
title: "[SOLVED] kernel patch"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by leo_rockway on 2007-08-16
I don't know if this belongs to Installation & upgrade... if it is in the wrong place then please someone move it for me.

I am trying to apply the patch found in:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119457](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119457)

I never applied a patch before, so I have no idea what I'm doing. I tried "patch -p0 < dg-dell9400-pin-configs.patch" but I get:

> can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-source-2.6.22-2.6.22.old/sound/pci/hda/patch_sigmatel.c      2007-07-09 01:32:17.000000000 +0200
|+++ linux-source-2.6.22-2.6.22/sound/pci/hda/patch_sigmatel.c  2007-08-16 00:09:16.000000000 +0200
--------------------------
File to patch:

If someone can help me with this would be great.

TIA

---

### Post by ddrichardson on 2007-08-16
This is a patch for a patch. You need patch_sigmatel.c, kernel source (possibly) and the alsa source packages.

---

### Post by leo_rockway on 2007-08-16
> **ddrichardson said:**
> This is a patch for a patch. You need patch_sigmatel.c, kernel source (possibly) and the alsa source packages.

mmhhh... ok, i don't know if that task is up to my actual level of experience with linux. but i'll try and see if i can make it work (i'm planning to format my HD to get rid of XP anyway ... so if i make it work i'll take notes and if not then i won't be losing anything)

thanks for your help.

---


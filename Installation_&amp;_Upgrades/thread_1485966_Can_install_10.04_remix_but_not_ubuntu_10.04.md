---
title: "Can install 10.04 remix but not ubuntu 10.04"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by twomoons on 2010-05-17
I have a dell latitude d820.  Can install Ubuntu remix 10.04 fine with no problems whatsoever.  However, I've tried 4 times now to install the full blown 10.04 ubuntu desktop and keep on getting this error when it reboots after installation:

[    1.062342] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

it just hangs at that screen

any help please as it's driving me around the bend.

---

### Post by twomoons on 2010-05-17
ok, just tried installing 9.10

get this error:

uncompression error

--System Halted

:(

---

### Post by twomoons on 2010-05-17
anyone?

---

### Post by ronparent on 2010-05-17
You probably need to append a boot parameter to the kernel boot line in the grub menu (hit 'e' to edit the grub menu line). You could initially try **noapic nolapic**. A list of all the more common ones can be found in the menu of the live cd - under f6. Any one or combination of these parameters could fix you problem, Finding the right parameter(s) is trial and error. Good luck.

---


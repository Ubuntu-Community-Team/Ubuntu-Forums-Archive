---
title: "Upgrading kernel"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by bk452 on 2005-12-06
The upgrade thing says I can upgrade the following:

linux-386
linux-image-386
linux-restricted-modules-386
linux-restricted-modules-comm

Shoud I just go ahead and upgrade all 4 of them? Is this the kernel I would be messing with?

---

### Post by mcduck on 2005-12-06
yes, you can upgrade all four safely.

The older kernel version will still be available from grub menu if you have any problems with the upgraded one.

Also, what kind of prosessor you have? You might want to install kernel version optimised for your CPU, 'linux-686' for Pentiums or 'linux-k7' for Athlons.

---

### Post by metoo on 2005-12-06
Yes, all required. Well if you need something from the restricted-modules like nvidia or ati 3d drivers.
Just update all of them.
The first is probably pretty small, I assume it is a meta package just pointing to the second.

---

### Post by towsonu2003 on 2005-12-06
if you're using nvidia drivers (or any driver you had to compile yourself I believe), you will have to recompile tyhem after the update... there was a link to a page around here that said this, but I can't find it (not using any compiled drivers here) :)

---

### Post by bk452 on 2005-12-06
> or 'linux-k7' for Athlons.

Good to know.  I'm saving for an athlon 64.

---

### Post by bk452 on 2005-12-06
I hate tampering with something that's works great but security updates shouldn't be put off.  Thanks everyone.  If I run into trouble I know where to turn.

---


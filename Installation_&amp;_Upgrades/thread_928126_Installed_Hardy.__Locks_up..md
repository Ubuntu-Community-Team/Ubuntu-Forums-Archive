---
title: "Installed Hardy.  Locks up."
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2008-09-23
I saw various forum messages about lockups, but the dates spanned a long time so I can't tell if any of those would help me.

I just installed Hardy on a clean partition (my Gutsy install is on another partition and works fine).  After about 2 - 5 minutes, my system freezes.  I have to hard boot to do anything.

I am running a Dell Dimension 8100 (yes old machine).
Has 1.4Ghz Processor
512mb memory
NVidia Graphics (I selected enable on restricted drivers and it installed the package)

Any other information I can provide that might help?

Steve

---

### Post by Sef on 2008-09-23
> I just installed Hardy on a clean partition (my Gutsy install is on another partition and works fine). After about 2 - 5 minutes, my system freezes. I have to hard boot to do anything.

When it freezes, have you been using a particular application? (e.g., firefox, open office, etc.)

---

### Post by SteveF on 2008-09-23
> **Sef said:**
> When it freezes, have you been using a particular application? (e.g., firefox, open office, etc.)

The first time I was trying to download the latest updates.  It had started to download one package when it died.  The second time I was in user manager trying to add a user when it died after I clicked Add User.

The only thing I can think of that is consistent is both required me to enter the sudo password to get as far as I did.

Steve

---

### Post by SteveF on 2008-09-24
I read somewhere to try adding highres=off nhz=off irqpoll to my grub entry.  This did not help.  First time I opened Firefox, it locked up my machine (which also makes it seem that sudo is not the common item anymore).

Steve

---


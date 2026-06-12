---
title: "Can not boot Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2007-10-18
I just installed Gutsy new.  No problems were reported.  I tried booting into Gutsy and it hung after the splash screen appeared.  

My keyboard's caps lock and scroll lock start blinking and the machine is dead.  I have to hard boot to restart.

I removed quiet from the grub menu and tried again.  When the splash screen appears it dies on the line:
/scripts/init-premount

I looked for a /scripts directory to see hwat the script is doing, but I don't see it (don't see it in Feisty either).

any ideas?

Steve

---

### Post by Pumalite on 2007-10-18
You might need Alternate CD. Also follow this guide:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(make sure to do md5sum on iso and burn at 4x)

---

### Post by SteveF on 2007-10-18
Thanks for the reply, but what would really help is if I could spell.  I booted using the recovery mode and it stated that /scripts/init-premount worked fine.  I died on mounting root with a syntax error.  I relooked at the grub menu and saw I spelled UUID wrong.  Fixed that and booted no problem.

Steve

---

### Post by Pumalite on 2007-10-18
I'm glad you fixed it.

---


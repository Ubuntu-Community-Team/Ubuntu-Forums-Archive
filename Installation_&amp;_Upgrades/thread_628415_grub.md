---
title: "grub"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Eviltelm on 2007-12-01
Hi :)
I have a triple boot with windows xp, ubuntu gutsy and archlinux don't panic
I want to format my windows xp partition (wonder why? :D), however grub is installed in the mbr so i will lose grub right? what can I do to install grub after the format in gutsy's partition?
Thanks

---

### Post by sandysandy on 2007-12-01
> **Eviltelm said:**
> Hi :)
I have a triple boot with windows xp, ubuntu gutsy and archlinux don't panic
I want to format my windows xp partition (wonder why? :D), however grub is installed in the mbr so i will lose grub right? what can I do to install grub after the format in gutsy's partition?
Thanks

MBR as the name suggests is the Master Boot Record and so formatting the Win XP should not loose ur GRUB. However u can backup the MBR for safety. Also Super Grub Disk is quite useful for reinstalling GRUB.

regards

---

### Post by Pumalite on 2007-12-01
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Eviltelm on 2007-12-01
> **sandysandy said:**
> MBR as the name suggests is the Master Boot Record and so formatting the Win XP should not loose ur GRUB. However u can backup the MBR for safety. Also Super Grub Disk is quite useful for reinstalling GRUB.

regards

but grub is installed in mbr, so delete mbr and loose that grub part i think

i'm reading the link thought Pumalite, thanks ;)

---

### Post by Eviltelm on 2007-12-01
Ok, I found some guide, will format and try it when i have time :)
Thanks

---

### Post by Pumalite on 2007-12-01
Good luck.

---


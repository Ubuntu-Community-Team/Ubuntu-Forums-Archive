---
title: "How can I run a script automatically when Grub has been updated?"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2018-08-02
I have a script that must run immediately after Grub has been updated, e.g. after a kernel update.

How can I set that script to run automatically?

My thought was to use either [FONT=lucida console]incron[/FONT] or [FONT=lucida console]inotifywait[/FONT] to detect a change on some critical Grub file, wait until any running instance of [FONT=lucida console]dpkg[/FONT] has completed, and then run the required script.

Do you think that this is a good strategy?

[LIST]
[*]If so, which file (or files) should I watch, and should I use [FONT=&amp]incron[/FONT], [FONT=&amp]inotifywait[/FONT], or something else?
[*]If not, what do you suggest as a better solution?
[/LIST]

---

### Post by TheFu on 2018-08-03
Just an idea, but **dkms** is one method. I have no idea how it actually works, but that is how kernel modules get rebuilt/linked whenever the kernel changes.  It should also force an update-initramfs to occur too.
[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)

---

### Post by Paddy Landau on 2018-08-03
> **TheFu said:**
> Just an idea, but **dkms** is one method.
Thanks. Unfortunately, that goes above my head — it's way more complicated than I understand! :(
> **TheFu said:**
> …  It should also force an update-initramfs to occur too.
The problem is that the Grub update and initrramfs refresh are being done incorrectly. Thus, whenever Grub is updated, I need to run a script that fixes it.

(This is for [manual full-system encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), which currently works but needs manual intervention every time that Grub is updated. I need to automate this; all that needs doing each time is to run [the repair script]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot#Script_to_refresh_Grub").)

---

### Post by Paddy Landau on 2018-08-05
I've managed to make this work using incrontab. I have it watch /boot and the first-level files within it. As far as I can tell, it works perfectly.

---


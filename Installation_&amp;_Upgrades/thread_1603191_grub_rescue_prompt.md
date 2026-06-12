---
title: "grub rescue prompt"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by dondiego3 on 2010-10-22
I just tried to upgrade to the latest release through the update manager.  During the upgrade I told it to keep my old grub as I had issues the last time I upgraded.  I dual boot XP and Ubuntu.

When it told me to restart the computer I did and it boots to the following:

error:  the symbol  grub_xputs  not found.
grub rescue>

So I get a grub rescue prompt.  What do I do now?  I'm desperate for help as I need my computer!

I'm posting this with my sons mac book.

---

### Post by drs305 on 2010-10-22
The xputs command means that grub was not completely installed - parts of it are missing.

You can reinstall it via a LiveCD with chroot. Just running "grub-install /dev/sdXY" won't work. I wrote a guide on how to install via chroot:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If you continue to get a rescue prompt, you can also take a look at this link (make sure you read the "Have you tried..." which will take you to the above thread first).
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

If you have questions or problems you can post here.

---

### Post by drs305 on 2010-10-22
dondiego3,

Welcome to the Ubuntu forums!

The xputs command means that grub was not completely installed - parts of it are missing.

You can reinstall it via a LiveCD with chroot. Just running "grub-install /dev/sdXY" won't work. I wrote a guide on how to install via chroot:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If you continue to get a rescue prompt, you can also take a look at this link (make sure you read the "Have you tried..." which will take you to the above thread first).
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by dondiego3 on 2010-10-22
Thanks.  I tried the install via an upgrade.  I am downloading 10.10 right now and will make a CD and give your method a try.

---


---
title: "[SOLVED] Help! Upgrade process hung"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2008-08-16
Hi, everybody

I was finally updating to Hardy Heron from Gutsy, and, when it was almost done, it got stuck while generating locales.

I noticed that the root partition was almost full, and killed the upgrade window. I have emptied the partition a little (not much I could do, though), and restarted the process with "sudo dpkg --configure -a", but it still hangs at the "generating locales" part.

Is there anything I can do to skip this part and finish the whole thing?

Joan

---

### Post by Partyboi2 on 2008-08-16
[[COLOR=Blue]this [/COLOR]]("http://ubuntuforums.org/showthread.php?t=865679")might help.

---

### Post by cdtech on 2008-08-16
Try dpkg --configure -a using the recovery mode instead and see if that get you going.

---

### Post by linux_tech on 2008-08-16
[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

You can try using- 
chmod 644 /usr/bin/localedef
killall locale-gen

Ignore errors. If it does not continue, check if locale-gen has been killed (ps aux|grep locale-gen) and repeat "killall locale-gen" until it's gone.

When update-manager is done,

chmod 755 /usr/bin/localedef

---

### Post by skamarla on 2008-08-16
Thanks a lot, [this thread]("http://ubuntuforums.org/showthread.php?t=865679") had the solution.

The installation is back in track.

---


---
title: "problem with dual booting"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by technokiran on 2006-04-12
Haiii, Iam having dual booting system with windows xp and ubuntu-5.10 and now i got a problem with windows xp and i have to reinstall it. But when i do that the linux operating system is not going to work, then again i have to install ubuntu. 
                  Can any one help me of how to install windows xp in an ubuntu system.
Best regards,
kiran.

---

### Post by Sef on 2006-04-12
What you will need to do is reinstall grub, once you have reinstalled XP.

Read this post to reinstall Grub:

[http://ubuntuforums.org/showthread.php?t=158453&highlight=Reinstall+Grub]("http://ubuntuforums.org/showthread.php?t=158453&highlight=Reinstall+Grub")

---

### Post by Darkriser on 2006-04-12
once xp is installed, you'll be able to boot xp only.
there are several ways how to fix it:

- before xp installation, make a boot floppy from ubuntu. once xp is installed, boot ubuntu from floppy and install grub to MBR again.
- install xp. boot from ubutnu cd in rescue mode. install grub to MBR.

---


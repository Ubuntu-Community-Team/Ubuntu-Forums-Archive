---
title: "&quot;the following packages have been held back&quot; linux-generic etc"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by likes2skate on 2012-05-28
I switched to AMD64 kubuntu 12.04 precise at the beginning of the month.

Recently (over at least the past week), when I run apt-get update, I get this:

[INDENT]The following packages have been held back:
 linux-generic linux-headers-generic linux-image-generic[/INDENT]

Should I be worried?

What is going on? 

Thanks,

---

### Post by Old_Grey_Wolf on 2012-05-28
Those are kernel packages. sudo apt-get upgrade does not update the kernel. You need to use sudo apt-get dist-upgrade.

---

### Post by stoian on 2012-09-12
> **Old_Gray_Wolf said:**
> Those are kernel packages. sudo apt-get upgrade does not update the kernel. You need to use sudo apt-get dist-upgrade.

thanks a lot for this! i am running ubuntu since 2006, and this is the first time i had to do dist-upgrade for the kernel to get upgraded... funny, eh? i think it is time for me to move to a more simple distro...

---

### Post by Old_Grey_Wolf on 2012-09-12
:lolflag:

apt-get upgrade, apt-get dist-upgrade, and do-release-upgrade may not behave exactly the same way in some distros. 

If the distro uses incremental releases or the distro uses rolling releases, apt-get dist-upgrade can have dramatically different results.

Before using those commands with a distro, you really should research how the distro does upgrades and what those commands actually do.

If your system upgraded, please mark the thread as solved.

---

### Post by OmegaShadowwraith on 2012-09-13
Hi i have also been getting this message, but apt-get upgrade had always updated the kernel in the past but this is the first time i received this message. :?

---


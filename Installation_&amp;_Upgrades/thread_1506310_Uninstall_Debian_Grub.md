---
title: "Uninstall Debian Grub"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by The Thunder Chimp on 2010-06-10
Hi and thanks for taking the time to read,

Back in April, I installed Debian on my computer. I used it seldom. The Grub2 that showed up upon boot was, however, Debian's Grub. I tried to install xPud on my computer, but there are no way of doing that except by putting it in the Ubuntu Grub somewhere. However, since the Debian Grub2 is the one running my computer, installing it in the Ubuntu Grub2 isn't doing anything at all. My friend has managed to boot in xPud via the command line. I uninstalled Debian today, and the Grub2 with the Debian background is still there, and "sudo grub-update" if ran in Ubuntu, removed Debian from the Grub2 list.

 Why isn't xPud in the Grub2's list?

---

### Post by The Thunder Chimp on 2010-06-12
Bump

---

### Post by darkod on 2010-06-12
Are you booting grub2 from ubuntu or not? Grub2 from ubuntu needs to be on the MBR of the disk so when you boot it shows the grub menu from ubuntu.

---

### Post by The Thunder Chimp on 2010-06-13
I'm pretty sure it's booting from Ubuntu because why Debian partition doesn't exist anymore (it's still the Debian Background on the Grub2 splashscreen though).

---

### Post by darkod on 2010-06-13
I don't know about the splashscreen but if the debian partition is gone, you are right, it must be the ubuntu grub you are using. Otherwise it wouldn't work at all.

Maybe the image got integrated somehow in ubuntu grub also?

For more details about your boot process you can run the boot info script from the link in my signature. If you need instructions how to do it, here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You can run it from hdd installation too, not only from live mode. But that post is written with live mode in focus.

The results file will have detailed info what are you running and from where.

---


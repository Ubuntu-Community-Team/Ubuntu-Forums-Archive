---
title: "Installation failed"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by grany on 2007-05-23
Hello,

I was upgrading to Feisty 7.04 with the official method - ' gksu "update-manager -c" ', but it failed somehow. When I now try to reboot my system, with the earliest Kernel (2.6.17-10-386), it sticks in the boot process, and returns the error "Boot failure /bin/sh: can't access tty: job control turned off". By pressing Ctrl+Alt+F1, the message is: "ALERT! /dev/disk/f4191ab2...... does not exist. Dropping to a shell."
If I try to reboot it from Grub with an earlier Kernel (2.6.15-23-386), it sticks in Checking file systems.

So, it seems that it mixed up some links to the file systems, but how can I repair this?

I tried to reboot from Live-CD, and it worked fine. Is it possible to re-install or repair my latest installation from there? I am a little worried about loosing data because of the partition manager that appears.

Thanks for any hint. As you can see, I am not really familiar with this story.

Greets!

---

### Post by mikewhatever on 2007-05-23
Personally, I was never too confident with upgrading, owing to the fact that people customise their desktops so much. Where (on which partition) is the data you wish to keep? Have you backed up?

---


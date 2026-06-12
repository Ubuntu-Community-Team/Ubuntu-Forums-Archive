---
title: "10_linux deleted (grub2)"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by ironmaiden943 on 2010-11-27
Hi, I deleted the 10_linux by accident while trying to make grub2 recognize my Windows 7 partition. Now when I run update-grub it only outputs: 

"Adding Windows
Found memtest86+ image: /boot/memtest86+.bin
fdone"

and does not show the linux partition. Does anyone know how to replace the file, I'm afraid of turning off the computer and being unable to boot into ubuntu.
Thanks

---

### Post by ironmaiden943 on 2010-11-27
bump

---

### Post by ironmaiden943 on 2010-11-27
anyone?

---

### Post by lmarmisa on 2010-11-27
What is your version of Ubuntu?

---

### Post by lmarmisa on 2010-11-27
I attach the file /etc/grub.d/10_linux corresponding to Ubuntu 10.10 (remove the .txt extension, please).

---

### Post by ironmaiden943 on 2010-11-27
thank you, problem solved

---


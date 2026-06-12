---
title: "Server installation fails to install GRUB"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Aramaki on 2010-04-08
Hi everyone!

While installing Ubuntu Server 9.10 I seem to have problem with installing GRUB. The whole installation process runs fine, no problems at all. But when it comes to the part where GRUB is installed the installation process returns to the "Ubuntu installer main menu". If I choose to install GRUB it doesn't return any error, it looks like it starts to install the package and then it returns to the "Ubutnu installer main menu". Choosing to finish the installation also returns to the same menu. 

To be honest I don't have a clue to what could be wrong: I haven't seen any error message, I've tried to just redo the process but the problem reoccurs again and I haven't been able to Google any similar cases.

Anyone got any ides (they don't have to be good, worst case I'll learn something new ;)) how to find what is causing the problem?

Best regards A

---

### Post by prodigy_ on 2010-04-08
Well, you can boot from Live CD and check if you'll be able to chroot into the newly installed OS. Then you can try to install Grub manually.

---

### Post by Aramaki on 2010-04-08
Smart! Thanks prodigy_! I'll give it a try :)

---


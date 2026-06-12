---
title: "Asus M2N68-Plus - Ubuntu not goes in shutdown or restart"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by DjDiabolik on 2012-04-04
Hi boys.. i have installed Ubuntu 11.10 on this Motherboard..... it's all ok.... but when i try to Shutdown my PC ubuntu goes in crash!

On screen i can view the image Ubuntu with five white point and nothing append... at this point i need to shutdown or restart manually!

From Terminal if i use "sudo reboot" or use "sudo shutdown" all working without problems:
"sudo reboot" working ever... "sudo shutdown" not ever.....

I have read so other post over internet and i have edited my grub file to put this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
GRUB_CMDLINE_LINUX=""
```

But it's not a solution... you can help me ?

---


---
title: "Feisty, WinXP, Vista, and dual booting"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by ronald_stall on 2007-05-26
I am trying to anticipate what I am about to get into, so if anyone has an experience please share it. 

I am dual booting WinXP and Feisty using the Grub bootloader. I am going to upgrade WinXP to Vista while running in WinXP. Has anyone had this experience and did it screw up your Grub Bootloader menu and if so how did you correct it?

Thanks in advance

---

### Post by jba6511 on 2007-05-26
well i can offer a little help here. When I was dual booting between xp and vista, I had xp installed first, created a partition for vista and then installed vista into that partition. Vista overwrite the boot files from xp so that the vista bootloader appears at startup to allow you to select between OS. Then I partitioned a space for ubuntu and installed. GRUB then took over from here. Sorry I can not be of more assistants.

---


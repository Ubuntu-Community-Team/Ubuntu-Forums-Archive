---
title: "dual boot problem/bios priority"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by noname2k on 2006-02-21
Hi,
I have an IDE hard drive with nothing on and an 80gig SATA hdd with windows on. In the bios the IDE takes priority over SATA in the boot order. If I was to install linux ubuntu on the IDE which hard drive should take prioroty? Because when I previously tried it with this configuration with suse I could load Linux suse from GRUB but not windows (the option was there but it wouldnt load). Any ideas on the matter would be great.
Thanks,
noname2k

---

### Post by lha on 2006-02-21
[QUOTE=noname2k]Hi,
I have an IDE hard drive with nothing on and an 80gig SATA hdd with windows on. In the bios the IDE takes priority over SATA in the boot order. If I was to install linux ubuntu on the IDE which hard drive should take prioroty? Because when I previously tried it with this configuration with suse I could load Linux suse from GRUB but not windows (the option was there but it wouldnt load). Any ideas on the matter would be great.
Thanks,
noname2k[/QUOTE]

I'd prefer booting from IDE. Grub can boot Windows from that other drive. Usually installer automatically adds an entry for Windows. If you run into trouble, come back here and I'll try to help.

---

### Post by noname2k on 2006-02-21
Thanks, I'll try it.

---


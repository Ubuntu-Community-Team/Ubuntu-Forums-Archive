---
title: "Ubuntu server get error on update."
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by jonizen on 2012-04-30
[FONT=Times]Hi, i get errors on update. I googled the "Sub-Process /usr/bin/dpkg returned an error code (1).

And i did the command: [/FONT]
  **[FONT=Courier]> sudo dpkg --configure -a[/FONT]**[FONT=Courier] StÃ¤ller in linux-image-2.6.32-41-server (2.6.32-41.88) ... Running depmod. update-initramfs: Generating /boot/initrd.img-2.6.32-41-server Running postinst hook script /usr/sbin/update-grub. /usr/sbin/grub-mkconfig: 109: /usr/sbin/grub-probe: not found User postinst hook script [/usr/sbin/update-grub] exited with value 127 dpkg: fel vid hantering av linux-image-2.6.32-41-server (--configure):  underprocess installerade post-installation-skript gav felkod 127 dpkg: beroendeproblem fÃ¶rhindrar konfigurering av linux-image-server:  linux-image-server Ã¤r beroende av linux-image-2.6.32-41-server, men:   Paketet linux-image-2.6.32-41-server har inte konfigurerats Ã¤nnu. dpkg: fel vid hantering av linux-image-server (--configure):  beroendeproblem - lÃ¤mnar okonfigurerad dpkg: beroendeproblem fÃ¶rhindrar konfigurering av linux-server:  linux-server Ã¤r beroende av linux-image-server (= 2.6.32.41.48), men:   Paketet linux-image-server har inte konfigurerats Ã¤nnu. dpkg: fel vid hantering av linux-server (--configure):  beroendeproblem - lÃ¤mnar okonfigurerad Fel uppstod vid hantering:  linux-image-2.6.32-41-server  linux-image-server  linux-server[/FONT]
  [FONT=Times] 
But i cannot find any way of solving it.
I had my server running for weeks then i buy mistake hit the power switch to and power adapter and it died, and when i restart it i had a line in my dev list that i fixed and after that i realized that rsyslog and ssh is not working at all. I tried to upgrade and this is what i got.

Can anyone help or assist me?[/FONT]
  [FONT=Times] [/FONT]
  [FONT=Times]Regard[/FONT]
  [FONT=Times]Jonathan[/FONT]****

---

### Post by jonizen on 2012-05-01
I have solved it, i just had to reinstall grub, and after the installation all my errors disapear! But my ssh still did not work but i just removed it and then reinstalled it and now it works to!

---


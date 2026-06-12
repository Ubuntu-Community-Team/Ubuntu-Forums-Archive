---
title: "XServer doesn't start"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by sandman94 on 2008-02-06
Hello,

I've tried recently to install Gutsy on my computer, and the installation went pretty ok (Alternate Install DVD),
but when I rebooted, where gdm was supposed to start, I had a black screen. Sound works, but the screen stays black. What can I do ? Is my xorg.conf wrong ?
I have a 19" TFT-Screen from Medion and an iGMA 900.
What can I do ?

Thanks in advance,

Sandman

---

### Post by marufaberlin on 2008-02-06
Try this:

Stop the X sever
run dpkg and reconfigure X

that should recreate your xorg.conf

---

### Post by marufaberlin on 2008-02-06
Then a wizard should come up where you can configure your X Server.

---

### Post by marufaberlin on 2008-02-06
PS.: Does  sudo startx work?

---

### Post by marufaberlin on 2008-02-06
Tip: run /etc/init.d/gdm stop
CTRL + ALT + BACKSPACE restarts gdm!

---


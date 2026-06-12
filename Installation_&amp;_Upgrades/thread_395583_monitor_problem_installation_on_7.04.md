---
title: "monitor problem installation on 7.04"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by tanozfood on 2007-03-28
Hello,
I have downloaded live-cd of the new ubuntu release 7.04 and I want to try on my pc.
However, x server does not found the correct timings so the monitor goes repeatly in
stand-by. When I tried the current version (6.10), what I did is ctrl+alt+backspace, go
to command line and modify the /etc/X11/xorg.conf file. After that, I switched to ctrl+alt+f7 and all was ok.
With this version, however, no terminals appears in alt+f1..alt+f6, so there is no
possible to get a command line. I try to press esc at startup menu, the answer of the
installer was : "leaving graphical to go to textual mode", more or less, but after it proceeds
as the graphical mode (i.e. try to launch x server).
What should I do?
Thanks,
                       tano

---

### Post by goghgoner on 2007-03-28
At the start up screen you should be able to push F6 to get to kernel options. Then enter the code below
```
chroot /root nano /etc/X11/xorg.conf
```
save and exit xorg.conf and then press CTRL-D to continue booting. 

This thread has pictures and stuff [https://wiki.ubuntu.com/EdgyKnownIssues/59618]("https://wiki.ubuntu.com/EdgyKnownIssues/59618")

---

### Post by tanozfood on 2007-03-28
Not works. The pc hangs with something like "Spurious ACK" messages.
Should I *replace* the boot options or *add* to the boot options?
However, I try a little in various way, and seems not to be a good solution..

---

### Post by tanozfood on 2007-03-28
Now it works. The code you entered lacks of somethings that is included in the link.
However, great job.
Thanks!!

---


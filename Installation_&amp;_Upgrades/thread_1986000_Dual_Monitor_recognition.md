---
title: "Dual Monitor recognition"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by freshminted on 2012-05-24
I installed a fresh Ubuntu 12.04 onto my HP Pavilion (Entertainment)  laptop. It all went superbly, with one exception (so Far). In System Settings > Displays, the system fails to find my external HP LP2465 monitor. It is not using the HDMI but is using the standard cable connection.

Currently my other HO laptop (Pavilion dv6)  with Ubuntu 11.10 recognises and starts the monitor, albeit the screen position needs to be adjusted after each start-up.

The monitor is only ever connected to one laptop or another, never both simultaneously.

Can the laptop use its HDMI to link to the monitor which has all the right sockets?

Thank you for any advice on this

---

### Post by dino99 on 2012-05-24
which graphic driver is used ? is it activated ? (sudo jockey-gtk)

and you should watch the ~/.xsession-errors log inside this hidden /home file (ctrl+h to unhide it), and /var/log/ too.

---


---
title: "upgrade 9.10 and my computer can not start in a graphics mode"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by irondon on 2009-11-14
[B]Hi 
I am a primer in Linux. I would like someone can help me.

I was upgrade my Linux to 9.10 , the installation in my computer was not succesfully at all. Because I can not start my computer in a graphics mode.

What can I do. Please any suggestion let me know.

[/B]

---

### Post by optimisteo on 2009-11-24
Hi,

Try:

 sudo dpkg-reconfigure -phigh xserver-xorg

this will reconfigure your xorg.conf


Regards,

---


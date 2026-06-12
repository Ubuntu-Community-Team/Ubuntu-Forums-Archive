---
title: "Unable to install &quot;module-assistant&quot;"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Seeb on 2007-01-14
SOLVED!

Hi, 

I followed the instructions ( [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) )
to install my X1300 video card with the original ATI drivers, cause I want to use hibernate.

When applying this...: "sudo aptitude install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-$(uname -r) "

..it says that there is no module-assistant paket. I enabled all multiverse/universe things
in my sources.list and already tried another mirror but it doesnt get this
module-assistant which I need to complete installation.


Can anyone help me? Thanks!

---

### Post by Seeb on 2007-01-15
Hello help? :(

---

### Post by eightballd on 2007-01-22
Your edit to your original post says you solved this?   How?   I'm having the same problem (same video card too BTW)

---

### Post by eightballd on 2007-01-23
Nevermind, I see now..... the package is in the universe repositories

---


---
title: "anyone with little knowledge of GRUB scripting can help!"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-10-01
so a guy with the same problem as me said that all he did to make the resolution work and everything was do this
"changed the entry to not load the splash screen (remove the word splash). I get the same issue (let me guess, amd64?)."

ok how do i do that? n00b help here since i dont know ubuntu scripting (never used linux b4) only windows scripting knowlegde....

so can anyone give me what scripts to type in after i press C in grub?

---

### Post by maybeway36 on 2007-10-01
Edit /boot/grub/menu.lst, and change all the instances of "quiet splash" to just "splash".
You should be able to boot with recovery mode if you need to.

---

### Post by twist2b on 2007-10-01
kk thanks..... ill try that! be back in like an hour with my results!

---


---
title: "Loading module at boot time"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by DarkBabar on 2006-09-24
I just built a module from source, and now I'm wondering how to make it load at boot time. I copied it into the directory where the other modules reside, but it's not showing up when I do 'modprobe -l'. What should I do?

---

### Post by angkor on 2006-09-24
I think you can add the name of the module to the /etc/modules file.

---


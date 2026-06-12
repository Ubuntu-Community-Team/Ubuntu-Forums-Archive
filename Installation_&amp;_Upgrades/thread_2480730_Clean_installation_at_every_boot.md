---
title: "Clean installation at every boot"
date: 2022-11-08
forum: Installation &amp; Upgrades
---

### Post by alessio89g on 2022-11-08
Hi,
I need to configure a dual boot system, with Windows and Ubuntu. I need that Ubuntu remove any modification (file, program or setting applied during its using) at shutdown, so when I boot again in to it, I find a factory resetted system; I mean like when you boot with a live USB and any modification is temporary.
There is any way to get this, with an installation in to the hard drive and without the need to select anything (try or install and language) except what OS to boot?

---

### Post by ActionParsnip on 2022-11-08
Select guest session at login

---

### Post by alessio89g on 2022-11-08
Thanks for answer.
Can we automate the login as guest?

---

### Post by ActionParsnip on 2022-11-08
Sure. You can set gdm to autologin as guest when it loads. Just edit /etc/gdm/custom.conf

---

### Post by alessio89g on 2022-11-08
> **ActionParsnip said:**
> Sure. You can set gdm to autologin as guest when it loads. Just edit /etc/gdm/custom.conf
Thank you very much!

---


---
title: "automatically run script after kernel update"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by justin.matthews on 2010-09-12
Hi.

I'd like to have my own script be executed automatically after doing a Linux kernel update. Is there somewhere i can link into this process that isn't touched by the update itself? The purpose of this idea is to try automate the installation of sound (alsa 1.0.23-2) and video drivers (nvidia from website) that i typically need to do after every kernel update.

Thanks.

---

### Post by Marcelo Ruiz on 2010-09-18
Try to create a bash script and put it in /etc/kernel/postinst.d/
Hope it helps! 

Marcelo.

---

### Post by Marcelo Ruiz on 2010-09-18
Try to create a bash script and put it in /etc/kernel/postinst.d/

Also, take a look here: [http://www.edugeek.net/forums/scripts/47778-script-update-manually-installed-nvidia-drivers-after-kernel-updates.html](http://www.edugeek.net/forums/scripts/47778-script-update-manually-installed-nvidia-drivers-after-kernel-updates.html)

Hope it helps! 

Marcelo.

---

### Post by justin.matthews on 2010-09-20
Cheers mate - that's exactly what i was looking for.
That link was a nice find.
justin

---


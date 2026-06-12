---
title: "Configure Sound After Minimal/Custom Install"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by spooky655 on 2008-10-04
I did a hardy cli install not too long ago and tried to get a lighter ubuntu by just installing essentials (gdm, gnome, synaptic, xorg, firefox, etc.). That worked out fine and I noticed a speed increase, but, unfortunately, my sound wasn't working. I tried installing every sound package from a regular ubuntu install to no success. I was wondering how to configure sound like the CD seems to do when I do a normal install from that.

---

### Post by Girya on 2008-10-04
> **spooky655 said:**
> I did a hardy cli install not too long ago and tried to get a lighter ubuntu by just installing essentials (gdm, gnome, synaptic, xorg, firefox, etc.). That worked out fine and I noticed a speed increase, but, unfortunately, my sound wasn't working. I tried installing every sound package from a regular ubuntu install to no success. I was wondering how to configure sound like the CD seems to do when I do a normal install from that.

Have you checked to see that sound is not muted in alsamixer?

in a terminal type: alsamixer and you can adjust levels from there. It might not be your problem but its easy to check

---

### Post by spooky655 on 2008-10-05
Well, I had tested building up from a base install on both a virtual machine and a desktop and I'm pretty sure I tried unmuting it, as well as installing multiple packages suggested from different forums. I don't have it install at the moment so I can't really test anything. I just thought if there was something that you had to do that I didn't know about, it would be great if someone could tell me. But there must be a lot of people who build their install from a base install so it should be common knowledge shouldn't it? Unless it just me. But if the CD can get it working, then why can't I?

---

### Post by spooky655 on 2008-10-05
bump

---

### Post by spooky655 on 2008-10-05
I just thought of something. Is it possible that everything was installed and configured properly, but there's some service that doesn't start up by default that you need for sound?

---

### Post by spooky655 on 2008-10-05
bump

---


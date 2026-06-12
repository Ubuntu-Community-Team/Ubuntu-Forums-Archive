---
title: "Upgraded 10.04 to 10.10, unable to boot normally"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Quadunit404 on 2010-10-10
I had upgraded Ubuntu 10.04 (which had worked fine) to 10.10 and now if I try to boot normally, I see the "Ubuntu 10.10" text and startup meter... thing for only about a second, then it becomes a pure purple screen and all disk activity stops. I can still boot through Recovery mode with a failsafe X session and Windows (my other OS) can still boot. Along with that my desktop wallpaper is completely white. My PC is an Acer Aspire 4530-6823 with an AMD Athlon 64 X2 QL-62 dual-core processor clocked at 2GHz, a NVIDIA GeForce 9100M G and has a dual-boot between Windows 7 and Ubuntu 10.10 set up.

I'd like some help here, thanks (and yes, I know my way around Linux)

---

### Post by Quadunit404 on 2010-10-10
Hello? Anyone?

---

### Post by dino99 on 2010-10-10
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

be sure you only use maverick repo, check it: synaptic repo tab
(take care of third party and exotic ppa if any)

---

### Post by Quadunit404 on 2010-10-10
I tried that and it works. I can't use the NVIDIA graphics settings though (meaning temporarily no Compiz)

I'll post that in the appropriate section.

---

### Post by cariboo on 2010-10-10
Have you installed the restricted nvidia driver from System->Administration->Additional Drivers?

If you don't want to use the restricted drivers, you can get 3D with the nouveau driver by installing libgl1-mesa-dri-experimental from the repositories.

---

### Post by Quadunit404 on 2010-10-10
I installed the drivers from NVIDIA's site and now I have Compiz working again. No NVIDIA X Configuration, though :|

---


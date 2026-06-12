---
title: "Manually edit dpkg/status, thoughts?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by LaserGuidedStefan on 2008-01-24
ng,

I've experienced some major problems with a 3rd party package. I'm using a Brother MFC-8440 printer, and I installed the mfc8440lpr package from the [brother linux driver homepage]("http://solutions.brother.com/linux/en_us/index.html"). This package was 'in a very bad state' when I tried to 'dpkg -i' it. It never actually installed, but it messed up apt-get/synaptic. I couldn't install/update/upgrade anything. Apt-get said I needed to reinstall the mfc8440lpr package... I did *everything* to resolve the matter. As a last resort I took the advice from an online poster and edited '/var/lib/dpkg/status' by hand. I ruthlessly removed the entire paragraph in the file that referred to the faulty package. And after a 'dpkg-reconfigure -a' everything works, to the best of my knowledge, fine.

Now my question; how do you pros out there stand on the issue of manually editing '/var/lib/dpkg/status'? Is it always a bad idea? I'm afraid that I messed things up galore. Could anyone give me some comfort?

//s

---

### Post by Pumalite on 2008-01-24
It lets you use apt-get again, install etc, but the mess is left behind. It's a 'fix'

---


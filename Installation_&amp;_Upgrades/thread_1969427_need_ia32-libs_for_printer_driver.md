---
title: "need ia32-libs for printer driver"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by magicman5421 on 2012-04-30
I currently own a Brother HL-2240D printer. There are no drivers for it in the printer dialog, but Brother has a very good site full of missing drivers with installers. When I first installed my printer I was using 10.04 and the installation instructions said to install either ia32-libs or lib32stdc++. I installed ia32-libs and everything was fine. I just upgraded to 12.04 and I noticed it removed ia32-libs. Trying to print now fails. I removed the printer and its drivers and attempted a reinstall, but it refuses to because the Software Center says "Dependency is not satisfiable: libc6 (>=2.3.4-1)". I've attempted installing lib32stdc++. It didn't help. How do I get this version of libc6 installed?

---

### Post by dino99 on 2012-04-30
install ia32-libs-multiarch from synaptic

and you might search for "brother" inside synaptic, lot of drivers are there

---


---
title: "how can I install older C++ compiler (gcc-4.1.2 or gcc-4.2.1) on Ubuntu 12.04 LTS ?"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by Gunnnn on 2012-09-29
I have to run application based on Geant4 simulation (from geant4.cern.ch). The application was created using older version of geant4 (version 9.2) which requires that my Linux have C++ compiler also in old version. And the suitable versions are gcc-4.1.2 and gcc-4.2.1. But at the moment I have Ubuntu 12.04 LTS and it has gcc 4.6 or something. How can I install older version of gcc ? Or should I install just older Ubuntu (say 10.04 LTS ?)?

---

### Post by slooksterpsv on 2012-09-29
> **Gunnnn said:**
> I have to run application based on Geant4 simulation (from geant4.cern.ch). The application was created using older version of geant4 (version 9.2) which requires that my Linux have C++ compiler also in old version. And the suitable versions are gcc-4.1.2 and gcc-4.2.1. But at the moment I have Ubuntu 12.04 LTS and it has gcc 4.6 or something. How can I install older version of gcc ? Or should I install just older Ubuntu (say 10.04 LTS ?)?

Technically you could uninstall gcc-4.6.x and download the deb for gcc-4.2.1 but it should compile fine under 4.6.x - may have to test out. Are you using a build script or just running gcc on the main.c file?

---


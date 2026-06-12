---
title: "Status error on Package Installer"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Tropical Joe on 2010-06-12
Hello, I'm relatively new to Ubuntu and have little knowledge about this, hope you can help. While downloading an aMSN packcage for an Intel x86 machine (I386)  I get this message: 

Error: Dependency is not satisfiable: libgssdp-1.0-1 (>= 0.6.4)

Can you give me some advice on what to do? It'd be much appreciated.

Using Karmic Koala, BTW.

---

### Post by labinnsw on 2010-06-13
Search for GObject-based library for SSDP in Ubuntu Software Centre or libgssdp-1-0-1 (or higher) in Synaptic, and install.

---

### Post by Tropical Joe on 2010-06-13
Thank You.

---

### Post by Ubulindy on 2010-06-25
> **Tropical Joe said:**
> Hello, I'm relatively new to Ubuntu and have little knowledge about this, hope you can help. While downloading an aMSN packcage for an Intel x86 machine (I386)  I get this message: 

Error: Dependency is not satisfiable: libgssdp-1.0-1 (>= 0.6.4)

Can you give me some advice on what to do? It'd be much appreciated.

Using Karmic Koala, BTW.

 Sometimes when you get this error it means you arent downloading the proper package for the distro you have. In the case of aMSN, the latest one avail for Lucid is 0.98.3 ( 6-3-2010 ).  Its is avail via Synaptic:  menu>system>administration>Synaptic   OR
open a terminal and type: sudo apt-get install amsn
 You will then find aMSN under internet: menu>internet>aMSN
Hope this helps

---


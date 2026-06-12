---
title: "Long Mode?????"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by cgbben1 on 2006-03-04
I just picked up a 64bit copy of Ubuntu.....I was installing it onto VMware Workstation, when i got this error..... Your CPU dose not support long mode.  Use a 32bit distribution.:confused: How can this be :confused:   I am using a athlon 64 socket 754 on a DFI Nf3 250gb.  Why won't the 64 bit version install???

Thanks,
Blaine Benson

---

### Post by cgbben1 on 2006-03-05
Anyone?????:confused:

---

### Post by engla on 2006-03-05
Wait.. I'm not sure what this VMWare is, but are you trying to run ubuntu virtualized in VMware?

Then it's really about the limitations of that application, not your actual hardware..

---

### Post by cgbben1 on 2006-03-05
The program VMware is capable of a 64 bit prosesser.

---

### Post by Stormbringer on 2006-03-05
a) Are you running VMware on a 64-Bit Host-OS (Windows XP / Server 2003 x64 Editon, Ubuntu Linux 64-Bit, ...)?

If the answer is no, then you are out of luck - you can run a 64-Bit Guest-OS ONLY on a 64-Bit Host-OS!

b) Socket 754 Athlon 64 CPUs below Step E6 (you need to have an Venice Core or newer) ARE NOT capable of running 64-on-64.

If your system is equipped with an older Stepping - although you are running an 64-Bit Host-OS - you are also out of luck.

Cheers,
Storm.

---


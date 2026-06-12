---
title: "Installation fails on SuperMicro 7049GP-TRT server"
date: 2024-12-07
forum: Installation &amp; Upgrades
---

### Post by rogueagent991 on 2024-12-07
I have a brand new SuperMicro 7049gp-trt: dual Xeon processors, 96 GB RAM, WD 770 NVMe, 4×1 TB Kingston SSD.
This system is certified for Ubuntu 18.04 and 20.04 (albeit with different processors).

The BIOS detects the processors, RAM, hard drives, and doesn't report any errors.
The only BIOS change I made was to force UFEI.

I have tried both Desktop and Server versions of Ubuntu 20.04, 22.04, and 24.04 (all just downloaded). These were created using Rufus and Etcher. In all cases, after selecting "Try or Install Ubuntu", the system does a file check, then freezes. Safe graphics mode, same thing. I even pulled the SSD's out to see if that was the problem.
The Server installation outputs more to the screen. All checks are OK. The server installation stops at TTY1.

There are no logs on the installation USB.
For reference, RHEL 9.5 goes through the set-up to installation. (I didn't actually click install as I don't have an account.)

Suggestions?

Thx

---

### Post by him610 on 2024-12-07
> RHEL 9.5 goes through the set-up to installation. (I didn't actually click install as I don't have an account.)

Maybe Fedora is worth a look.

---

### Post by rogueagent991 on 2024-12-07
> **him610 said:**
> Maybe Fedora is worth a look.

Fedora Live 4.1 boots to GUI. It's slow, but it loads.

---

### Post by rogueagent991 on 2024-12-07
Debian installed without a problem.

---


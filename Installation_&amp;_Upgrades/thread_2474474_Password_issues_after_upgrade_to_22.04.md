---
title: "Password issues after upgrade to 22.04"
date: 2022-04-30
forum: Installation &amp; Upgrades
---

### Post by pugacioff83 on 2022-04-30
> **tips2448 said:**
> **Post 22.04, password fails root authentication for half of my programs**

Example: KSystemLog, Muon Package Manager, Discovery (password works for upgrade only, but not configure sources), and Krusader
Entering password lead's to the error, "Permission denied. Possibly incorrect password, please try again. On some systems, you need to be in a special group (often: wheel) to use this program.".
Log say's:
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): conversation failed
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): auth could not identify password for [USERNAME]

id: uid=1000(USERNAME) gid=1000(USERNAME)  groups=1000(USERNAME),4(adm),24(cdrom),27(sudo),30   (dip),46(plugdev),122(lpadmin),131(lxd),132(sambas  hare)

Password works for GParted, KDE Partition Manager, and Ubuntu Mainline Kernel Installer

Hello, I have the same problem, with the same id response and the same log message. Did you manage to solve?

---

### Post by QIII on 2022-04-30
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2474337](https://ubuntuforums.org/showthread.php?t=2474337)

Please do not hijack the threads of other users.  Similar symptoms often arise from different causes.  In that case, threads going down several lines of investigation can get confusing to the OP, you and anyone trying to help.

Unlike some StackExchange sites, we like to provide one-on-one individualized support, even if that means we have several threads with the same subject matter.

---


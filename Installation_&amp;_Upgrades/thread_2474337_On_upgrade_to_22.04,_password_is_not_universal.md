---
title: "On upgrade to 22.04, password is not universal"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by tips2448 on 2022-04-26
**Post 22.04, password fails root authentication for half of my programs**

Example: KSystemLog, Muon Package Manager, Discovery (password works for upgrade only, but not configure sources), and Krusader
Entering password lead's to the error, "Permission denied. Possibly incorrect password, please try again. On some systems, you need to be in a special group (often: wheel) to use this program.".
Log say's:
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): conversation failed
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): auth could not identify password for [USERNAME]

id: uid=1000(USERNAME) gid=1000(USERNAME)  groups=1000(USERNAME),4(adm),24(cdrom),27(sudo),30   (dip),46(plugdev),122(lpadmin),131(lxd),132(sambas  hare)

Password works for GParted, KDE Partition Manager, and Ubuntu Mainline Kernel Installer

---

### Post by TheFu on 2022-04-27
'wheel' is from the SunOS days.
On Ubuntu, the group is 'sudo'. Use the **id** command to validate group membership.
I did a 22.04 install last weekend and didn't see anything funny with sudo. It worked fine, like it does on 20.04 as far as I could tell.
*If it doesn't work, check the logs. See what they claim.* That's always step 1 in troubleshooting.  Logs are in /var/log/

BTW, I've never seen or used Muon.

---

### Post by tips2448 on 2022-04-27
Yes!  I remember the 'wheel' from Debian, and wasn't surprised that when I tried to add myself to the 'wheel', that it didn't exist...

I can't even use my password to open KSystemLog to view the log, so looked at it via dolphin.

Log say's:
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): conversation failed
Apr 28 15:23:52 USERNAME sudo: pam_unix(sudo:auth): auth could not identify password for [USERNAME]

My password doesn't work for Discovery, and Krusader, but does work for gparted and Ubuntu Mainline Kernel Installer (haha). Note, the password works for Discovery's upgrade, but doesn't work to configure.
I can however gain root to change software sources via Discovery etc. via terminal sudo

I had already checked the groups, and couldn't see anything unusual:
uid=1000(USERNAME) gid=1000(USERNAME) groups=1000(USERNAME),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),131(lxd),132(sambashare)


*I lost all my beans, as it's been so many many years since I came to the forum, different email, I will sort this out at a later time.

---

### Post by tips2448 on 2022-09-14
This outstanding problem was solved today by today's update of the Sudo package.

---


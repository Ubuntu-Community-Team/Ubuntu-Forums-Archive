---
title: "[SOLVED] Im having errors during installations"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by encryption.egz on 2008-07-14
i have a HP nx7400 notebook with proccesor dual core 1.7 Ghz, 1 Gb ram, and 80 Gb ATA FUJITSU hard disk.

When i was trying to install from Live Cd at 51% give me errno5 but from alternate at 83% give me error:

[B]Unable to install the select kernel
An error was returned while trying to install the kernel into traget system
kernel package: 'linux-generix'[/B] 

and then i activated console and the last row was

**Jul 13 13:05:27 base--installer: error: exiting on error base-instaler/kernel/failed-install**

so i try again from thet step "install base system" and than come another error:

**chroot/target dpkg --force--depends--install var/cache/apt/archives/libc6_2.7-10ubuntu3_i386.deb**

someone here tell me to check my disk , i did that with HDD self test and 3 tested gone succeeded
TEST 1 (QUICK)
test succeeded
TEST 2 (COMPREHENSIVE)
test succeeded
TEST 3 (S.M.A.R.T)
test succeded

What to do?!! im at least 54 hours without sleeping just to set ubuntu at my notebook... and im trying to give a big S.O.S here :S:S...

---

### Post by overdrank on 2008-07-14
> **encryption.egz said:**
> i have a HP nx7400 notebook with proccesor dual core 1.7 Ghz, 1 Gb ram, and 80 Gb ATA FUJITSU hard disk.

When i was trying to install from Live Cd at 51% give me errno5 but from alternate at 83% give me error:

[B]Unable to install the select kernel
An error was returned while trying to install the kernel into traget system
kernel package: 'linux-generix'[/B] 

and then i activated console and the last row was

**Jul 13 13:05:27 base--installer: error: exiting on error base-instaler/kernel/failed-install**

so i try again from thet step "install base system" and than come another error:

**chroot/target dpkg --force--depends--install var/cache/apt/archives/libc6_2.7-10ubuntu3_i386.deb**

someone here tell me to check my disk , i did that with HDD self test and 3 tested gone succeeded
TEST 1 (QUICK)
test succeeded
TEST 2 (COMPREHENSIVE)
test succeeded
TEST 3 (S.M.A.R.T)
test succeded

What to do?!! im at least 54 hours without sleeping just to set ubuntu at my notebook... and im trying to give a big S.O.S here :S:S...

HI and welcome, and you will need sleep as this can complicate the issues. Have you checked the cd for errors, and also the iso with MD5SUM 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Those errors lead me to believe there maybe a error on the iso.

---

### Post by encryption.egz on 2008-07-14
you were right both of cd had errors ... .but i did the MD5 sum of iso`s files and there are OK.. How to burn the CD at low speed... ?!

---

### Post by overdrank on 2008-07-14
> **encryption.egz said:**
> you were right both of cd had errors ... .but i did the MD5 sum of iso`s files and there are OK.. How to burn the CD at low speed... ?!

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by encryption.egz on 2008-07-14
thanx man..now im quoting from ubuntu thanks to u :D
a last adviceing .. do u have any ebook for using ubuntu system ...

---

### Post by overdrank on 2008-07-14
> **encryption.egz said:**
> thanx man..now im quoting from ubuntu thanks to u :D
a last adviceing .. do u have any ebook for using ubuntu system ...

Check out the help on the top panel by applications, systems. Good luck and you are welcome.

---


---
title: "Eclipse Ganymede"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by tde on 2008-10-25
Hi guys,

I'm new to kubuntu and I'm trying to install the latest version of Eclipse. Since there is only version 3.2 in repositories, I have downloaded the newest, Ganymede version in .tar.gz file. I unpacked it but there is no setup.exe ;) file in there so I'm lost. Could you please help me install it?

Thank you,
Tde

---

### Post by jespdj on 2008-10-25
You don't need to run a setup program after unpacking the .tar.gz. After unpacking, just cd into the directory and type ./eclipse.

---

### Post by tde on 2008-10-25
But when I use Konsole, if I type in eclipse, it says that it is not installed. How come?

---

### Post by jespdj on 2008-10-25
Because the directory that you unpacked Eclipse in is not in the PATH (the environment variable that specifies where the Bash shell looks for programs to execute).

Don't just open a terminal and type "eclipse". Go to the directory (with "cd") where Eclipse is unpacked and type "./eclipse" (dot, slash, eclipse).

---


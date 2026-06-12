---
title: "I can't open Sh and pl Files"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by delphiexile on 2008-09-02
Hello everybody;

I don't know why I can't install SH or PL files, I mean, when I clic on Lauch , nothing happens , I tried to make "Open a Terminal", the window of is close in less than 1 seconde .

I need to launch SH files to proceed the installation of my downloaded softwares.

Thanks for Helping me.

---

### Post by iaculallad on 2008-09-02
> **delphiexile said:**
> Hello everybody;

I don't know why I can't install SH or PL files, I mean, when I clic on Lauch , nothing happens , I tried to make "Open a Terminal", the window of is close in less than 1 seconde .

I need to launch SH files to proceed the installation of my downloaded softwares.

Thanks for Helping me.

On your terminal, make the script executable:

```
sudo chmod 777 /path/some_linux_installation_file.sh
```

then, change directory to /path and:

```
sudo ./some_linux_installation_file.sh
```

---

### Post by delphiexile on 2009-10-16
Thanks so much.

---


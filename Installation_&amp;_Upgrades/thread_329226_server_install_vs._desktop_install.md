---
title: "server install vs. desktop install"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-01-01
Can someone give me a link which will explain to me the basic differences between the functionality of a **SERVER** install vs. a **DESKTOP** install of Ubuntu ?

One thing in particular that I am looking for is if I want to have a networkable printer, do I need to have the system to which the printer is physically hooked (and would be hooked as a **LPT1/local** port printer) installed with a **SERVER** version of Ubuntu or a **DESKTOP** version of Ubuntu ?

Thanks.

---

### Post by Sef on 2007-01-01
What you want is a print server.  For that you can have a desktop set up, then download samba if you are networking with a windows computer.

---

### Post by meng on 2007-01-01
The basic difference is that you install the desktop version for a machine you intend to use as a workstation, you install the server version for a machine that you only intend to use as a server (local or web). The server version does not come with a GUI by default, although you can install one if you really wish to.

---

### Post by wpshooter on 2007-01-01
> **Sef said:**
> What you want is a print server.  For that you can have a desktop set up, then download samba if you are networking with a windows computer.

What if I have **NO** windows machines and ALL of my workstations are **Ubuntu** ?  Do I still use SAMBA ?

Thanks.

---

### Post by meng on 2007-01-01
Yes you can still use samba, or if you really want to you can use NFS.

---


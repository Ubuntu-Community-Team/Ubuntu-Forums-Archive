---
title: "correct to dpkg configuration"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by yojit on 2008-06-08
somebody please help me about dpkg error problem
(E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.)
how to resolve this
thanx

---

### Post by robertchahine on 2008-06-08
did you try ```
dpkg --configure -a
```

---

### Post by bapoumba on 2008-06-08
Moved to Installation & Upgrades.

---

### Post by yojit on 2008-06-08
> **robertchahine said:**
> did you try ```
dpkg --configure -a
```


sir but he asked for superuser
(dpkg: requested operation requires superuser privilege)

how i entered in superuser mode

thanx for reply


i m new user

---

### Post by bapoumba on 2008-06-08
Please run:
```
sudo dpkg --configure -a
```
Enter your own password (nothing will appear on the terminal output, it is normal).

---

### Post by robertchahine on 2008-06-08
oh yeah, for sure you will add sudo for the begining of the line.
that means 
```

sudo dpkg --configure -a 
```
then type your password

---


---
title: "help"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by nik1990 on 2008-08-22
i need help creating ubuntu account i tryed to create account with terminal but no cusses can sum one plz help me

---

### Post by iaculallad on 2008-08-22
> **nik1990 said:**
> i need help creating ubuntu account i tryed to create account with terminal but no cusses can sum one plz help me

On your terminal:

```
sudo useradd username
```

to give it a password:

```
sudo passwd username
```

---

### Post by nik1990 on 2008-08-22
it seas that i'm not in the sudoers file what should i do?

---

### Post by iaculallad on 2008-08-22
> **nik1990 said:**
> it seas that i'm not in the sudoers file

Add yourself to the admin group:

```
sudo adduser your_username admin
```

or

```
sudo cp /etc/group /etc/group.original
gksudo gedit /etc/group

```
and add your username to the admin line.

---

### Post by nik1990 on 2008-08-22
no it still dons't work

---

### Post by forger on 2008-08-22
Login with your first account (not the one you create) and then do the sudo commands iaculallad gave above, and you add the second username you created in the admin group

---

### Post by nik1990 on 2008-08-22
oooo ok then thank you

---


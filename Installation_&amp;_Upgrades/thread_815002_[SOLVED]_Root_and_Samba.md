---
title: "[SOLVED] Root and Samba"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by wabbit46 on 2008-06-01
How do I log in as root and edit the Samba conf file ?

---

### Post by Pumalite on 2008-06-01
sudo nano....
gksudo gedit...

---

### Post by sisco311 on 2008-06-01
By default, the root account password is locked in ubuntu.
You can use sudo and gksu to execute a command as super user(root).

To edit the samba configuration file open a terminal (Applications -> Accessories -> Terminal) and type:
```
gksu gedit /etc/samba/smb.conf
```

---

### Post by kamaji792 on 2008-06-01
Forgive me if this is not quite right, but in a terminal try:

```
sudo <your_favorite_editor> /etc/samba/smb.conf
```

I'd use **vim** for your_favourite_editor but my guess is you want a gui editor.

Might be a good idea to make a backup copy of the current samba confguration file:

```
cd /etc/samba
sudo cp smb.conf smb.conf.001
```

---


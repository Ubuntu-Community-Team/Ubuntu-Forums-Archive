---
title: "Super user Rights"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by krsnavan on 2008-06-28
i installed server from Zimbra.

Tried to install Xwindow packeage n it asks super user username password.

But during installation, tehre is no option to select n create super user account n username!

how to do it?

vanna

---

### Post by iaculallad on 2008-06-28
On your terminal:

Create the user:

```
useradd -c "FirstName LastName" -g admin -d /home/desired_username -s /bin/bash desired_username

```

Set the password:

```
passwd desired_username
```

---

### Post by krsnavan on 2008-06-28
when i try to add,it says

unable to lock password file.

---

### Post by iaculallad on 2008-06-28
> **krsnavan said:**
> when i try to add,it says

unable to lock password file.

Try inserting sudo before those commands:

```
sudo useradd -c "FirstName LastName" -g admin -d /home/desired_username -s /bin/bash desired_username
```

```
sudo passwd desired_username
```

---


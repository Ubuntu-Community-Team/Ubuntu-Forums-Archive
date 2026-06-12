---
title: "after password change cannot login into Gnome"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-10-17
hi

I have dapper drake installed.
I changed a user password using:```

sudo passwd user
```
and now cannot login into Gnome.
what's wrong ?

p.s
I can login into Gnome only using root user

---

### Post by aysiu on 2006-10-17
Maybe you had caps lock on when you typed your password?

You can try resetting your password again: ```
sudo passwd user
```

---

### Post by joff13 on 2006-10-17
why you do```
$ sudo passwd user
```

it's enough 

```
$ passwd
```

as a user

---

### Post by cccc on 2006-10-17
I tried everything, but still doesn't help !

---

### Post by joff13 on 2006-10-17
really stange, but did you try to reboot, just to verify?

---

### Post by cccc on 2006-10-17
yep, I tried to reboot many times. 

that's very strange and I cannot understand

---

### Post by taurus on 2006-10-17
Can you reset the password for that user again with 

```
sudo passwd username
```
Otherwise, reboot into recovery mode (from GRUB) and change the password for that user again with

```
passwd username
```

---


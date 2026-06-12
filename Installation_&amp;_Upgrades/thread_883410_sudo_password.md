---
title: "sudo password"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by ss2pheonix on 2008-08-07
im trying to sudo install some programs but when i type a sudo command it asksw for my sudo password but when i try to type i cant HELP!!!!!!!!!

---

### Post by SuperSonic4 on 2008-08-07
It is invisible typing in, you won't see any sign you're typing it in. Just type in as normal and press enter

---

### Post by ercferret18 on 2008-08-07
> **ss2pheonix said:**
> im trying to sudo install some programs but when i type a sudo command it asksw for my sudo password but when i try to type i cant HELP!!!!!!!!!

yeah, its typing, you just can't see it.

---

### Post by ss2pheonix on 2008-08-07
ok well what is my sudo password is it just my admin password or is it something different and if it is how do i change it

---

### Post by tuxxy on 2008-08-07
Should be your username password

---

### Post by iaculallad on 2008-08-07
> **ss2pheonix said:**
> ok well what is my sudo password is it just my admin password or is it something different and if it is how do i change it

When accessing sudo, you use your own account password. To change it (you're own password), drop on your terminal and issue the command below:

```
sudo passwd your_username
```

and input your current password followed by your new password and confirmation password.

---

### Post by tuxxy on 2008-08-07
You would only need to neter the root password if you were issuing the **su** command

---

### Post by ilrudie on 2008-08-08
> **iaculallad said:**
> When accessing sudo, you use your own account password. To change it (you're own password), drop on your terminal and issue the command below:

```
sudo passwd your_username
```and input your current password followed by your new password and confirmation password.

Alternatively you can always change your password in the terminal with ```
passwd
```  No need to be root or use sudo or anything special.  I mean, why make it more complicated than it is?

---


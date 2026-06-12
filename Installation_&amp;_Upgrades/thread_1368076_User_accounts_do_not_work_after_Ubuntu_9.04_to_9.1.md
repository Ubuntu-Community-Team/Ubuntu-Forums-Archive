---
title: "User accounts do not work after Ubuntu 9.04 to 9.10 upgrade"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by KarmicFan on 2009-12-30
I am fairly new to Ubuntu, but so far absolutely LOVE it!  However, I recently upgraded from Ubuntu 9.04 to 9.10 using the Update Manager and since then, the two user accounts I had configured will not work.

When I enter my user ID and password from the login screen, it looks as if Ubuntu is starting the GUI normally, but then it pops right back to the login screen.

Oddly enough, I can login as root (and that's how I've been using it) and get all the way in to the desktop.  Can anyone suggest a fix?  I'd rather not delete the accounts and start over, but if I must, I will have no choice.

Thanks!

---

### Post by zey on 2009-12-30
fresh install absolutely better than upgrade from 9.04 to 9.10
try to do fresh install ubuntu 9.10 on your computer.

---

### Post by KarmicFan on 2009-12-31
Well, I was hoping to avoid that, but like I said...  If I have to, I will.  I appreciate the help!  Thanks!

Happy New Year!

---

### Post by phillw on 2009-12-31
> **KarmicFan said:**
> I am fairly new to Ubuntu, but so far absolutely LOVE it!  However, I recently upgraded from Ubuntu 9.04 to 9.10 using the Update Manager and since then, the two user accounts I had configured will not work.

When I enter my user ID and password from the login screen, it looks as if Ubuntu is starting the GUI normally, but then it pops right back to the login screen.

Oddly enough, I can login as root (and that's how I've been using it) and get all the way in to the desktop.  Can anyone suggest a fix?  I'd rather not delete the accounts and start over, but if I must, I will have no choice.

Thanks!

If you can log in as root, try this ....

```
cat /etc/passwd
```

If you see the user names there, then do this ..

[code]passwd *username*[code]

for both *username*'s

That should allow them to log on.

If the 2 passwds are set okay, then you can delete the xorg.conf file & reboot - the xorg.conf file will re-create itself automatically (but, you'll loose any special video driver for either nvidia or ati that you've put on)

Post back if you have either of those two video cards.

Regards,

Phill.

---

### Post by KarmicFan on 2010-01-03
Tkans for the reply!  I have performed the password resets, but I can't find the xorg.conf fle.  Can you tell me what directory it resides in?  Even searching for it in the file browser yields no results...

---


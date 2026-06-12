---
title: "after install, no username or password"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by JPMaximilian on 2006-11-27
I installed 6.10, it was taking a while, so I went and had some breakfast, anyways, it never asked for a username or password during the install, so I don't know what that is when I try to login.  Is there a default?

---

### Post by taurus on 2006-11-27
Are you using the desktop CD (LiveCD) or the alternate CD?

---

### Post by JPMaximilian on 2006-11-27
The alternate CD.

---

### Post by taurus on 2006-11-27
Did you pick the first option or the second option when you installed it?

---

### Post by JPMaximilian on 2006-11-27
the first one.

---

### Post by taurus on 2006-11-27
And it didn't ask you to create a username and a password?  Reboot your machine and when you are at the GRUB menu, pick the recovery mode, probably second option on the list, and boot from it.  Once it's finished booting, paste the output of this command here...

```
cat /etc/passwd
ls -la /home
```

---

### Post by JPMaximilian on 2006-11-27
How do I bring the grub menu up?  It seems to skip over that.

---

### Post by taurus on 2006-11-27
I guess you have it hidden...  Just press <Esc> to displace it when you see the word GRUB or something similar to that one the screen.  I believe you have 10 seconds to press it or it will boot up Ubuntu...

---


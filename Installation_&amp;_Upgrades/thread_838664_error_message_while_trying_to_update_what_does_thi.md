---
title: "error message while trying to update? what does this mean?"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by tardiaf on 2008-06-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by avtolle on 2008-06-23
At the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

---

### Post by wbmcleod on 2008-06-23
> **avtolle said:**
> At the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

I got the same error message and went to terminal and ran your fix.  The program asked for my sudo password. I was unable to type in any password.  The cursor simply would not move and typing produced no result at all.  Hitting enter just got a wrong password message.  What to do?  Thanks, Bill

---

### Post by Pumalite on 2008-06-23
Type the password. You cannot see it. It's OK. Hit 'Enter' after you finish typing.

---

### Post by ibutho on 2008-06-23
You should enter your own user password. The password is not echoed back to the screen and the cursor does not move, so you will not see anything whilst entering the password.

---

### Post by avtolle on 2008-06-23
And, be sure you are typing in the correct password (remember, case sensitivity, just in case your Caps Lock is on).

---

### Post by tardiaf on 2008-06-23
thanks guys that command workd for me - an thanks for the rapid response!

---

### Post by wbmcleod on 2008-06-23
Thanks from me as well!  Now I have a broken package somewhere that I have to find, but I am progressing!  Bill

---


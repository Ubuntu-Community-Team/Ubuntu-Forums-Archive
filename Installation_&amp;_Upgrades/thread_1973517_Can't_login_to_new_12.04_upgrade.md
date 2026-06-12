---
title: "Can't login to new 12.04 upgrade"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by c901906 on 2012-05-04
Upgraded from 10.10 (Maverick Meerkat) all the way up to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64) through all of the release upgrades along the way. Now I can't login through the GUI. The account and password are correct (an incorrect password message will come up If I deliberately type in a wrong password). I can SSH from another machine just fine. There is a "guest" account that appears to work. Not that a Guest account is a good idea, it's not. But that is another problem for another day.

Any hints appreciated.

TIA!

---

### Post by oboedad55 on 2012-05-04
> **c901906 said:**
> Upgraded from 10.10 (Maverick Meerkat) to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64) and now I can't login through the GUI. The account and password are correct (an incorrect password message will come up If I deliberately type in a wrong password). I can SSH from another machine just fine. There is a "guest" account that appears to work. Not that a Guest account is a good idea, it's not. But that is another problem for another day.

Any hints appreciated.

TIA!

That upgrade path isn't supported: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

You'd have needed to go 10.10 to 11.04 to 11.10 to 12.04. Personally, I can't see the point. With that much to go through a clean install is faster and has a much better chance of success.

---

### Post by c901906 on 2012-05-04
Sorry. I should have said I went through all of the requisite upgrade versions. 


Thanks for responding. Anybody else?

---

### Post by c901906 on 2012-05-05
Here's what I found worked for me:

```
rm ~/.Xauthority
```

---

### Post by bbmonster on 2012-06-10
That also worked for me but make sure you do not reboot after deleting the file. Instead go back to the login screen and try logging in again. The first time i tried this, I rebooted right after deleting the file I booted into the terminal at tty7 if that's what's it called. 

> **c901906 said:**
> Here's what I found worked for me:

```
rm ~/.Xauthority
```

---


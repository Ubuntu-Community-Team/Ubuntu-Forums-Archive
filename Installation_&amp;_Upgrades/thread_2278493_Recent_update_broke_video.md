---
title: "Recent update broke video"
date: 2015-05-17
forum: Installation &amp; Upgrades
---

### Post by Radly on 2015-05-17
I have been running 15.04 for a few weeks, and did a routine update a few days ago.  Now my login screen is a useless mess--big black or white regions with random colored specks.  I can ssh into the system okay, so I can run command-line actions, and if reinstalling is the only solution, it won't kill me.  But I don't want to run into this again.  How can I determine exactly what caused this, and how to prevent it from recurring?  I don't even know what kind of graphics hardware I have, so some help in finding out that information via command line might be useful.  The hardware is a Dell Inspiron 531.

---

### Post by RobGoss on 2015-05-17
Open up your terminal and run this command it will give you your graphic card details.

```
 lspci | grep "VGA" 
```

---

### Post by Radly on 2015-05-17
Thanks.  So now I know that I have an NVIDIA GeForce 7900 GS, and that "grep -i nvidia /var/log/apt/history.log" returns nothing.  Is there something else I should be looking for that relates to the display?

---

### Post by Vladlenin5000 on 2015-05-17
Had you previously installed nvidia proprietary drivers? If so - depending on the way you did it - breaking after a kernel update is to be expected.
I won't comment further on the solutions because almost everything depends on your answer...

---


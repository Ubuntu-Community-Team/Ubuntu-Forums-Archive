---
title: "How can I fix the download manager?"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by kooia on 2010-03-25
The Software Manager, whenever I try to download something, says "Waiting for all other software managers to stop."  It doesn't install anything.  I close everything, and then it still says that.  How can I fix this, or have you had this experience?

---

### Post by foxmulder881 on 2010-03-25
Reboot your pc. Try again.

---

### Post by Serpher on 2010-03-25
You don't have to reboot, simply press Ctrl + Alt + F2 and enter the following command (Press Ctrl + Alt + F7 to return to your GUI)

```
sudo /etc/init.d/gdm restart
```

It simply means something is currently being installed. That command should kill all possible processes doing that. If it still doesn't work just reboot.

---

### Post by kooia on 2010-03-25
Thanks for the info... however, it didn't help.  I think I must have set some setting so one of the software managers starts when you turn on the computer.  Do you have any ideas with which programs could do this?

---

### Post by foxmulder881 on 2010-03-26
Can you post a screenshot of your task manager running?

---


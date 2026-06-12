---
title: "Problem with using installation software on Kubuntu"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by articnomad on 2006-11-09
Here's what happened, I was using Adept to install Java, the application locked up and I killed it. When I restarted Adept it said another program using the software database was already running. I looked at the process list and couldn't see anything else running that resembled, apt, apt-get, adept, or anything similar.

I don't what logs/files or whatever I should give, any help would be greatly appreciated.

---

### Post by gothique on 2006-11-09
Try to reboot?

---

### Post by articnomad on 2006-11-09
I've had this problem for three days, and of course I've rebooted several times. Now I'm thinking the database file has not been unlocked.

---

### Post by articnomad on 2006-11-09
Figured out the answer my self, so for anyone else who might have a problem like this run  ```
sudo dpkg --configure -a

```

---


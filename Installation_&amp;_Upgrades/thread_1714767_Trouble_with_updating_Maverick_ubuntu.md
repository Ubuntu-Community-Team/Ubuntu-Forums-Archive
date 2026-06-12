---
title: "Trouble with updating Maverick ubuntu"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by carega on 2011-03-25
Hi there! I'm having trouble updating Maverick ubuntu right now and I don't know why... When I try to download the new updates the following error pops up:

Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.4_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.4_all.deb) 404  Not Found [IP: 200.17.202.1 80]

The system tells me to check my internet connection but it's working fine. I'm actually online right now on messenger and using firefox (in fact I'm on my computer posting this!)

What can I do?

---

### Post by ~Plue on 2011-03-25
see if updating the software index fixes it and try again
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by carega on 2011-03-25
It worked. Why couldn't I do it trough the manager?

---

### Post by ~Plue on 2011-03-25
the software index was too old and the package referred was updated with a new one on the server

clicking 'check for new updates' (or something similar, cant recall the exact wording) would have achieved the same thing

---

### Post by carega on 2011-03-25
Oh! It was so simple. Thanks for helping!

---


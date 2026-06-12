---
title: "karmic's synaptic on strike"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dino99 on 2009-07-01
hi,

surprise: after today updates, update manager find new packages but refuse to install them (do nothing, no error shown), and can't open synaptic: ckick in menu but nothing happen.

Have to use console.

---

### Post by morryis on 2009-07-01
try to start synaptic via console, it works for me!

EDIT: console -> terminal ;-)

---

### Post by mano cazalet on 2009-07-01
same here, but terminal works fine

---

### Post by chrismine on 2009-07-01
Same here - I did an sudo apt-get upgrade and all updates installed - now I cannot get Karmic to boot not even in recovery mode - just a blank screen.

---

### Post by davideotape on 2009-07-01
Synaptic won't work at all for me. Just found this: [https://bugs.edge.launchpad.net/ubuntu/+bug/394203](https://bugs.edge.launchpad.net/ubuntu/+bug/394203) , so I'm going to reboot now and see what happens. Wish me luck :S

---

### Post by davideotape on 2009-07-01
Rebooted fine, but synaptic still isn't working. [https://bugs.edge.launchpad.net/ubuntu/+bug/394210](https://bugs.edge.launchpad.net/ubuntu/+bug/394210) is the bug I've filed, so please could someone confirm it :D

---

### Post by DougieFresh4U on 2009-07-01
> **davideotape said:**
> Rebooted fine, but synaptic still isn't working. [https://bugs.edge.launchpad.net/ubuntu/+bug/394210](https://bugs.edge.launchpad.net/ubuntu/+bug/394210) is the bug I've filed, so please could someone confirm it :D

Done.

---

### Post by tad1073 on 2009-07-01
Confirmed and added comment to launchpad.

---

### Post by dino99 on 2009-07-01
installed last libgksu2-0 from repo;)

---

### Post by cariboo on 2009-07-01
I have the same problem, and Users & Groups displays the same behavior.

Edit: I should have read the bug report first. :)

---

### Post by descendent87 on 2009-07-01
all fixed for me after libgksu update earlier

---


---
title: "If your 2.6.32-9 boots to a black screen (nVidia)..."
date: 2009-12-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-12-20
... try adding "nouveau.modeset=0" to the kernel line of the boot stanza. :(

---

### Post by plun on 2009-12-20
Well and thanks....

I am not going to test this Nouveau-crap for any reasons !!!

[-(

---

### Post by ruik on 2009-12-20
I was just going to do some nouveau testing :)

---

### Post by dino99 on 2009-12-20
i'm not so lucky: still black screen  ](*,)

---

### Post by MacUntu on 2009-12-20
Marking as "unsolved" then.

---

### Post by hikaricore on 2009-12-20
I did notice this, but i figured it just wasn't launching ttys again.
Sshed in from my media server and started X no probs.

---

### Post by MacUntu on 2009-12-20
Had no time to investigate. This "nouveau.modeset=0" option was a luck shot I tried because I remembered this "boot to black screen"-problem from earlier testing of Nouveau's kernel tree. Maybe coincidence (don't even know if 2.6.32-9 contains the relevant Nouveau parts) but it works! :D

---

### Post by ruik on 2009-12-21
Works for me, thanks!

---

### Post by dino99 on 2009-12-21
> **ruik said:**
> Works for me, thanks!

have you made change into dkms_autoloader (gnomeuser tweak) ?

---

### Post by ruik on 2009-12-21
All I did was that "nouveau.modeset=0".

---

### Post by MacUntu on 2009-12-25
Edit: crap.

---


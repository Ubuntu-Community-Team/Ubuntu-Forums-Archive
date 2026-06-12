---
title: "Karmic within Virtualbox"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tajreed on 2009-07-09
Installing daily build via Virtualbox within Jaunty I get "cannot format ext4". Or something to that effect. Is it even possible to use VB to test
Karmic on Jaunty with it's ext3 file system. If so, what am I missing?

Thanks

---

### Post by aamukahvi on 2009-07-10
> **tajreed said:**
> Installing daily build via Virtualbox within Jaunty I get "cannot format ext4". Or something to that effect. Is it even possible to use VB to test
Karmic on Jaunty with it's ext3 file system. If so, what am I missing?

Thanks

It doesn't matter what file system the host is using, the virtual hard disk is just one file on your system. Well, unless some constraints such as maximum file size come into play. Not likely in the case of ext3.

I had trouble in the past but the daily of 09/07 (x86) worked. If you're using Virtualbox 3.0 set the network card as Intel Desktop, otherwise I would get crashes and/or freezes.

---

### Post by jaakan on 2009-07-10
> **tajreed said:**
> Installing daily build via Virtualbox within Jaunty I get "cannot format ext4". Or something to that effect. Is it even possible to use VB to test
Karmic on Jaunty with it's ext3 file system. If so, what am I missing?

Thanks

I got that same error and other errors with in KVM when using K.K. Alpha 2 or little newer daily-live ISO but when I got yesterdays daily-live x64 ISO
and the install went smoothly, / = ext4 and just swap.

try a newer daily-live ISO like todays or yesterdays

---

### Post by tajreed on 2009-07-10
Solved-switched to the Intell network, and downloaded "daily" on a wired connection as opposed to a wireless connection. Daily (7/10)
loaded fine in VB

---

### Post by Andre_luis_bsrsoft on 2009-07-10
Here is all ok. Try a new daily build. It will works fine.

---

### Post by flakeparadigm on 2009-07-16
Does anyone know how I could successfully install the VB Xorg driver so I can use desktop effects within the VM?

---

### Post by aamukahvi on 2009-07-16
> **flakeparadigm said:**
> Does anyone know how I could successfully install the VB Xorg driver so I can use desktop effects within the VM?

Have you tried with VB 3.0.2, just a few days old.

---

### Post by flakeparadigm on 2009-07-16
I just realized that, thank you! It works great now.

---


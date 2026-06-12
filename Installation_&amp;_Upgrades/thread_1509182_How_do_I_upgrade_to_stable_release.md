---
title: "How do I upgrade to stable release?"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by creative31 on 2010-06-13
Hello, I have the Ubuntu 10.04 beta, though It isn't the most stable,how can I upgrade, without having to burn a cd, from the Ubuntu 10.04 beta, to the Ubuntu 10.04 stable release? 

thx!
Creative

---

### Post by suryaccnamcse on 2010-06-13
you can update through the update manager or You can update with the help of a USB stick , you dont need to burn a CD.

---

### Post by creative31 on 2010-06-14
I've tryed through the update manager, that didn't work, though I'll see if i have a 2 gig memory stick around. Is there any other way though?

---

### Post by linux-hack on 2010-06-14
> **creative31 said:**
> I've tryed through the update manager, that didn't work, though I'll see if i have a 2 gig memory stick around. Is there any other way though?

Did you have an error message ? Why didn't it work ? what did you do exactly ?

---

### Post by creative31 on 2010-06-14
there isn't any error, The stable version doesn't show up even when  I click check, just recommended and security updates.

---

### Post by howefield on 2010-06-14
What is the output of the following terminal command ?

```
lsb_release -a
```

If you started with the Beta and applied the updates, you'd end up with the final release.

---

### Post by creative31 on 2010-06-15
I did thata, heres what i got

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid

```

I have installed the updates too.

---

### Post by dino99 on 2010-06-15
so you have the latest of the latest :lolflag:

---

### Post by Chame_Wizard on 2010-06-15
```
uname -a 
```

---

### Post by linux-hack on 2010-06-15
> **dino99 said:**
> so you have the latest of the latest :lolflag:

:lolflag: if you have the latest you can't upgrade :lolflag:

---

### Post by howefield on 2010-06-15
> **creative31 said:**
> ```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid

```

Yep, you have the full release, if it weren't, it would have said development branch (or similar) in there.

Installing from any of the development snapshots/alphas ect and updating will give you the full release.

---


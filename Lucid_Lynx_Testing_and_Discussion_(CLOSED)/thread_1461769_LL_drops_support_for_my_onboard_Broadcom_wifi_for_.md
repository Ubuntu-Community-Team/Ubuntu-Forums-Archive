---
title: "LL drops support for my onboard Broadcom wifi for no extant reason."
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Krovas on 2010-04-24
It was there for a couple days, and now it isn't. Have no idea where to begin. Please advise.

---

### Post by Aearenda on 2010-04-24
I'd begin by looking at the output of 'dmesg' - in particular, for firmware messages, since broadcom wifi often needs it.

Paste this in a terminal:
```
dmesg | grep firmware
```

---

### Post by tokyobadger on 2010-04-24
I don't use wireless nor have broadcom hardware, but perhaps [this thread](http://ubuntuforums.org/showthread.php?t=885847&highlight=Broadcom+BCM43XX) might help your troubleshooting?

---

### Post by Krovas on 2010-04-25
> **tokyobadger said:**
> I don't use wireless nor have broadcom hardware, but perhaps [this thread](http://ubuntuforums.org/showthread.php?t=885847&highlight=Broadcom+BCM43XX) might help your troubleshooting?



No, Ludid supported it natively (for a few days, anyway)...no Winblowz drivers required. I always hated ndiswrapper.

---

### Post by mcooke1 on 2010-04-25
Is it the broadcom STA driver, some more information may help.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Krovas on 2010-04-26
> **mcooke1 said:**
> Is it the broadcom STA driver, some more information may help.


Okay, that clued me in. Evidently, it is. 5.60.38.36 is installed at the moment. However:

```
lspci | grep wireless
```

...yields nothing. There's no mention the card with a simple lspci. It seems to have disappeared again.

---

### Post by metallica1788 on 2010-04-26
I know this problem, my moms laptop has broadcom too.
I dont know why but sometimes after a crash or something the chipset locks itself. I've had that several times and it is just some weird hardware issue of broadcom. Sometimes it does it for no reason:confused: Most of the time the problem fixes itself when you disconnect the power for sometime.

---

### Post by Krovas on 2010-04-26
> **metallica1788 said:**
> I know this problem, my moms laptop has broadcom too.
I dont know why but sometimes after a crash or something the chipset locks itself. I've had that several times and it is just some weird hardware issue of broadcom. Sometimes it does it for no reason:confused: Most of the time the problem fixes itself when you disconnect the power for sometime.

Ah, that's interesting...and worth a try.

---

### Post by Krovas on 2010-04-26
> **metallica1788 said:**
> I know this problem, my moms laptop has broadcom too.
I dont know why but sometimes after a crash or something the chipset locks itself. I've had that several times and it is just some weird hardware issue of broadcom. Sometimes it does it for no reason:confused: Most of the time the problem fixes itself when you disconnect the power for sometime.


And we have a winnaaaaaah. Ten minutes sans power cord and battery worked. It seems I owe Lucid an apology.

Thank you very much for that post.

---


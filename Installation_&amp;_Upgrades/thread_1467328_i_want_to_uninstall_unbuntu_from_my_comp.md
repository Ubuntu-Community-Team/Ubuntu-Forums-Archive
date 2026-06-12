---
title: "i want to uninstall unbuntu from my comp"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by knighthaq on 2010-04-30
i have unbuntu and windows vista on my pc and would like to remove unbuntu from the hard drive and leave windows. getting rid of the grub option to boot and transfer unbuntu to my other pc. How do i get it off of this one? i dont see any folder for it under windows to delete

---

### Post by howefield on 2010-04-30
> **knighthaq said:**
> How do i get it off of this one? i dont see any folder for it under windows to delete

Did you install Ubuntu using the Wubi installer ?

---

### Post by Rasa1111 on 2010-04-30
sorry.

---

### Post by kansasnoob on 2010-04-30
Please post the output of the Boot Info script so we can see what you have:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dmata82 on 2010-04-30
> **howefield said:**
> Did you install Ubuntu using the Wubi installer ?

What happens with the partition ubuntu did?

---

### Post by howefield on 2010-05-01
> **dmata82 said:**
> What happens with the partition ubuntu did?

What partition ?

You don't know whether the OP has installed into a partition yet.

---

### Post by mshenrick on 2010-05-01
remove the partition in windows, then boot up the win install dvd, go to recovery console and type
```
fixmbr
```

---


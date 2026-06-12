---
title: "Swap File in Extended Partition?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Sand Lee on 2007-05-15
Does anyone know why the ubuntu installation defaults to putting your swap file in an extended partition instead of a primary? I'm not an engineer but it just looks inefficient to me..

---

### Post by jrusso2 on 2007-05-15
[QUOTE=Sand Lee;2657287]Does anyone know why the ubuntu installation defaults to putting your swap file in an extended partition instead of a primary? I'm not an engineer but it just looks inefficient to me..[/Q

That was supposed to say I am not sure its inefficient?

Just because its on an extended partition should not matter for efficiency unless you know something I don't?

---

### Post by Sand Lee on 2007-05-15
> **jrusso2 said:**
> Not sure you its inefficent?

huh?

---

### Post by pixellany on 2007-05-15
Having something in an extended partition should not affect speed.

Why they do it that way?--who knows?

---

### Post by bulldog on 2007-05-15
I think the reason is this,most people use ubuntu as a second OS.
So windows is primary1,windows data is primary2,ubuntu can be primary3,extended primary4[you can have only four primary partitions,but logicals as much as you want,up till 256 if I'm correct]so the swap should be a logical.
And you can create a separate /home or /data as an logical,otherwise you where stuck with four primary's.

---

### Post by Sand Lee on 2007-05-15
Makes sense :)

---


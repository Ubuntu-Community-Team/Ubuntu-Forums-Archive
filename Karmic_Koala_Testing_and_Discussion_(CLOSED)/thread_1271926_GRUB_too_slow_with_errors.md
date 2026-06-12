---
title: "GRUB too slow with errors"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-09-21
These are the errors that I get:

-no parent found for of device

-SYMLINK{unique}

and much more.

takes about 10 seconds on it's own. The os works well, except that all windows are frameless. I did "metacity --replace" works well for just once, then it goes back.

How can I resolve this problem? :p

---

### Post by knarf on 2009-09-21
Those SYMLINK{unique} messages are not grub errors, they're caused by a bug in udev: [#430654]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654")

---

### Post by dadedo123 on 2009-09-21
> **knarf said:**
> Those SYMLINK{unique} messages are not grub errors, they're caused by a bug in udev: [#430654]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654")

Do you know if updates later in the "updates manager" will fix it? Or should I wait for the full version of Karmic and reinstall?

---

### Post by VMC on 2009-09-21
> **dadedo123 said:**
> Do you know if updates later in the "updates manager" will fix it? Or should I wait for the full version of Karmic and reinstall?

dadedo, If you read that bug report you will find that they will be fixed shortly. At least read post#12.

---

### Post by martinpm24 on 2009-09-21
haha this have to be the most reported bug in karmic era.

---


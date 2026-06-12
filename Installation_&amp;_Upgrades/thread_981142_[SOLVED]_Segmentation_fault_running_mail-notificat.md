---
title: "[SOLVED] Segmentation fault running mail-notification"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by webit on 2008-11-13
After upgrade 8.04 to 8.10 mail-notification stopped working (no tray icon). I do some research and opened mail-notification in command line. This is what I saw:

```
$ mail-notification -i
** INFO: -------@-----.com: pobieram nag&#322;ówek z https://mail.google.com/mail/feed/atom
** INFO: --------@gmail.com: pobieram nag&#322;ówek z https://mail.google.com/mail/feed/atom
** INFO: -----------@yp.pl: pobieram nag&#322;ówek z https://mail.google.com/mail/feed/atom
Segmentation fault

```

I used ```
apt-get remove mail-notification
``` and than installed again. It didn't help. Any idea?

---

### Post by webit on 2008-11-13
> **webit said:**
> Any idea?

No matter what parameter I will use I always see Segmentation fault:

```
$ mail-notification -p    
Segmentation fault
```

```
$ mail-notification -a
Segmentation fault
```

:(

---

### Post by webit on 2008-11-13
All you have to do is remove /home/YOUR_USERNAME/gnome2/mail-notification

---

### Post by JarekMk on 2009-09-30
Nop, it's still don't work... Whis same info... What's wrong?

---

### Post by handjob_the_sofa_surfer on 2010-09-22
Having same problem. It's a bit disapointing that Ubuntu does not have any decent (cgmail is a gangbang of crash) mail notification.

---


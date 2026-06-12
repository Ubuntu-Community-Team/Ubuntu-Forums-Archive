---
title: "GRUB-2 eats kittens?"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by snargfish on 2009-07-23
Or at least my Windows XP x64 install. It isn't in the GRUB-2 boot menu. How do I get it back?

---

### Post by alexmurray on 2009-07-23
This is a [known issue]("http://www.ubuntu.com/testing/karmic/alpha3#Known issues").

---

### Post by snargfish on 2009-07-23
> **alexmurray said:**
> This is a [known issue]("http://www.ubuntu.com/testing/karmic/alpha3#Known issues").

Oh crap. Is there any kind of workaround?

---

### Post by christian.convey on 2009-07-23
> **snargfish said:**
> Oh crap. Is there any kind of workaround?

I think so.  In the recovery console, there's a menu option relating to grub.  When I selected it, the next time I booted I saw Windows in my grub menu.  (It had previously been missing.)

---

### Post by snargfish on 2009-07-23
> **christian.convey said:**
> I think so.  In the recovery console, there's a menu option relating to grub.  When I selected it, the next time I booted I saw Windows in my grub menu.  (It had previously been missing.)

Thanks. I'll give that a try now.

---

### Post by snargfish on 2009-07-23
That worked perfectly. All I had to do was select Update Grub in the Recovery Console. 

I owe you! :P

---

### Post by budluva04 on 2009-07-24
yup, or
```

$ sudo update-grub
```

works aswell :P

---

### Post by vishalrao on 2009-07-24
quick question: does doing the above steps (like sudo update-grub) mean you are still working with grub2 or reverting back to the old grub?

---

### Post by ranch hand on 2009-07-24
> **vishalrao said:**
> quick question: does doing the above steps (like sudo update-grub) mean you are still working with grub2 or reverting back to the old grub?
Grub2

---

### Post by dentaku65 on 2009-07-24
update-grub
should be present in the command shell of grub :-)

---


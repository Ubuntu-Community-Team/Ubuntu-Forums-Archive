---
title: "Help my update sends error"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Ragde15 on 2009-12-04
Solved

---

### Post by raymondh on 2009-12-04
> **Ragde15 said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

It keeps sending out this error, I'm new here by the way.
The updates on top of the list are "cups", "Cups bsd" cups clients and cups comon help would be appreciated.

Have you tried to open a terminal (applications > accessories) and typed

```
sudo dpkg --configure -a
```

You'll be asked for your password which when you type will not be shown.  Go ahead and try the terminal code.

If you have done so, are there any errors?

regards,

---

### Post by wojox on 2009-12-04
Open your terminal Applications > Accessories > Terminal and run:

```
sudo dpkg --configure -a'
```

---

### Post by Ragde15 on 2009-12-04
Yeah it now says blank deferred processing now taking place...

---

### Post by Ragde15 on 2009-12-04
thank you it's now solved! :)

---

### Post by raymondh on 2009-12-04
We're glad :)

Happy ubuntu-ing.

---


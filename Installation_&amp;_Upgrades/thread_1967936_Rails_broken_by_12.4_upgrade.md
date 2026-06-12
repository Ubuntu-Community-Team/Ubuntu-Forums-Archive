---
title: "Rails broken by 12.4 upgrade"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by bkline on 2012-04-28
Anyone else getting failures from rails 3 after upgrading Ubuntu to 12.4?

```
Invalid gemspec in [/var/lib/gems/1.9.1/specifications/mail-2.4.4.gemspec]: invalid date format in specification: "2012-03-14 00:00:00.000000000Z"
Invalid gemspec in [/var/lib/gems/1.9.1/specifications/tilt-1.3.3.gemspec]: invalid date format in specification: "2011-08-25 00:00:00.000000000Z"
Invalid gemspec in [/var/lib/gems/1.9.1/specifications/mime-types-1.18.gemspec]: invalid date format in specification: "2012-03-21 00:00:00.000000000Z"

```

And lots more error output ....

---

### Post by ciroque on 2012-04-28
Just noticed this happening. 

I am new to RoR, any thoughts on where to start looking?

---

### Post by ciroque on 2012-04-30
Going to try this tonight:

[http://stackoverflow.com/questions/5771758/invalid-gemspec-because-of-the-date-format-in-specification](http://stackoverflow.com/questions/5771758/invalid-gemspec-because-of-the-date-format-in-specification)


Will report the results.

---

### Post by bkline on 2012-05-02
> **ciroque said:**
> Just noticed this happening. 

I am new to RoR, any thoughts on where to start looking?

I'm no expert either.  Let me know if you're successful following the workaround you found.

---

### Post by ciroque on 2012-05-02
Yup! It did in fact work for me :-)

---

### Post by bkline on 2012-05-02
> **ciroque said:**
> Yup! It did in fact work for me :-)

Excellent, thanks!  I'll give it a try.

---


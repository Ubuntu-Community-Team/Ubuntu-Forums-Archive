---
title: "Remove / Disable rsyslog?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dxxvi on 2009-09-23
If I don't need any log message, can I remove/disable rsyslog to speed up my pc a little bit? If yes, how could I do it?

Thank you.

---

### Post by Longinus00 on 2009-09-23
Considering how quickly things can break using an alpha release I wouldn't recommend you do this. I'm also not convinced this will give you any noticeable speed up but if you still want to do it...

```
$ sudo apt-get remove rsyslog
```

---

### Post by VMC on 2009-09-23
> **dxxvi said:**
> If I don't need any log message, can I remove/disable rsyslog to speed up my pc a little bit? If yes, how could I do it?

Thank you.

Just to clarify. Why do you think removing 'rsyslog' will speed up the boot process? Have you looked at "/var/log". There is a ton of logs in there.

---


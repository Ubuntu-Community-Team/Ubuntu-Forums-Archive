---
title: "Do I need postfix. Just updated and the thing keeps popping up."
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-08-21
Debconf, postfix configuration.

---

### Post by taavikko on 2009-08-21
Update of "at" brings it in, for reasons that are unclear for me...

---

### Post by hugmenot on 2009-08-21
```
at (3.1.11-1ubuntu2) karmic; urgency=low

  * Restore the Recommends: default-mta | mail-transport-agent, which was
    dropped in the latest merge.

```

You can use « aptitude --without-recommends dist-upgrade » to skip it. When you schedule a task with « at » it will mail you the results of running the task. This is why there is a recommends on an MTA.

---

### Post by taavikko on 2009-08-21
> **hugmenot said:**
> When you schedule a task with « at » it will mail you the results of running the task. This is why there is a recommends on an MTA.

I meant that, how many average Joe's runs an scheduled task with "at", and do want to get notified. IMHO it should be only suggested.

---

### Post by hugmenot on 2009-08-22
Your wish was heard:

```
at (3.1.11-1ubuntu3) karmic; urgency=low

  * And drop the MTA back down from a Recommends to a Suggests, to not be
    pulled in by default.

```

---

### Post by philinux on 2009-08-22
I'm not going to run a mail server so I uninstalled postfix.

---


---
title: "firefox + esound = problem"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sandyd on 2010-04-08
For lucid, I found a weird thing going on with firefox and esound?
occasionally, firefox would give
```

/home/carleedolphinaura/.esd_auth: File exists
/home/carleedolphinaura/.esd_auth: File exists
/home/carleedolphinaura/.esd_auth: File exists

```
and while firefox outputed those errors (in the terminal), its menus would lag 3 seconds. Each time I would click on a menu, another identical line would be added to the terminal output.

however, all turns back to normal if I rm the ~/.esd_auth file

anyone else having this?

---

### Post by Jose Consuervo on 2010-04-21
This is happening to me as well. I have been having a number of problems with firefox the past couple of days, and this is one of them. Do you anything about this file?

---

### Post by dino99 on 2010-04-21
well esound is not the first choice actually  :confused:

time to time i use 2 magical tools: gconf cleaner & bleachbit (as root), to have a clean install

---


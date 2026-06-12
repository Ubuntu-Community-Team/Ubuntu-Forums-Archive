---
title: "Updated some updates in 16.04 but after restart got black screen"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by pankaj0008 on 2018-10-29
Hello everyone, I am using ubuntu 16.04. Today I am updated updates but after restarting I got blank black screen. What should I do?

---

### Post by Bashing-om on 2018-10-29
pankaj0008; Ouch ! Hate when that happens -

What can you boot to ?
Can you - at the login screen - execute ctl+alt+F2 to gain a console interface ?
If so, log into the system here - username and password; no response to the screen when the password is entered.
What shows now for a graphic's driver:
```

sudo lshw -C display

```
And let's see if this is a driver issue.

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---


---
title: "cannot apt-get anything???"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by hojotoolee2 on 2006-06-29
hi all,

how come I cannot apt-get install <anything>???  for example: i tried to

*sudo apt-get install make*

I am getting error messages:

[I]Reading package lists... Done
Building dependency tree... Done
E:  Couldn't find package make[/I]

Thanks in advance.

---

### Post by taurus on 2006-06-29
Try
```

sudo apt-get install build-essential

```

---

### Post by bikeboy on 2006-06-29
Don't forget to do a sudo apt-get update 1st.

---

### Post by hojotoolee2 on 2006-06-29
Hey guys, It is truely a n00b problem,
I did what you guys told me, it is working!!!

Thanks

---


---
title: "upgrade to 11.04 on dell inspiron 6400"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by neekos on 2011-07-22
greetings!

i upgraded from 10.10 to 11.04 a few months ago through the auto update method and found that the laptop would boot but was then unusable - trackpad and internet not functional and interface doesn't load.

i just downloaded the install cd and reinstalled (upgrade) and found that now i can access and run programs via alt-f2, however, the rest is still not functional.

does anyone have any suggestions of code to run or links to read?

thanks

---

### Post by neekos on 2011-07-23
i still have yet to find any clue as to what is causing this.. anyone?
thanks again

---

### Post by dino99 on 2011-07-23
watching logs is the best you can do: sort usefull errors

/var/log/
.xsession-errors

but try also the recovery mode & repair packages

---

### Post by neekos on 2011-07-23
thanks dino,
though that xsession command is not recognised in my terminal here.. hmm

---

### Post by 2F4U on 2011-07-23
.xsession-errors is a file, so what you should do is 

```
cat .xsession-errors
```

---


---
title: "Error: Wrong architecture 'amd64' ?? what the hell ?!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by newbcake on 2009-12-30
this happened when iwas trying to install wine on my pc what should i do

---

### Post by atomizer on 2009-12-30
do ```
uname -m
``` in a terminal to see what architecture you need


```

tom@tom-laptop:~$ uname -m
x86_64

```

---

### Post by howefield on 2009-12-30
> **newbcake said:**
> this happened when iwas trying to install wine on my pc what should i do

Generally happens when you try and install 64 bit application into a 32 bit system. You need the proper package for your system.

---

### Post by kellemes on 2009-12-30
Yes, as said by *howefield* you need the proper package for your system..
See [Ubuntu/Wine-documentation]("https://help.ubuntu.com/community/Wine#Ubuntu%20versions%20of%20Wine%20%28Recommended%29") for info on how to install and more..

---

### Post by newbcake on 2009-12-30
thanx for thehelp every body but i got it done :D

---


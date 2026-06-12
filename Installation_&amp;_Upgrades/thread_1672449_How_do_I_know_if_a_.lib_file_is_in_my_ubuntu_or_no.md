---
title: "How do I know if a .lib file is in my ubuntu or not?"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by elecbear on 2011-01-20
Hey guys, is there any command line that can show me the list of .lib files & development tools I've already have in my ubuntu?

Thanks a lot!

---

### Post by tommcd on 2011-01-21
There will be a bazillion lib files on your system.
Perhaps there is an easier way. What libs and or development packages are you searching for?

You could just install aptitude and run:
```
aptitude search .lib
```
Note that this will be a *long!!!* list of .libs. You could pipe it through *less* so you could scroll through it.
It would be more productive to search for the libs that you are looking for.

And welcome to the Ubuntu forums!

---

### Post by elecbear on 2011-01-22
> **tommcd said:**
> There will be a bazillion lib files on your system.
Perhaps there is an easier way. What libs and or development packages are you searching for?

You could just install aptitude and run:
```
aptitude search .lib
```Note that this will be a *long!!!* list of .libs. You could pipe it through *less* so you could scroll through it.
It would be more productive to search for the libs that you are looking for.

And welcome to the Ubuntu forums!

Thanks! I'm really a newbird XD

---

### Post by tommcd on 2011-01-22
> **elecbear said:**
> Thanks! I'm really a newbird XD
So, just out of curiosity, did you find the lib(s) that you were looking for? 
Write back if you need more help.

---


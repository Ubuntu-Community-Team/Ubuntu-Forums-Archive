---
title: "After upgrade from 9.1 to 10.4 700MB size increase"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by arborhil on 2010-05-03
Just wondering...

After upgrading my netbook from 9.1 to 10.4 (which went very smoothly, I'm happy to say) I noticed that my hard disk free space has decreased by about 700MB.  I'm using the full version of Ubuntu, not the netbook version.

Does 10.4 use 700 MB more than 9.1?

Is is possible there are some junk files left behind that I can get rid of?  :confused:

I already did the Janitor clean-up thing, so Ubuntu is telling me there is nothing left to get rid of.

---

### Post by cuby on 2010-05-05
hello,

try cleaning apt:

```
sudo pat-get clean
```

You may have a lot of old kernels and kernel sources in your system.
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1426744")

---


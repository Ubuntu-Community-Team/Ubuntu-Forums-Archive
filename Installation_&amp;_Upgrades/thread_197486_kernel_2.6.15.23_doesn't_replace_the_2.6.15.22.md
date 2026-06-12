---
title: "kernel 2.6.15.23 doesn't replace the 2.6.15.22?"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2006-06-15
ive noticed i have the following kernel packages:
```

linux-686 (version 2.6.15.22)
linux-image-2.6.15.23-686 (version 2.6.15.23.39)
linux-image-2.6.15.23-383 (version 2.6.15.23.39)
linux-image-686 (version 2.6.15.22)
linux-image-386 (version 2.6.15.22)
linux-kernel-headers (version 2.6.11.2-0ubuntu18)

```

what packages from this list can i remove?
and should i add the linux-headers-2.6.15.23-686 package? (and if i do so, should i remove the linux-kernel-headers package?)

---

### Post by FredB on 2006-06-16
[QUOTE=fargoth]ive noticed i have the following kernel packages:
```

linux-686 (version 2.6.15.22)
linux-image-2.6.15.23-686 (version 2.6.15.23.39)
linux-image-2.6.15.23-383 (version 2.6.15.23.39)
linux-image-686 (version 2.6.15.22)
linux-image-386 (version 2.6.15.22)
linux-kernel-headers (version 2.6.11.2-0ubuntu18)

```

what packages from this list can i remove?
and should i add the linux-headers-2.6.15.23-686 package? (and if i do so, should i remove the linux-kernel-headers package?)[/QUOTE]

First in a console, type :

```
uname -a
```

It will tell you what's your kernel version. And so, you can decide which kernel you want to keep. And of course, kernel and headers version must be the same.

And I think you could upgrade to 2.6.15-25 version ;)

---

### Post by fargoth on 2006-06-16
well, if im running the 2.6.15-25 kernel - is it safe to remove all the other packages?

is it ok to just have the "linux-image-2.6.15-25-686"  and "linux-restricted modules-2.6.25-25-686" packages and remove:
linux-686 (2.6.15.23)
linux-image-686 (2.6.15.23)
linux-image-2.6.15-23-686 (2.6.15-23.39)
linux-restricted modules-2.6.15-23-686 (2.6.15.11-1)

oh, and whats the difference between linux-686 and linux-image-686?

---

### Post by nocturn on 2006-06-16
[QUOTE=fargoth]well, if im running the 2.6.15-25 kernel - is it safe to remove all the other packages?

is it ok to just have the "linux-image-2.6.15-25-686"  and "linux-restricted modules-2.6.25-25-686" packages and remove:
linux-686 (2.6.15.23)
linux-image-686 (2.6.15.23)
linux-image-2.6.15-23-686 (2.6.15-23.39)
linux-restricted modules-2.6.15-23-686 (2.6.15.11-1)

oh, and whats the difference between linux-686 and linux-image-686?[/QUOTE]

Don't remove linux-686; it's a meta package.  If you don't have this, you may miss future kernel updates.

---

### Post by fargoth on 2006-06-16
so except the linux-686 i can remove the other packages?
by the way, why does the linux-686 have the version of my last kernel (when i had 23 it was 22 and now that i got 25 its 23....)

---


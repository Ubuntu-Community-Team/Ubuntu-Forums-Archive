---
title: "apps messed up after upgrade from 6.06 to 6.10"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by madsravn on 2007-03-25
Hey there...

I just upgraded from 6.06 to 6.10 yesterday, and now some of my apps doesn't work as they should (or at least, did before). When I try to run xmms, I get: 
```

mads@mrpro:~$ xmms
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2493 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2494 error_code 8 request_code 72 minor_code 0

```

Anyone able to point out what is wrong? :S I, a linux newbie, am not qualified for that :S

Thanks - Mads Ravn

---

### Post by mikelygee on 2007-04-01
I had a similar problem with qiv, and found a solution at [http://readthefuckingmanual.net/error/606/]("http://readthefuckingmanual.net/error/606/"):

XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/qiv

in your case, replace "qiv" with xmms and see if it works. I got different numbers in the error message, but it's worth a shot.

---


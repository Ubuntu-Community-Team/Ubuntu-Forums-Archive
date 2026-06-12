---
title: "/usr/bin/ld: cannot find -lpthread"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by bhaskar123 on 2012-06-11
hai guys,
        iam ney w to ubuntu..iam using ubuntu 10.10 version...
whenever am executing my prtogram i got a error message as follows..
send me solution as early as possible...

/usr/bin/ld: cannot find -libpthread
/usr/bin/ld: cannot find -lm
/usr/bin/ld: cannot find -lrt
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make: *** [exe] Error 1
:(
thanks in advance

---

### Post by steeldriver on 2012-06-11
You will need to give us a lot more information about what you are trying to do

It sounds like either you don't have the necessary build environment installed (build tools + dev libraries) or your Makefile is broken (missing or wrong -L paths)

BTW this kind of question probably belongs in the Developing and Programming subforum: [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---


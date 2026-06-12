---
title: "Compile firefox wiki not working for me"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-03-06
Anyone who had experience with this [https://wiki.ubuntu.com/CompileFirefoxNewVersion](https://wiki.ubuntu.com/CompileFirefoxNewVersion) , could you tell me your ideas? the compile exits with errors (in ancient greek I think) when using conf file from the wiki site.

While it ends without errors, make -C doesn't work, when I use the short options from [http://developer.mozilla.org/en/docs/Configuring_Build_Options#Firefox_Optimized_Static](http://developer.mozilla.org/en/docs/Configuring_Build_Options#Firefox_Optimized_Static)

which are: ```

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-opt-static
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --enable-static
ac_add_options --disable-shared
ac_add_options --disable-tests
mk_add_options MOZ_CO_PROJECT=browser
```

I wanted to compile to see if it makes any difference... thanks.

PS. I got all the depencies listed in that wiki.

---


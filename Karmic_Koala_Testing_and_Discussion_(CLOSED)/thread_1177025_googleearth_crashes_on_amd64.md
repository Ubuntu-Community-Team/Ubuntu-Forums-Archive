---
title: "googleearth crashes on amd64"
date: 2009-06-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-06-02
I just built googleearth with make-googleearth-package , it threw some warnings but completed sucessfully and installed ok (with gdebi) . When I try to run it I get the splash screen and then it crashes , from term I get this  .
```
ron@ron-desktop2:~$ googleearth %f
/usr/lib/googleearth/googleearth-bin: symbol lookup error: /usr/lib/googleearth/libssl.so.0.9.8: undefined symbol: EVP_idea_cbc
ron@ron-desktop2:~$ 

```

libssl0.9.8 is installed and uptodate also libssl0.9.8 -dev

---

### Post by ronacc on 2009-06-03
found the cure , atleast for me , googleing on "googleearth crashes" I found that googleearth installs its own version of libssl.so.0.9.8 in the dir where it installed (in my case /usr/lib/googleearth ) , renaming that to libssl.so.0.9.8.bak forces googleearth to use the ubuntu version of libssl.so.0.9.8 and it starts and runs OK .

---

### Post by philinux on 2009-06-03
I think I've seen this before a few weeks back. I recollect it's been bugged too with similar fix.

---

### Post by ronacc on 2009-06-03
a search of the forum didn't turn anything up but googleing it turned up a similar error and fix for libcrypto , so I tried the rename and it worked , I'll take your hint and search for the bug to add my comments.


edit: thanks philinux .  heres the link to the bug  [https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/369471](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/369471)   , confirmed the bug and added comment .

---


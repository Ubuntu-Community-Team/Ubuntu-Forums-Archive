---
title: "Possible bug: ctrl+alt+backspace not working even after disabling DontZap in Xorg.con"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-07-28
I am trying to enable ctrl+alt+backspace to restart Xorg but I am not able to do it. In my/etc/X11/xorg.conf I have

```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```

I also tried installing dontzap and ran sudo dontzap --disable but no luck. On the other hand RightAlt+PrtSc+k works

---

### Post by MacUntu on 2009-07-28
[http://ubuntuforums.org/showpost.php?p=7486270&postcount=14](http://ubuntuforums.org/showpost.php?p=7486270&postcount=14)

---


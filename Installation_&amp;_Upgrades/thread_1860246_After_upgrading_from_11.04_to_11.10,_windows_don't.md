---
title: "After upgrading from 11.04 to 11.10, windows don't draw correctly"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by 81duz1d0 on 2011-10-14
Hello.
I just update my Ubuntu and after it all the windows aren't showing up as they should. Their frames don't got drawn and neither does their content.

Here in the forum I ran into this topic [http://ubuntuforums.org/showthread.php?t=893925](http://ubuntuforums.org/showthread.php?t=893925) and tried the following commands

```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24
gtk-window-decorator --replace &

```

No luck.

I'm using nVidia drivers and Compiz

---

### Post by 81duz1d0 on 2011-10-14
```

metacity --replace

```

"Worked", it showed the windows properly but I couldn't do anything else in the system

---


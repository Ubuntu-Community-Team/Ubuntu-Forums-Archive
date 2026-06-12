---
title: "grub-gfx : install errors"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by jeanjean23 on 2007-04-20
hello,
i exactly followed the help ([http://doc.ubuntu-fr.org/grub-gfx](http://doc.ubuntu-fr.org/grub-gfx) ) : it's seems very simple & clear.
But at the end of the process, an error occurs :

I typed this (for info)
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,2)
```

and when installing Grub :

```
sudo grub-install hdX
```

thus for me X = a or 0 (i've tried both ; and i also tried (hd0)  and dev/hda )

there is the problem :

```

/usr/sbin/grub-install: 272: Syntax error: redirection unexpected
```

Any idea would be helpful,
thanks

---

### Post by jeanjean23 on 2007-04-20
nobody to help me ?

---


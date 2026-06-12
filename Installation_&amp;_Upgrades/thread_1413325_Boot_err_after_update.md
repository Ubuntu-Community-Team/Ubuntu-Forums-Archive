---
title: "Boot err after update"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by yuxin.gts on 2010-02-22
Hi there,

I got a grub err each time after updating ubuntu. I have to boot the system manually, and then update grub2. Now I am really scared to update. I thought this bug would be solved very soon, but it is still there. I can't bare it anymore.

 Is there any solution for that? 

Cheers,

---

### Post by ajgreeny on 2010-02-22
More info please.
What grub error, and which version of ubuntu and grub?
What do you mean by "have to boot manually"?

---

### Post by kansasnoob on 2010-02-22
It would be good to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'd also like to see the output of:

```
uname -m
```

and:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

---


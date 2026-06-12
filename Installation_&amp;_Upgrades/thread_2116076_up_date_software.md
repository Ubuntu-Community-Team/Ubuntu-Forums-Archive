---
title: "up date software"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by omid2s on 2013-02-14
Hello to all
I update softwares
and after restart run [FONT=Arial Black][SIZE=3]tty1 console[/SIZE][/FONT] and I press alt ctrl f2 and not exit.....
[SIZE=3]help me):P[/SIZE]

---

### Post by ibjsb4 on 2013-02-14
Its

Ctrl + Alt + F7

---

### Post by omid2s on 2013-02-14
ohhhhh..no

alt ctrl f7  not work...
any answer):P

---

### Post by Bashing-om on 2013-02-14
omid2s; Hi !

do you mean that you are not booting to the GUI (desktop) ?

For your graphics were you using a proprietary driver ?

[INDENT][INDENT]will try to help

[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2013-02-15
> **Bashing-om said:**
> omid2s; Hi !

do you mean that you are not booting to the GUI (desktop) ?

For your graphics were you using a proprietary driver ?

[INDENT][INDENT]will try to help

[/INDENT][/INDENT]
That's how I read that... Booting straight to a console prompt.

Update to a new kernel sometimes borks proprietary drivers because they were installed/built/compiled on a previous kernel version.

If he removes/purges the driver, then reinstalls, he should be back up.

Posting the results of 
```

lspci -vnn | grep VGA

```
and posting /etc/X11/xorg.conf (if it exists) would tell us if he has special video hardware and a proprietary driver installed (ATI or nVidia). If so, then he could get help doing that, tailored to his needs.

If not and if it was natively supported, it could be a kernel change that dropped out an old video hardware module or a change in Xorg-Server that did the same... But more than likely than not, the above.

---


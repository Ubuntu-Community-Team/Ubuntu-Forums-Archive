---
title: "Ubuntu does not boot without &quot;nomodeset&quot; in grub"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by gore-amit on 2013-12-18
I was having a working 12.04 64bit system. However suddenly after couple of abnormal shut down of system. I am not able to boot normally.
Machine boots but there is default purple/black screen. No textbox or login buttons.
After editing the grub and making "nomodeset", machine boots.
However I can see an "AMD Testing use only. Unsupported Hardware" watermark at right bottom corner of screen.
I have not activated "ATI/AMD proprietary FGLRX graphics drivers"

Following some forums, I tried to edit grub and make it nomodeset and then tried update-grub but it fails.
I keep getting "/usr/sbin/grub-mkconfig: 36: /etc/default/grub: Syntax error: EOF in backquote substitution" error message.

Also tried to use Boot Repair but still not able to fix it.
[http://paste.ubuntu.com/6594930/](http://paste.ubuntu.com/6594930/)

Attaching the grub file for reference (grub.txt).

---

### Post by gore-amit on 2013-12-18
While booting i can see following entry:
linux /vmlinuz ........ ro drm.\ debug=0xe plymouth:debug

---

### Post by oldfred on 2013-12-18
Silly computers do not like typos. And often those are the hardest to find.

[COLOR=#ff0000]quite[/COLOR] splash nomodeset

quiet splash nomodeset

---

### Post by gore-amit on 2014-01-03
Thanks for pointing out.
I was not able to fix it any which way so I just reinstalled it and it worked.

---

### Post by steeldriver on 2014-01-03
FYI your GRUB_CMDLINE_LINUX_DEFAULT line also had a Unicode double quote instead of a regular ASCII character

```
GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=#ff0000]**&#8221;**[/COLOR]quite splash nomodeset"
```

---


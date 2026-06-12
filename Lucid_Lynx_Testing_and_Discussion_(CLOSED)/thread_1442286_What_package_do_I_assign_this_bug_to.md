---
title: "What package do I assign this bug to?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-03-29
If you use F11 with Firefox, it goes fullscreen. Pressing it again restores the window.

But if you go fullscreen and quit (ALT F4), the next time you start Firefox you will have a problem; it will be fullscreen, but when you try to restore with F11, the window title is under the gnome panel.

I'd like to know #1) What package do I report against and #2) Can anyone confirm this behavior?

Thanks,
Jarlath

---

### Post by miegiel on 2010-03-29
> **jarlath said:**
> If you use F11 with Firefox, it goes fullscreen. Pressing it again restores the window.

But if you go fullscreen and quit (ALT F4), the next time you start Firefox you will have a problem; it will be fullscreen, but when you try to restore with F11, the window title is under the gnome panel.

I'd like to know #1) What package do I report against and #2) Can anyone confirm this behavior?

Thanks,
Jarlath

[LIST=1]
[*]Firefox :-k
[*]Yes (in xubuntu + compiz + emerald).
[/LIST]

---

### Post by QwUo173Hy on 2010-03-30
Thanks Miguel.  I'm not sure about #1. I think the window manager may be to blame? I think I'll file it against gtk-window-decorator, which I see running as a process.

---

### Post by QwUo173Hy on 2010-03-30
Maybe you can confirm my report also? [https://bugs.launchpad.net/ubuntu/+source/compiz/+filebug](https://bugs.launchpad.net/ubuntu/+source/compiz/+filebug)

Thanks :)

---


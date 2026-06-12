---
title: "New theme metacity aliasing."
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by screaminj3sus on 2010-03-06
Its 2010. What is with the ugly aliasing with rounded corners? its looks very unprofessional and ruins the look of the new default them which has potential to look great. Windows and OSX don't have this problem. We need to get with the times and get anti-aliasing support in metacity.

---

### Post by Rob2687 on 2010-03-06
A long overdue improvement. When is it gonna happen already?....

---

### Post by yoasif on 2010-03-06
[https://bugzilla.gnome.org/show_bug.cgi?id=345249](https://bugzilla.gnome.org/show_bug.cgi?id=345249)

---

### Post by cyberkilla on 2010-03-06
It is rather a shame, because there is no alternative of the same calibre. Emerald is buggy and abandoned software.

Since Metacity actually supports compositing, it must be theoretically possible. I bet there are some serious technical hurdles though; there has to be /some/ reason that nobody has attempted it yet.

EDIT:

> **yoasif said:**
> [https://bugzilla.gnome.org/show_bug.cgi?id=345249](https://bugzilla.gnome.org/show_bug.cgi?id=345249)
Wow, that thing's barren, considering the number of mentions this aliasing problem gets.

---

### Post by psyke83 on 2010-03-06
Yes, this is something that's desperately needed.

Individual themes are not capable of modifying the aliasing or rounding on windows, so it really does need to be patched in Metacity's application code (and steps taken to ensure that Compiz's Metacity theming - through gtk-window-decorator - is taken into consideration).

---

### Post by cyberkilla on 2010-03-06
> **psyke83 said:**
> Yes, this is something that's desperately needed.

Individual themes are not capable of modifying the aliasing or rounding on windows, so it really does need to be patched in Metacity's application code (and steps taken to ensure that Compiz's Metacity theming - through gtk-window-decorator - is taken into consideration).

I heard something about Metacity being abandoned soon, in favour of Mutter (which the blog post deemed "Metacity 3"). Lots of mixed messages lately..

[http://blogs.gnome.org/metacity/2009/07/06/the-future-of/](http://blogs.gnome.org/metacity/2009/07/06/the-future-of/)

---

### Post by psyke83 on 2010-03-06
> **cyberkilla said:**
> I heard something about Metacity being abandoned soon, in favour of Mutter (which the blog post deemed "Metacity 3"). Lots of mixed messages lately..

Yes, but will it replace Metacity for Lucid's release? I don't think so. I tried out Mutter and it was *very* slow on my system (and I couldn't find any options to disable or modify compositing). Perhaps Lucid's version is not representative of the final product, but I sure hope it improves before replacing *any* window manager...

---

### Post by cyberkilla on 2010-03-06
> **psyke83 said:**
> Yes, but will it replace Metacity for Lucid's release? I don't think so. I tried out Mutter and it was *very* slow on my system (and I couldn't find any options to disable or modify compositing). Perhaps Lucid's version is not representative of the final product, but I sure hope it improves before replacing *any* window manager...

Good idea about trying Mutter. I'm installing it now. If mutter doesn't support non-compositing, it would be a bit of a problem on some computers. In fact, resizing windows with a compositor enabled on any WM is rather slow compared to basic Metacity for me.

EDIT:
I just tried it. A few console error messages and the functional equivalent of 2FPS:P Then I realised that I'm using Nouveau and don't have 3D acceleration...

---


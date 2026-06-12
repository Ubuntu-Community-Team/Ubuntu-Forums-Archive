---
title: "Terminal cut/paste broken in Karmic?"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Blueshell on 2009-10-06
Using mouse-right and mouse-middle to select and then paste text in the Terminal window appears broken for me in the Karmic beta.  It's worked fine for many years for me in Hoary, Breezy, etc, though I can't recall if I've tried 8.04, 8.10, or 9.04 with it; I'm reinstalling (not upgrading) some machines running fairly old releases directly into 9.10.

I can select a word by double-clicking on it, but then mouse-middle won't paste it back in.  shift+insert -does- paste it in.  This also seems to affect, e.g., the location bar in Firefox; selected text in one window can't be pasted into the location bar, which is crippling.

What changed?  I assume there's some global setting in Gnome somewhere that I need to reset, but what?  Searching for the obvious keywords yields -way- too many hits to investigate because cut, paste, terminal, gnome-terminal, xterm, etc are all too generic.

Thanks!

---

### Post by Giblet5 on 2009-10-06
Works for me.

Select text (whatever method, whatever window).
Middle-click in terminal = pasted.

Did you globally bind 'button2' somewhere else? (That's my bet)

This box is Karmic, patched to date.

---

### Post by Blueshell on 2009-10-06
I haven't bound anything.  This is a fresh install on a new disk.  I suppose I should see if it happens in the LiveCD, but it would be a subtly different install---I actually installed from the AMD64 Alternate Install.

Any other ideas?

---

### Post by Blueshell on 2009-10-06
I just tried xev---yes, it at least sees all three mouse buttons... :)

[Although as far as I can see in a quick perusal, it prints the -same- data (except for the timestamp) for all three buttons, which seems weird.  An old Hoary does the same, though (though it prints "63" for keys and karmic is printing some number up around 2^32).]

So I'm still stuck.

---


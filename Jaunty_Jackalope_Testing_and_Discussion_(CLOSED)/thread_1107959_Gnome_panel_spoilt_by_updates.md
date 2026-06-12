---
title: "Gnome panel spoilt by updates"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2009-03-27
This is only cosmetic, but irritating. The updates that came down a little while ago spoilt the gnome panels.

If you right-click > properties on a panel, and click on the 'Background' tab, you get a choice of 'None', 'Solid colour' (glad to see they've spelt colour correctly :wink: ) and 'Background Image'. I don't like two default bright white bars glaring at me top and bottom of the screen, so I always change the default 'None' to Solid colour and set it more transparent than opaque. This allows the wallpaper pattern and colour to bleed through and I find it more restful.

Alternatively, if you choose 'Background Image' and choose a different (but complementary colour) wallpaper you can get some really psychedelic effects.

But now after the latest updates, with either 'Solid colour' or 'Background Image', the bright white shows through with the main menu, with the default panel apps at top right but not, strangely, with icons for other apps like firefox. It looks revolting. See the screenshot.

This is probably a bug/regression. Any thoughts? Anyone else getting this, or is this just on my system?

---

### Post by rbmorse on 2009-03-27
I'm getting it and share your annoyance.

Filed bug 349774

---

### Post by coffeecat on 2009-03-27
> **rbmorse said:**
> I'm getting it and share your annoyance.

Thank goodness for that! Not thank goodness that you're annoyed; I'm glad it's not just me. :(

And thanks for posting. I was getting lonely.

I've had a quick look on launchpad and can't see any relevant bug reports, but I haven't posted a bug myself. I'm not sure how to describe this succinctly and I was hoping others may have untangled this already.

---

### Post by rbmorse on 2009-03-27
I filed bug 349774

---

### Post by coffeecat on 2009-03-27
Thanks.

---

### Post by PatrickVogeli on 2009-03-29
same here, looks really ugly..

---

### Post by Kosimo on 2009-03-29
Same here guys.
The curious thing is; If you already had some panel with this configuration now looks fine, but if you create a new user and change the panel transparency then you get this bug.

---

### Post by coffeecat on 2009-03-29
> **Kosimo said:**
> Same here guys.

Have a look at [lunchpad bug 349774]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/349774") that rbmorse initiated. It's a bug with the Human theme. Try another theme. I've changed to an all-blue desktop with Clearlooks and the Oxygen icon set and now I'm a happy bunny.

---

### Post by Sand &amp; Mercury on 2009-03-29
> **coffeecat said:**
> Have a look at [lunchpad bug 349774]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/349774") that rbmorse initiated. It's a bug with the Human theme. Try another theme. I've changed to an all-blue desktop with Clearlooks and the Oxygen icon set and now I'm a happy bunny.
It would be because the panel has a background set for it already in its gtkrc, a very very subtle gradient. This happens for any themes that set backgrounds for the panel themselves. If it bothers you, use the Human-Clearlooks theme.

---

### Post by coffeecat on 2009-03-29
> **Sand & Mercury said:**
> If it bothers you, use the Human-Clearlooks theme.

The point is that the Human theme worked fine when I first installed (a network install on 26th March - so equivalent to a fresh Beta) - as far as I can make out this was with the human-theme_0.28.6_all.deb package. But it was after updating on 27th that the problem appeared. That was when the human-theme_0.28.7ubuntu1_all.deb package was installed. So, perhaps the 0.28.7 version of the Human Theme needs fixing. And the Human Theme, by the way, doesn't have this problem in either Intrepid or Hardy.

Yes, it does bother me, but why are you telling me to use Human-Clearlooks when not only have I said that I'm using Clearlooks, but you've quoted me as saying that I'm using Clearlooks? :roll:

---

### Post by coffeecat on 2009-03-30
The latest post on the launchpad thread linked earlier reports that v 0.28.8 of the Human Theme fixes this. I've just updated and can confirm this.

---


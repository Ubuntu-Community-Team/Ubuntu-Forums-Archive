---
title: "Shutdown and Firefox Fonts"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gannin on 2009-10-22
I'm testing out the beta of Karmic and I have two questions.  First, is there any way to get the Shutdown option back into the System menu instead of only having it in the fast-user-switching applet?

Also, under Appearance > Fonts I changed the way fonts are rendered and it seemed to update to the new style everywhere except Firefox, which still has the funky blurry-looking fonts from before I made the change.  How do you get Firefox to follow along with the rest of the desktop?  Thanks.

---

### Post by oboedad55 on 2009-10-22
> **Gannin said:**
> I'm testing out the beta of Karmic and I have two questions.  First, is there any way to get the Shutdown option back into the System menu instead of only having it in the fast-user-switching applet?

Also, under Appearance > Fonts I changed the way fonts are rendered and it seemed to update to the new style everywhere except Firefox, which still has the funky blurry-looking fonts from before I made the change.  How do you get Firefox to follow along with the rest of the desktop?  Thanks.

Are the Firefox fonts handled in Firefox?

---

### Post by cor2y on 2009-10-22
Set your firefox font rendering selection manually in Edit->Preferences->Content->Fonts & Colors->Advanced

---

### Post by FuturePilot on 2009-10-22
> **Gannin said:**
> I'm testing out the beta of Karmic and I have two questions.  First, is there any way to get the Shutdown option back into the System menu instead of only having it in the fast-user-switching applet?


Remove the user-switcher applet from the panel. The Shutdown option will appear in the System menu.

> Also, under Appearance > Fonts I changed the way fonts are rendered and it seemed to update to the new style everywhere except Firefox, which still has the funky blurry-looking fonts from before I made the change.  How do you get Firefox to follow along with the rest of the desktop?  Thanks.

That's a known issue. [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761") There's a workaround mentioned in there.

---

### Post by Gannin on 2009-10-22
Thanks for the information FuturePilot, that fixed things nicely.

---


---
title: "cairo/pango cairo_show_text_glyphs"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by billenbois on 2008-09-15
Apparently libpango has been upgraded to latest libcairo, but not libcairo, and no dependency checks.
Or I might be wrong, since its a new upgrade, and theres no dep check it looks strange..

/usr/lib/libpangocairo-1.0.so.0: undefined symbol: cairo_show_text_glyphs

of course, this means no gnome app can start, and, reverting to the previous libpango "fixes" the problem.

I don't see anyone else having that so I wonder what I might have done incorrectly or if its really a bug (I'd think the dev would have noticed after starting a new gnome-terminal - not starting of course)

tryed reinstalling libcario and latest pango of course (from main repositories)

libcairo2 1.7.4-0ubuntu1
libpango1.0-0  1.21.6-1

edit:
nevermind, by typing cairo version i found it was up to date to started looking at unpackaged libcairo libs that would be around.. and.. found some. removing em = fix.

---


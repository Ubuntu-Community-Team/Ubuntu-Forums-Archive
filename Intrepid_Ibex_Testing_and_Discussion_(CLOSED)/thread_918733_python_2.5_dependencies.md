---
title: "python 2.5 dependencies"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by darkenergy on 2008-09-13
i noticed that the python update wants me to install tcl8.4 as well as tk8.4 but i got already both 8.5 versions.

i have not yet performed this update so.. how can i fix this or circumvent it.

it's not a matter of space to me  but it's anoying to have different versions installed because then /etc/alternatives/wish and/or /etc/alternatves/tclsh point again to an unpredictable target.

had a comparable problem with the tcltls package that seems to be still depending on 8.3 | 8.4 (but works of course also with 8.5)...
don't want to fix that by hand again by rearranging some symlinks.

---

### Post by darkenergy on 2008-09-14
bump

---

### Post by Nullack on 2008-09-14
You could consider discussing your packaging dependency concerns with the devs on IRC or the devel discuss mailing list. I think creating a bug is a bit of a stretch IMHO.

---


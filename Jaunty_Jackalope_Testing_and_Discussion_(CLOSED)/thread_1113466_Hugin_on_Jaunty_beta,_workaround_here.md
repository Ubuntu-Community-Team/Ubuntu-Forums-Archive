---
title: "Hugin on Jaunty beta, workaround here"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Rallg on 2009-04-01
If you are using Hugin on Jaunty, and discover that Hugin launches but crashes at some point later, then try this:

In Hugin, Edit > Preferences > Autopano

Select autopano-SIFT (by S. Nowozin). On the first line of parameters, change it to:

autopano-complete

On the second line of parameters, change it to:

--points %p -o %o %i

Apply, OK, then re-launch Hugin. This worked for me, both for the distro Hugin and for the latest svn compiled. I haven't tried it if a different autopano is selected.

There's already a launchpad bug report, which is how I found the info.

---


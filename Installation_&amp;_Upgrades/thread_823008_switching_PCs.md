---
title: "switching PCs"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by brunods on 2008-06-08
Hey,

I'm buying a new laptop on July. I was wondering, if I just copy and paste my home folder into the new laptop, will all my user customizations go along nicely? Are there any problems on just copying it??

Thanks

---

### Post by pytheas22 on 2008-06-08
In principle, yes, everything should copy over transparently without a problem as long as you create a user account with the same name as the original system.  A common issue when doing stuff like this is that you might not be able to log in to Gnome at first because you'll get an error complaining about bad permissions for user's .dmcr directory or something along those lines, but if you do a search for the error message on this forum, the solution should be easy to find; you just need to run a couple of chown commands.  Other than that, you shouldn't have any trouble that I can see.

---


---
title: "Compiz &amp; Human Window border"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lancest on 2008-10-24
Hi there is some problem running Compiz with the regular Human Window borders. At times when deselected the Window borders fade out into strange colors. I have seen this on both machines. Any ideas how to remedy?

---

### Post by Cenotaph on 2008-10-25
as i suggested to someone on another thread with another rendering issue, i would advise you to disable render acceleration. You do this by adding the line "Option" "RenderAccel" "False" to your graphic driver section in xorg.conf

---

### Post by forumache on 2008-10-25
It is a known bug. Please search for it in launchpad and contribute there.
I am hit by a similar one (you'll find both in launchpad) where have of the titlebar dissapears. "Solved" by modify the titlebar to Glossy style (or anything else not based on Human)

---

### Post by lancest on 2008-10-25
Good suggestions. This helped me to rediscover Aging Gorilla. Looks good. I will check out Launchpad.

---

### Post by phoenix_snake on 2008-10-25
> **forumache said:**
> It is a known bug. Please search for it in launchpad and contribute there.
I am hit by a similar one (you'll find both in launchpad) where have of the titlebar dissapears. "Solved" by modify the titlebar to Glossy style (or anything else not based on Human)
this bug has been around for a long time, and someone still hasn't fixed it?

---


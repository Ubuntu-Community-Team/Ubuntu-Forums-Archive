---
title: "sudo missing"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by pau on 2006-03-13
Hi,

I in stalled dapper but am missing the sudo feature. When I try to include a user in the wheel group, so that he has access to the su features, I find out that the wheel gorup doesn't exist...

What to do?

A funny thing was that dapper didn't ask for any user... so that in the default boot I was left with the gdm and it was impossible to log in because no users existed... hahahahaha :mrgreen: 
I had to boot from rescue and from root I created a user...

---

### Post by gtkourounis on 2006-03-13
where did you get dapper drake from?

oops nevermind my question, and sorry i cant help.

---

### Post by taurus on 2006-03-13
When you create a new user from the rescue mode, make sure to add that user to group "adm" so you can use sudo again...

---


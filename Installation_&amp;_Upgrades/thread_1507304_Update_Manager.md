---
title: "Update Manager"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by shannsett on 2010-06-11
I am running version 9.04. Recently I am having difficulties installing updates being provided through Update Manager. I can perform the "Important updates" perfectly fine, but when I tried to do the "Other Updates" I get a request to insert the new Lucid Lynx version CD, which I do not have. Why is it asking for this CD?

---

### Post by cbecker78 on 2010-06-11
Most likely the cd somehow got added to your repositories and needs to be commented out or unchecked.  If you are not sure how to proceed checking that:

Can you go to a terminal (Applications -> Accessories -> terminal) and type
```
gedit /etc/apt/sources.list
```
Then copy and paste the contents here

---


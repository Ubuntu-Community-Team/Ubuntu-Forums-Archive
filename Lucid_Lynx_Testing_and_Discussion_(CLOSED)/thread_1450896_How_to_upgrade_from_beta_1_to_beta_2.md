---
title: "How to upgrade from beta 1 to beta 2"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluestar14 on 2010-04-09
i have lucid installed(beta 1), i have mentioned how i approached how i tried to upgrade in my other post..[Lucid: Can't Login]("http://ubuntuforums.org/showthread.php?p=9099765#post9099765"), is that how you do it, if not, how?

---

### Post by cariboo on 2010-04-09
I you've been keeping your beta 1 install up-to-date, there is no need to do anything with the beta 2 cd, as you're already updated to Beta 2. 

I would suggest you drop to a console and run:

```
sudo aptitude -f 
```

then run

```
 sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by HMartinho on 2010-04-09
but can "we" recover from a bad installation with beta2 cd? i'm unable to do anything with my beta1 at the moment, wondering if i could upgrade the installation with beta2 cd

---

### Post by Uncle Spellbinder on 2010-04-09
@ HMartinho

If you're having that much trouble with Beta 1, a clean install of Beta 2 would be my suggestion. Why risk the possibility of bringing any issues from an upgrade when a fresh install takes less than a half hour.

---


---
title: "Firefox Menu'"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-02-15
something caused firefox's menu's to become extremely slow, is anyone else experiencing this behavior?

I moved all mozilla/firefox files and reinstalled with the same results.

---

### Post by cariboo on 2010-02-15
Did you also remove ~/.mozilla?

---

### Post by tad1073 on 2010-02-15
> **cariboo907 said:**
> Did you also remove ~/.mozilla?

yup

Every other aspect is fine, it is just the menu's

---

### Post by lovinglinux on 2010-02-15
> **tad1073 said:**
> something caused firefox's menu's to become extremely slow, is anyone else experiencing this behavior?

I moved all mozilla/firefox files and reinstalled with the same results.

When Firefox starts to act slow, specially menus, bookmarks and the address bar, it usually means your databases are full of junk. Most of the  time there is no need to delete the profile folder. You can simply [optimize your databases](http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1). Nevertheless, this doesn't seems to be the case here.

Have you upgraded Firefox/Ubuntu recently or it just started to act weird?

---

### Post by tad1073 on 2010-02-15
> **lovinglinux said:**
> When Firefox starts to act slow, specially menus, bookmarks and the address bar, it usually means your databases are full of junk. Most of the  time there is no need to delete the profile folder. You can simply [optimize your databases]("http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1"). Nevertheless, this doesn't seems to be the case here.

Have you upgraded Firefox/Ubuntu recently or it just started to act weird?

It just started acting weird.

I think it started when I tried to copy some text on a page to do a google search for that text but I am not sure.

---

### Post by lovinglinux on 2010-02-15
> **tad1073 said:**
> It just started acting weird.

I think it started when I tried to copy some text on a page to do a google search for that text but I am not sure.

Have you installed any extensions since you moved the ~/.mozilla/firefox folder?

---

### Post by tad1073 on 2010-02-15
> **lovinglinux said:**
> Have you installed any extensions since you moved the ~/.mozilla/firefox folder?

I installed the chromiun theme, but fx was working fine after it was restarted.

---

### Post by lovinglinux on 2010-02-15
> **tad1073 said:**
> I installed the chromiun theme, but fx was working fine after it was restarted.

It's a long shot, but try starting Firefox with this command:

```
firefox -safe-mode
```

---

### Post by tad1073 on 2010-02-15
I have a clean install of firefox, as mentioned above, I removed all instances of firefox from my computer.

---


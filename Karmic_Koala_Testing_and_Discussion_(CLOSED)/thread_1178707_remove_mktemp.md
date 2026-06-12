---
title: "remove mktemp?"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by inportb on 2009-06-04
I'm getting this stuff about mktemp being removed, during update. Should I tell it to do as I say or would that result in breakage?

Thanks =D

---

### Post by rudenko_ruslan on 2009-06-04
[http://ubuntuforums.org/showpost.php?p=7401016&postcount=3](http://ubuntuforums.org/showpost.php?p=7401016&postcount=3)

---

### Post by inportb on 2009-06-04
Oh, ha. I skipped right past that thread because of the title... I s'pose a merge is called for ;)

Thanks for the link.

---

### Post by binbash on 2009-06-04
thanks for the link

---

### Post by binbash on 2009-06-05
It is fixed now

---

### Post by rudenko_ruslan on 2009-06-05
> **binbash said:**
> It is fixed now
Confirmed. "coreutils" and "mktemp" were updated without any problems.

---

### Post by pferraro on 2009-06-05
mktemp can be safely deleted now.  Read the package description.

---

### Post by taavikko on 2009-06-05
> **pferraro said:**
> mktemp can be safely deleted now.  Read the package description.

It should be then removed automatically, not by user.

---

### Post by inportb on 2009-06-05
Cool, cool. I'ma update when I get home :)

---

### Post by pferraro on 2009-06-05
> **taavikko said:**
> It should be then removed automatically, not by user.

  Previously, coreutils was trying to "conflicts" mktemp, but mktemp was an essential package, thus apt was complaining.  The coreutils update now "replaces" mktemp and will not try to remove it automatically.

The updated mktemp package is now just a transitional package.  Transitional packages are never removed automatically.  It's a method of package deprecation, before the package is removed from the repository altogether.

---


---
title: "tzdata still screwed up"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by halfB on 2007-11-09
I am still having trouble with tzdata from an upgrade attempt.  I have tried deleting it, reinstalling it, changing time zones then installing: nothing works.
Not sure how it is related but I get this when I check locales
```

oslo@oslo:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
oslo@oslo:~$


```
  
Can anyone give me direction?
thanks 
Eric

---

### Post by halfB on 2007-11-09
Well, I found that "sudo locale-gen" fixed the errors in locale.  But tzdata still is messed up.  I cannot reinstall or repair it.  Without it I am unable to do any updates.
What do I need to post to help anyone help me??
Thanks 
Eric

---


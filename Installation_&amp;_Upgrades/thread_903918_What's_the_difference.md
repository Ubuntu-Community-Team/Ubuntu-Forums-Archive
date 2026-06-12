---
title: "What's the difference?"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by d0b33 on 2008-08-28
I would like to download a Ubuntu 8.04.1 LTS ISO, but this time I would like to do a custom install and choose my packages at installation time, I was told that only the server and alternate iso's allow you to choose is this true?

So what's the difference between server, alternate and desktop variants and which one will allow a custom installation?

---

### Post by tuxxy on 2008-08-28
The normal CD would do, after install just remove anything not needed this would then be a custom install too

---

### Post by d0b33 on 2008-08-28
> **tuxxy said:**
> The normal CD would do, after install just remove anything not needed this would then be a custom install too

It might be a custom install but I would like to do a clean custom install... :(

Not possible?

---

### Post by ugm6hr on 2008-08-28
Either do a minimum install with Alternate (or [minimal]("https://help.ubuntu.com/community/Installation/MinimalCD")) CD, or a server install (with server CD), then aptitude whatever else you want on top.

If you use the alternate CD, I think you should be able to use it as a "repository" rather than downloading everything (but have never actually done this).

---

### Post by Sef on 2008-08-28
> I would like to download a Ubuntu 8.04.1 LTS ISO, but this time I would like to do a custom install and choose my packages at installation time, I was told that only the server and alternate iso's allow you to choose is this true?


I would reccommend a[ minimal install]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD") and add what you want.

---

### Post by d0b33 on 2008-08-29
Ok thanks, but what I would like to know is does the server CD allow you to choose packages? and is the alternate CD installer text based without a GUI?

---

### Post by ugm6hr on 2008-08-29
> **d0b33 said:**
> Ok thanks, but what I would like to know is does the server CD allow you to choose packages?
Yes.  But the packages available to choose are generally not useful for a desktop: databases, web server etc.

>   and is the alternate CD installer text based without a GUI?
Yes. As is the minimal CD.

There is no GUI-based installer that allows package selection.

---

### Post by d0b33 on 2008-08-29
> **ugm6hr said:**
> Yes.  But the packages available to choose are generally not useful for a desktop: databases, web server etc.


Yes. As is the minimal CD.

There is no GUI-based installer that allows package selection.

Thanks.

---


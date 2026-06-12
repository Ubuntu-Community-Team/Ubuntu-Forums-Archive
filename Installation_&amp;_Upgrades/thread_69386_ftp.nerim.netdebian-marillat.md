---
title: "ftp.nerim.net/debian-marillat/"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by hubris on 2005-09-26
Something is wrong with this

I can't use apt-get in a normal fashion because something goes wrong there

anyone has an idea?

---

### Post by bored2k on 2005-09-26
You do not need Marillat. In fact, you ar enot advised to use it.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by DJ_Max on 2005-09-26
This needs to be stickied somewhere. Do not use packages made for another distribution. Those are packages made for Debian, and you are using Ubuntu. You will run into problems.

---

### Post by matthew on 2005-09-26
In general, it isn't a good idea to use it, but because some restricted codecs have been removed from the Ubuntu repos, this is a good place to get them, but be sure to remove them from your sources.list immediately after. See this page:
[https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8](https://wiki.ubuntu.com/RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8)

---

### Post by bored2k on 2005-09-26
The problem is people not following your "click and run" method. Backports try hard to fulfill those who crave Marillat's, so anything that is not there I would just manually browse the site and download (to save myself from some application upgrade). So far, what I had on Hoary's UBP and Breezy's got me satisfied.

---

### Post by matthew on 2005-09-26
[QUOTE=bored2k]The problem is people not following your "click and run" method. Backports try hard to fulfill those who crave Marillat's, so anything that is not there I would just manually browse the site and download (to save myself from some application upgrade). So far, what I had on Hoary's UBP and Breezy's got me satisfied.[/QUOTE]
It's not actually my method, I just linked to it, but I take your point. The idea of manually browsing the site and downloading is probably much safer for the average person.

---

### Post by hubris on 2005-09-27
if i'm not supposed to use those

then why are they in the ubuntu guide for warty when it explains how to add extra repositories?

---

### Post by DJ_Max on 2005-09-27
[QUOTE=hubris]if i'm not supposed to use those

then why are they in the ubuntu guide for warty when it explains how to add extra repositories?[/QUOTE]
Warty was closer to Debian than it is now, those packages are probably for a version of Debian Warty wasn't based on and not to mention the warty guide is a bit outdated.

---

### Post by hubris on 2005-09-27
OK but i still want to install dvd support through apt-get
and i believe it comes from those repo's...

any idea's?

i'm a new to this btw

---


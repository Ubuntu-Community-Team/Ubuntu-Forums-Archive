---
title: "Compile Notepad++ on Ubuntu"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by renanrischiotto1 on 2014-08-09
Hello!

I'm wanting compile the Notepad ++ instead of using by the wine. Is it possible? 

The source code is found here: 

[http://notepad-plus-plus.org/download/v6.6.8.html](http://notepad-plus-plus.org/download/v6.6.8.html) 

Hugs!

---

### Post by Toz on 2014-08-09
From the Notepad++ webpage:
> ...Notepad++ is written in C++ and uses pure Win32 API and STL which ensures a higher execution speed and smaller program size.
It is very windows-specific and you won't be able to compile it under Linux.

If you don't want to run it under wine, have you considered alternatives like [notepadqq]("http://notepadqq.altervista.org/wp/") (a clone of notepad++) or [sublime text]("http://www.sublimetext.com/")?

---

### Post by renanrischiotto1 on 2014-08-10
Hi Toz!
Thanks for the reply =)
I did not know Notepadqq, but the program seems to have been discontinued. The Sublime I have here, but I'd really like Notepad++ or some similar as Notepadqq.
Hugs!

---

### Post by Toz on 2014-08-10
> **renanrischiotto1 said:**
> but the program seems to have been discontinued. 
The PPA only has up to Precise (12.04) included, however, the [git tree]("https://github.com/notepadqq/notepadqq") does seem to have some recent activity, so I don't think its been discontinued.

What version of Ubuntu are you running?
- If its 12.04, you can install the version (0.13)  from the PPA.
- If its a version later than 12.04, you can build the package from source yourself (version 0.20). I just did that here and it works fine.

---

### Post by renanrischiotto1 on 2014-08-10
So, I sent an email to one of the developers (I believe to be the main one), and he told me he stopped, but are considering a change in the underlying technology for development to be faster and easier contributions. But on GitHub seems to be some movement same...
I use Ubuntu 14.04.

---


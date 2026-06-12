---
title: "[SOLVED] Package Manager error"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by gemani on 2007-10-11
Hi

I'm new to Ubuntu, and recently installed Feisty Fawn 7.04. I downloaded and tried to install a .deb file of virtualbox - after waiting for ages for anything to happen, it appeared to have stalled. I logged off and back on again, and now I'm getting a Package Manager error: "The package virtualbox needs to be reinstalled, but I can't find an archive for it". I can't run Package Manager, or remove or reinstall virtualbox (or in fact anything!)   I've tried all the apt-get options I can think of, but this error persists. Can anyone tell me how to fix this?

TIA 

Ian.

---

### Post by perlluver on 2007-10-11
Did you try to reboot?

---

### Post by forestpixie on 2007-10-11
hi - 

you can try these first, but I don't think they'll work

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

[this]("http://ubuntuforums.org/showthread.php?t=445014") is exactly the same problem - solution is on second page

---

### Post by gemani on 2007-10-11
That looks like the solution - can't try it now, but I'll try later and report my results (and hopefully resolve!)  Thanks!

---

### Post by forestpixie on 2007-10-11
hope so :)

can you make sure you mark thread solved when it is

---

### Post by bapoumba on 2007-10-11
Please try:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by forestpixie on 2007-10-11
yea that's the solution in the thread - and it was your reply to me at  the time :)

---

### Post by bapoumba on 2007-10-11
> **forestpixie said:**
> yea that's the solution in the thread - and it was your reply to me at  the time :)
oh dear! Sorry, I missed the link under "this" :D
At least I'm consistent, which is not bad ^^
(/me tired..)

---

### Post by forestpixie on 2007-10-11
he he he 

I'd love to know how many of these - sudo dpkg --remove --force-remove-reinstreq virtualbox - there are kicking around - probably almost as many as there are source.list errors from automatix leaving " around the "deb.blah.blah"

---

### Post by gemani on 2007-10-11
Thanks for all your replies! dpkg <etc> did the trick :)

---


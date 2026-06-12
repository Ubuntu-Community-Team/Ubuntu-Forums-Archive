---
title: "Got an error installing SuperKaramba"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by zac851 on 2005-10-08
I thought it was all going good at first and it was checking for everything.  THen it came to this error   

> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

It wont go any further than that.  Whats that and how can I fix it?  

Thanks

---

### Post by zac851 on 2005-10-09
OK after alot of searching I finally found what what "X" was.  and I installed the x.dev.  ANyway  I redid the install and it's asking for libXext because it can't find it.  So I went to symatec and it showed it being installed so I reinstalled it.  But im still getting this  error?  ANy ideas?

checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.

---

### Post by oxalá on 2005-10-15
[QUOTE=zac851]I thought it was all going good at first and it was checking for everything.  THen it came to this error   



It wont go any further than that.  Whats that and how can I fix it?  

Thanks[/QUOTE]


I'm having the exact same problem -- haven't tried the X.dev bit yet, but from the looks of your situation that won't get me far.

he'p!

---

### Post by oxalá on 2005-10-15
'ang on...this helped me:  

[http://ubuntuforums.org/showpost.php?p=381812&postcount=4](http://ubuntuforums.org/showpost.php?p=381812&postcount=4)

Superkaramba compiled successfully!

---


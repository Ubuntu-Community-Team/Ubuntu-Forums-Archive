---
title: "broken update"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by EarlGrey on 2006-12-08
Hello, 

the system crashed while I was updating and it left me with a bad error. Usually, I fixed it by

***dpkg --configure -a***

but that now gives me an error that something is wrong with /var/lib/dpkg/updates/0024

Please does somebody now what could be the problem?

Thanks!

---

### Post by lhtown on 2006-12-09
If you can give us the exact error, someone might be able to answer your question.

---

### Post by EarlGrey on 2006-12-09
Well, the error is in Czech, I will post it and try to translate ...

**dpkg: chyba p&#345;i rozboru, v souboru `/var/lib/dpkg/updates/0024' okolo &#345;ádku 1: nový &#345;ádek v polo&#382;ce `#padding'**

translation

*dpkg: parsing error in a file `/var/lib/dpkg/updates/0024' around line 1: new line in a '#padding' element*

Thanks. I am getting desparate.

---

### Post by EarlGrey on 2006-12-10
So I found it. I tokk took the chance and deleted what seemed to be the broken file. And now it works fine :)

---


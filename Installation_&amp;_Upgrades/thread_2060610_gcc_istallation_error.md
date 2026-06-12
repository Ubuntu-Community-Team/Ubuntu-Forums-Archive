---
title: "gcc istallation error"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by Captainhero on 2012-09-20
hello!
this is my first experience in ubuntu. I'd like to istall the compiler gcc, i followed this guide
[http://solarianprogrammer.com/2012/04/13/building-gcc-4-7-on-ubuntu-12-04/](http://solarianprogrammer.com/2012/04/13/building-gcc-4-7-on-ubuntu-12-04/) and in the step where i have to compile the gcc i get an error and i don't know what i have to do.

this is a screen of the error [IMG]http://ubuntuforums.org/<a href=&quot;<a href=http://tinypic.com?ref=i1jqro&quot; target=_blank>http://tinypic.com?ref=i1jqro&quot;</a> target=&quot;_blank&quot;><img src=&quot;<a href=http://i48.tinypic.com/i1jqro.png&quot; target=_blank>http://i48.tinypic.com/i1jqro.png&quot;</a> border=&quot;0&quot; alt=&quot;Image and video hosting by TinyPic&quot;></a>[/IMG][[IMG]http://i48.tinypic.com/i1jqro.png[/IMG]]("http://ubuntuforums.org/<a href=")">

(i used the version 4.7.0and i got the 12.04 ubuntu realease)

thanks

---

### Post by spjackson on 2012-09-21
Do you already have gcc installed? You can't build gcc unless you have gcc.
```

gcc --version

```
Does 4.7 have features that you really need that the repository version doesn't?

---

### Post by Captainhero on 2012-09-21
> **spjackson said:**
> Do you already have gcc installed? You can't build gcc unless you have gcc.
```

gcc --version

```Does 4.7 have features that you really need that the repository version doesn't?


thanks man! i wasted an evening trying to solve the problem!!
i thought there wasn't a compiler already installed!

---


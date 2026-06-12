---
title: "same updates over and over"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by ajpug on 2007-07-09
Hi all,

since sometime now I am getting notifications about the same updates over and over.
At least once a day I get an update notification regarding the following:
compiz
compiz-core
compiz-gnome
compiz-plugins
libdecoration0

the thing is that it does not matter how many time I install them, I still keep getting the same update notification.
Any idea what the problem might be and how to fix it?

-Andrea

---

### Post by hotkaffe on 2007-07-10
I'm having the exact same problem.
Does anyone know how to fix this manually?

//hotkaffe

---

### Post by bapoumba on 2007-07-10
Could you please post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by bren on 2007-07-10
maybe also post your /etc/apt/preferences

to see if you have config preventing update of certain packages....

bren

---

### Post by hotkaffe on 2007-07-10
I've found the offending sources.
I removed them from the source list and the annoying update went away.

```

# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

I'll be more careful what I put in there in the future #-o

Some additional info to answer your questions.
The rest in the source list is untouched. I update from the Swedish servers.
I have no /etc/apt/preferences

Thanks for the hint.

---

### Post by bapoumba on 2007-07-10
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html]("http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html")
There is a contact form on treviño's blog, with an email. It may be a good idea to have him check this (I could not find a "bug report" or similar, but I did not look much).

---

### Post by hotkaffe on 2007-07-10
Done.

---

### Post by ajpug on 2007-07-10
Thank you all for helping with this. Looking forward to Trevino's response.

ajpug

---

### Post by Treviño on 2007-07-10
**This is _not_ a problem**... Simply that repository is a *bleeding edge repository* with software compiled quite every day from git... That's why there are many updates!

You can find more informations about that in many places around the web (I got also dugg), but this is the main post about compiz fusion in this forum: [http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615).

---

### Post by hotkaffe on 2007-07-11
Thanks Treviño  for making that clear.
I failed to see the git dates on the packages.

I guess a "no problem - nothing to see here" is in order if this was what Andrea experienced.

---

### Post by bapoumba on 2007-07-11
Many thanks Treviño for taking the time to answer :)

---


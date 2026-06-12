---
title: "comix and unrar problems"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by shallow on 2007-12-12
i loved CDisplay for windows and i have hundreds of comics i now have on a test pc with the newest Ubuntu
CDisplay sadly is only for windows but i read that Comix would be a good reader for *.cbr (comic files)
yes i know they are *.rar files

so in add remove i downloaded comix no issues i double clicked my comic and i get an error
"Could not find the unrar executable. please install it if you wish to open RAR archives."

so i went back to add remove to see this unrar was there nope did a search and found a place to download it
"http://www.icewalkers.com/Linux/Software/53000/unRAR.html"

it downloads as a *.tgz file i unzip it and its a folder with a bunch of stuff in it
(oh yeah i am a noob)

others who have used comix how am i able to look at *.cbr files or how the heck do i get this unrar installed or what other program out there will let me view my comics on Linux like CDisplay does

---

### Post by shallow on 2007-12-14
still looked around and i couldnt find any other help on this
:(

---

### Post by arsenic23 on 2007-12-14
Have you enabled multiverse and universe repositories?  ( either with the preferences in Add/Remove or by uncommenting the lines in /etc/apt/sources.list )

unrar may be in one of those repos, I know I installed it from apt.

____________________
EDIT:
After looking into this I noticed that when I use Add/Remove to search for unrar it fails to show up as well, even though I know I can install it from the repos.  You may want to try using the terminal and installing it by typing:
```
sudo apt-get install unrar
```

---

### Post by rorshach on 2008-02-11
thanks, i was having the exact same problem and that command line sorted it right out :)

---

### Post by masque7 on 2008-02-15
yep thanks, sorted me out too:KS

---

### Post by Volkgeist on 2008-02-24
Thanks too!
Exactly what i was needing. :)

---

### Post by rememberme2016 on 2008-05-02
perfect. thanks.

---

### Post by laurielegit on 2008-07-01
> **arsenic23 said:**
> 
```
sudo apt-get install unrar
```

RUN!! He's getting technical. Thanks for this explanation, it realy helped me. thanks again.

---


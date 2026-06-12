---
title: "Spotify For Linux"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by Th3Blaze on 2010-09-27
[http://www.spotify.com/uk/download/previews/](http://www.spotify.com/uk/download/previews/)

I don't have permission to add the first thing and I cant find my root user on the list.

I am an administrator.
Any help?

Thanks In Advance  

- Luke . I -

---

### Post by sinaen on 2010-10-21
Ok... i thougt i had a sollution, what you need is to find how to ad repositories in ubuntu,

I recently moved from windows 7 to ubuntu (again) it has changed alot since last time i saw it.

but thats the only way there is right now.

Hope youll find your sollution, its always easyer and more fun to do this yourself so that youll learn to next time :-)

---

### Post by howefield on 2010-10-21
> **Th3Blaze said:**
> I don't have permission to add the first thing and I cant find my root user on the list.

Open a terminal and use...

```
gksudo gedit /etc/apt/sources.list
```

to open your software sources and place the line

```
deb http://repository.spotify.com stable non-free
```

at the end of the file on a new line, save and close. Then carry on with the rest of the instructions.

---

### Post by sinaen on 2010-10-21
Ok... i was in the wrong place in search for sources.list, not that much changed... after all

Edit: This was a bit suprising, the spotify client only support premium accounts, that feels a bit unfair :-(

---


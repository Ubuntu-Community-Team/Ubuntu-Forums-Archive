---
title: "Gnucash won't start"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Turtle.net on 2011-04-13
I'm using gnucash really often.
Today gnucash refused toto start.
When launched from the terminal I get the error :
```
ERROR: file: "libguile-srfi-srfi-13-14-v-1", message:"file not found"
```

To make sure that gnucash has all its dependencies installed i reinstalled it : nothing changed
I then upgraded to the latest version (from getdeb) : nothing changed

Any idea ?

---

### Post by Turtle.net on 2011-04-13
I found a way to start it again !
```
$ sudo ln -s /usr/lib/libguile-srfi-srfi-13-14-v-1.so.1 /usr/lib/libguile-srfi-srfi-13-14-v-1.so

```

Now Gnucash start again.

:)

That doesn't solve the problem though.

Is it a Gnucash bug or a guile one ?

---

### Post by Dutch70 on 2011-04-13
Did you try running the following to see if that fixed it?
```
sudo apt-get install -f
```

edit: Haa, nevermind. I'm sure if you've been around since 2005, you've tried that one. :p

---

### Post by Turtle.net on 2011-04-13
The package was not broken or anything.
For a good measure I purged gnucash and all it's dependencies, and reinstalled them.
I tried a bunch of things until I realised that gnucash was not finding the lib because le file ended in .so.1

That's why I created the link.

Thanks anyway for your help (eventhough I have been here a long time ... I'm far from mastering my system)

I posted a bug to the guile mailing list. We will see what happen.

---


---
title: "Error on startup"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Sinani201 on 2010-10-10
I installed Ubuntu 10.04 with Wubi earlier today. I upgraded to 10.10, and when I started it up, I get this error message:

```
error: file not found
error: file note found
error: no suitable mode found
```

It shows up on the screen for about 3-4 seconds, and then disappears and restarts my computer.

There is some command line stuff that shows up onscreen before that, but it flashes and goes away so fast I can't read it.

---

### Post by bcbc on 2010-10-11
> **Sinani201 said:**
> I installed Ubuntu 10.04 with Wubi earlier today. I upgraded to 10.10, and when I started it up, I get this error message:

```
error: file not found
error: file note found
error: no suitable mode found
```

It shows up on the screen for about 3-4 seconds, and then disappears and restarts my computer.

There is some command line stuff that shows up onscreen before that, but it flashes and goes away so fast I can't read it.

Upgrades to 10.10 from wubi are not supported yet. The 10.10 release notes state this clearly (for exactly the reason you are describing).
Why didn't you just install a 10.10 wubi instead? It would have been quicker. You can download the 10.10 desktop .iso and write it to CD and install it from there.

---

### Post by Sinani201 on 2010-10-11
The wubi download from Ubuntu's website is still 10.04, unless they updated it today.

---

### Post by bcbc on 2010-10-11
[http://people.canonical.com/~evand/wubi/maverick/](http://people.canonical.com/~evand/wubi/maverick/)

Try the most recently updated (Oct 7). Otherwise, just mount the .iso and extract wubi.exe from there. Or search for maverick wubi.exe - there are some other links where people have downloaded it.

---


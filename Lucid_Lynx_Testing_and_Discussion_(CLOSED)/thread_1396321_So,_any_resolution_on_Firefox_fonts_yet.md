---
title: "So, any resolution on Firefox fonts yet?"
date: 2010-02-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-02-01
Hi,
Now that 3.6 is out and the fonts issue still hasn't been fixed, is there anyone working on fixing it before Lucid is out?
If I was Canonical I'd make sure this glitch is fixed, it's gonna be an LTS and it's expected that many newbies will be adopting Ubuntu and will be disappointed that the browser has "visual glitches" and hence (silently) decide that "firefox & windows are better for browsing".
It's one of those issues that only **seem** to be a "minor" annoyance. Also, imho before even thinking competing for serious with Mac OS we should at least fix the obvious stuff, otherwise it's plain vapor-ware.

---

### Post by Seventh Reign on 2010-02-02
Huh? Fonts are perfect in Firefox 3.6 with my new monitor.  They were perfect in 3.5 too...

Acer 20" Widescreen

---

### Post by portis on 2010-02-02
You can add this ppa:

[https://launchpad.net/~mdeslaur/+archive/testing/+packages](https://launchpad.net/~mdeslaur/+archive/testing/+packages)

> **kahumba said:**
> Hi,
Now that 3.6 is out and the fonts issue still hasn't been fixed, is there anyone working on fixing it before Lucid is out?
If I was Canonical I'd make sure this glitch is fixed, it's gonna be an LTS and it's expected that many newbies will be adopting Ubuntu and will be disappointed that the browser has "visual glitches" and hence (silently) decide that "firefox & windows are better for browsing".
It's one of those issues that only **seem** to be a "minor" annoyance. Also, imho before even thinking competing for serious with Mac OS we should at least fix the obvious stuff, otherwise it's plain vapor-ware.

---

### Post by vade on 2010-02-02
What font issue? For me fonts look slightly different on firefox than on the rest of ubuntu desktop, but the difference is so small that it doesn't matter.

---

### Post by glasen on 2010-02-02
> **vade said:**
> What font issue?
The original Firefox builds don't support the subpixel-hinting method (LCD-filter aka Cleartype-style rendering) which is integrated in Ubuntu since many releases.

This means if you have activated this hinting-method, Firefox looks somehow strange in comparison to other programs.

---

### Post by kahumba on 2010-02-02
Attached. Two pictures are worth a thousand words.
**ok-after.jpeg** is how firefox renders **after** I fix this "glitch" with this solution:
[http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387)

this issue is almost a year old and nobody bothered fixing it. I'm sure a newbie will have to spend a lot of time to find that post to fix the issue (if he doesn't screw his system trying other solutions before that), but most (newbies) won't bother at all, will just go back to windows.

EDIT: and btw Chrome (using version 4 dev-channel) doesn't have this problem, so it's Firefox's fault.

---

### Post by glasen on 2010-02-02
This is a completely other issue and has nothing to do with the current problem.

The problem here discussed could only be solved by applying a patch and recompiling Firefox.

Non-working subpixel-hinting :

[[img]http://www.ubuntu-pics.de/thumb/40706/before_0ySYVu.png[/img]](http://www.ubuntu-pics.de/bild/40706/before_0ySYVu.png)

Working subpixel-hinting :

[[img]http://www.ubuntu-pics.de/thumb/40705/after_uo0sls.png[/img]](http://www.ubuntu-pics.de/bild/40705/after_uo0sls.png)

Just compare the "D" of "Datei" (German for "file") and the "A" of "Anwendungen" (German for "applications") of both pictures.

---

### Post by kahumba on 2010-02-02
If you're talking to me: frankly I don't think so. Google Chrome features good fonts by default without having me, the user, to recompile anything. If code needs to be changed inside Firefox - then do it, chop chop!! Period.

---

### Post by glasen on 2010-02-02
Yes, i know it is a Firefox problem and Chrome doesn't have this problem.

BTW, we are discussing about a problem in a **Alpha** version of a distribution.

---

### Post by kahumba on 2010-02-02
> **glasen said:**
> 
BTW, we are discussing about a problem in a **Alpha** version of a distribution.
Yes, but it doesn't matter it this case, cause this issue is also present in Karmic, actually since Firefox 3.5 was out.

---

### Post by ToxinPowe on 2010-02-02
Any fix for this problem in Karmic?

---


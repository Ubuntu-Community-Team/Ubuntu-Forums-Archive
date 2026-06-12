---
title: "Firefox Closing Without Explanation"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by quazi on 2008-10-19
Ever since upgrading to Intrepid from Hardy, I've had to deal with Firefox just closing spontaneously after a random amount of time browsing (sometimes it goes a whole day without choosing to close itself).  I tried running it in terminal to get some output, but this is all I got:
```
$ firefox
\Aborted (core dumped)
$

```

I'm running with compiz and flash-nonfree version 10.  I've making a new ~/.mozilla/firefox directory, but that was no help.  Any ideas what might be causing this, or some way I can get firefox to give me some useful output?

---

### Post by [Neurotic] on 2008-10-19
Just so you know, I have *exactly* the same issues, and couldn't get any more debug data out of it than that.

---

### Post by psyke83 on 2008-10-19
> **quazi said:**
> Ever since upgrading to Intrepid from Hardy, I've had to deal with Firefox just closing spontaneously after a random amount of time browsing (sometimes it goes a whole day without choosing to close itself).  I tried running it in terminal to get some output, but this is all I got:
```
$ firefox
\Aborted (core dumped)
$

```

I'm running with compiz and flash-nonfree version 10.  I've making a new ~/.mozilla/firefox directory, but that was no help.  Any ideas what might be causing this, or some way I can get firefox to give me some useful output?

Are you using 32bit or 64bit? Ensure the "libflashsupport" package is *not* installed.

---

### Post by [Neurotic] on 2008-10-19
I'm on 32bit, and libflashsupport is not installed.

---

### Post by psyke83 on 2008-10-19
> **'[Neurotic] said:**
> I'm on 32bit, and libflashsupport is not installed.

I suspect it's a plugin issue. The next time your browser session crashes, examine your history and see what websites trigger the crash. It's very likely to be a problem with the Flash or Java plugins.

---

### Post by [Neurotic] on 2008-10-19
I know [www.theage.com.au](www.theage.com.au) will commonly crash my browser.

---

### Post by quazi on 2008-10-20
I tried ```
$ sudo apt-get purge firefox flashplugin-nonfree
``` which removed flash, firefox, and the java6 plugin.  I then moved up my ~/.mozilla directory so as far as I knew, I was running a perfectly clean firefox installation after I ran ```
$ sudo apt-get install firefox
```  

I logged into igoogle and upon clicking on a google news link, firefox closed with the same (lack of) output as before.  This problem is getting extremely annoying and I'd rather not be forced to do a clean install of Intrepid to rectify it.

---

### Post by SpenceMakesSense on 2008-10-20
well before doing anything hastey just try a diferent browser. I've heard good things about opera...or kazehakase

---

### Post by quazi on 2008-10-23
Well, turns out that browsers hates me:
```
$ opera
Aborted (core dumped)
$

```

If I had to guess I'd say it was a flashplayer/java issue, but I removed both the flash plugin and the sun java6 plugin.

Any ideas why both opera and firefox are crashing inexplicably?

---

### Post by quazi on 2008-10-26
Quick update, this problem occurs both with and without compiz running.

---

### Post by FDBuff77 on 2008-10-27
First post!

Same issue. I updated to Intrepid the other day and immediately started having the spontaneous Browser abortions (Firefox & Opera). I removed libflashsupport and the flash plugin. I reinstalled all plugins with no change. If I disable both the flash and java plugins in Firefox I can browse, but obviously in a limited capacity. I am hoping that this gets fixed when the final 8.10 comes out in 4 days...

---

### Post by FDBuff77 on 2008-10-29
New development: even with those afore mentioned plugins disabled and/or removed completely I am still getting browser crashes. Very frequent now too...

---

### Post by FDBuff77 on 2008-10-30
Jeez just call me "Thread Killer!"

---


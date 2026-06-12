---
title: "Is there a test suite to find out why multiple graphics programs crash on startup?"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by rocksockdoc on 2010-09-09
Is it common for multiple graphics programs to crash upon startup (IBM X61 laptop, Ubuntu 10.04)? What do I do about it? [COLOR=DarkRed][B]

Is there a test suite that can help me identify WHY multiple programs crash upon startup?[/B][/COLOR]

Most of my programs (installed using the Ubuntu Software Center) work just fine, e.g., 
- The Gimp 2.6.8
- fotoxx v.8.7
- F-Spot 0.6.1.5
- gpaint 0.3.3
- Inkscape 0.47
- mtPaint 3.31
- Xara Xtreme 0.7
- Xfix 3.2
- XPaint 2.8.13
etc.

But a few others crash immediately upon startup, e.g.,
- KolourPaint
- Krita
- KSnapshot
etc.

**Is there a test suite I can run to identify & resolve the cause of the crashes on my computer?**

---

### Post by grief -l on 2010-09-09
Look in /var/logs for error reports

---

### Post by rocksockdoc on 2010-09-10
> **grief -l said:**
> Look in /var/logs for error reports

OK. In the terminal, I cd to /var/log (not /var/logs);
I do an "ls -ltr" to find the last logs written (namely auth.log, mail.err, mail.info, etc.);
So I "tail -f auth.log" to see, realtime, what it's reporting.
I then start up "Applications->Graphics->KolourPaint";
It crashes immediately;
Back in the terminal, I "ls -ltr" to find auth.log is still the last written log.
Bummer. 

I try with "Applications->Graphics->Krita", with the same result. The last write of the auth.log was about 10 minutes prior to this test.

Likewise with KSnapshot. 

**[COLOR=DarkRed]Is there another crash debugging sequence?[/COLOR]**

(BTW, isn't it strange all the failed programs start with "K".)

---

### Post by Elfy on 2010-09-10
Try running them from a terminal - see what messages you get when they crash.

Also you can see if there any options from the terminal - sometimes ... 

```
ksnapshot --help
```

---

### Post by rocksockdoc on 2011-03-10
I solved the problem by backing out almost every program I had installed, and, then re-installing the problematic programs.

Whatever it was that was causing multiple programs to crash, disappeared. 

Go figure.

Thanks for the help.

I hope this helps others with the same crashes.

---


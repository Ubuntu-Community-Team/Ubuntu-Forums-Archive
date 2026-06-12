---
title: "Upgrades broke gscan2pdg - Whom complain?"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by jreinis on 2008-07-04
Now upgrades broke behavior of gscan2pdf, sometimes it frezees on importing djvu into tiff.

Again question How to fix it?
Reinstallation does NOT help as in my previous thread about Nero 3.5

Damn!

---

### Post by JeffreyRatcliffe on 2008-07-05
> **jreinis said:**
> Now upgrades broke behavior of gscan2pdf, sometimes it frezees on importing djvu into tiff.

Which version of gscan2pdf are you using?

---

### Post by kafkaian on 2008-09-13
I'm locked out of the original scan2pdf thread but the latest problem I'm having is with respect to the scanning of one page at a time (regardless of All or # selection). Seems that it will only continuously scan regardless of the type of scanner.

scan2pdf v0.9.26

Linux ubuntu 2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux

---

### Post by JeffreyRatcliffe on 2008-09-13
> **kafkaian said:**
> I'm locked out of the original scan2pdf thread

Everybody is - it's been closed due to its age (the fact that it was still active seemed to have been irrelevant).

> **kafkaian said:**
> but the latest problem I'm having is with respect to the scanning of one page at a time (regardless of All or # selection). Seems that it will only continuously scan regardless of the type of scanner.


Start gscan2pdf with --debug, try to scan, and post the output from the command line.

---

### Post by kafkaian on 2008-09-13
Closed? - such a great and relevant thread. Bizarre

And I'm still having to clear the cache in places to get the output choices up

Anyway:

NOTE: Now not needed

---

### Post by JeffreyRatcliffe on 2008-09-13
> **kafkaian said:**
> Closed? - such a great and relevant thread. Bizarre

They've done it by date, not relevance.

> **kafkaian said:**
> And I'm still having to clear the cache in places to get the output choices up

If you can reproduce having to clear the cache (i.e. explain in small steps), I'll do my best to fix it.

But for your current problem, you forgot to try and scan before sending me the commandline output.

---

### Post by kafkaian on 2008-09-14
No longer needed as not a problem to resolve

---

### Post by JeffreyRatcliffe on 2008-09-15
> **kafkaian said:**
> the latest problem I'm having is with respect to the scanning of one page at a time (regardless of All or # selection). Seems that it will only continuously scan regardless of the type of scanner.

What do you mean by type of scanner? Do you have several scanners?

In the output you post, gscan2pdf scanned 2 pages. You scanner doesn't seem to have an ADF. I assume therefore, that you asked for 1 page and got 2?

---

### Post by kafkaian on 2008-09-17
Sorry for the delay, 

No, I just have the one scanner, but if I check "All pages" the scanner scans indefinitely. Similarly, if I check say 3 pages, it will not wait for me to load each page (old manual flat bed scanner) and will just scan 3 pages regardless.

---

### Post by kafkaian on 2008-09-28
Apologies Jeffrey. Clearly my mind wasn't on things last week. The clear cache issue must've reset my page options. When I just leave the # at 1, everything is as should be.

Sorry if you spent time that would otherwise be spent on more precious concerns

---


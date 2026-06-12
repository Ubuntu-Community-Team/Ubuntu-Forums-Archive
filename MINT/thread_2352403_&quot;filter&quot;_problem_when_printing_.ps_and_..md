---
title: "&quot;filter&quot; problem when printing .ps and .pdf"
date: 2017-02-12
forum: MINT
---

### Post by engine on 2017-02-12
same hardware that's been doing the job for years, but now I can no longer print .pdf or .ps files

system message says "There was a problem processing document {name}", and answering the questions behind the [Diagnose] button doesn't diagnose anything

CUPS says more succinctly "job state: filter failed"

How do I find / install this filter? Ubuntu 16.04.1 LTS, HP Deskjet840C.

---

### Post by engine on 2018-01-28
[bounce] so there's somebody out there who knows enough to include an error trap in the code, but nobody out there who knows enough to understand and correct the error!

---

### Post by dragonfly41 on 2018-01-28
There is this very, very old thread which discusses solutions ..

[https://bbs.archlinux.org/viewtopic.php?id=148850](https://bbs.archlinux.org/viewtopic.php?id=148850)

One poster suggests clearing cache.

And another ... [https://serverfault.com/questions/602523/cups-is-not-printing-with-filter-failed-message-how-to-get-more-info](https://serverfault.com/questions/602523/cups-is-not-printing-with-filter-failed-message-how-to-get-more-info)

and another ... [https://askubuntu.com/questions/378873/cant-print-any-more-stopped-filter-failed](https://askubuntu.com/questions/378873/cant-print-any-more-stopped-filter-failed)

---

### Post by engine on 2018-01-28
Thanks! I've also turned up a reference to "Bug #1718215 versions of cups-filters and libqpdf do not match" … the report concludes succinctly that
> release 1.17.5-1ubuntu1 got uploaded to solve this problem

I don't know enough to understand whether the release number refers to the ubuntu platform or the cups-filters package :-} so I'll mention that my platform version is Linux Mint 18.1 Serena (release: 18.1) and the cups-filters version installed is 1.8.3-2ubuntu3.1
Might the answer be that I need an updated version of cups-filters? if so, how do I find and install it?

---

### Post by vasa1 on 2018-01-28
Thread moved to the "MINT" forum.

---


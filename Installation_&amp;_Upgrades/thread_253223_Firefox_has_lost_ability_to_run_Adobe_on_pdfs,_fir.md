---
title: "Firefox has lost ability to run Adobe on pdfs, firefox and mozilla-acroread OK"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by leemckusic on 2006-09-08
Firefox has lost ability to run Adobe on pdfs, firefox and mozilla-acroread have been apt-get'ed.

Having a glitch following upgrade from Breezy to LTS 6.06.

Solution found, not the best but it works:

In the Firefox help pages is a link to the Adobe website.
Download the tar.gz file for Linux, unpack it and install it:
Site:
[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)
Unpack:
tar -zxf .... filename
Find in new subdirectory file named Install. 
sudo ./Install
Answer yes to questions and "no" to the final manual install question.

The default brower, Firefox previously started adobe acrobat reader when a web link fetched a pdf file. 

apt-get install shows both firefox and mozilla-acroread were installed.

dpkg-reconfigure on each package does not cause any menu or change.

Darn, this seems like something real obvious ...

When the browser loads a PDF file, view page source shows the pdf file was fetched. A previous install glitch with broken cups printing was simply fixed by remove the existing printer and add it again. I can't figure out a comparably simple fix for adobe pdf reader. A different firefox add-in, RSS reader still works despite the upgrade.

---

### Post by dugh on 2006-09-08
This forum is about installing Ubuntu itself.  You might have better luck posting your question on another one of the sub-forums here, or else asking on the #ubuntu channel on irc.

---


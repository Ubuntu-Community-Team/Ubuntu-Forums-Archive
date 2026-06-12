---
title: "problem with eclipse and jar apps after hardy install"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by erdomi on 2008-08-28
I just upgraded to hardy. Now when I use eclipse and try to run a java application, all of the windows pop up, but I can't click any buttons and if I move one window off of another, the window from below does not reanimate. By the way, I have tried several versions of eclipse and have the same problem in all of them.

Also, if I try to run the application as a jar file, the same thing happens.  Has anybody had this problem?  I don't get any error messages and so my solution search has come up with nothing.  Thanks!

---

### Post by jamesstansell on 2008-08-29
I don't think I've ever seen an error like that.  Is it only with an app that you've created?  Or does it happen with other apps too?

When you say you don't get any output, have you tried starting it from the command line?

Which Java virtual machines(s) have you tried running it with?

---

### Post by erdomi on 2008-08-30
Thanks for your response! It turns out that even though I had java 1.6 installed as default (java -version gives java 1.6), eclipse was still using java 1.5, and some of the libraries i was using require 1.6.  i changed the jre in eclipse to java 1.6 and its not working fine :)

Thanks!

---


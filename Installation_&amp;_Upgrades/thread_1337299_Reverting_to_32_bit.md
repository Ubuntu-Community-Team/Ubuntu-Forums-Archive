---
title: "Reverting to 32 bit"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by mousestalker on 2009-11-25
When I upgraded to 9.10 I lost some critical functionality with Firefox. I haven't been able to restore it but my friend who has 32 bit 9.10 can do what I can not (It's a flash and javascript issue combined).

How do I go from 64 bit to 32 bit?

A complete install or is there an easier way?

What other pointers, issues or suggestions does the community know about?

---

### Post by steven1664 on 2009-11-25
Do you have flash and java installed on your system.  If you dont have them then they aren't going to work.  You can go to your terminal and type

sudo apt-get install flashplayer-mozilla

There are many versions of java to choose from just the jre should work for you.  Go to your terminal and type:

sudo apt-get install sun-java6-jre

That should fix your issues.

---

### Post by mousestalker on 2009-11-25
I do have flash and java. They are both as current as possible. I still can not view tiffs in firefox (although I can in opera, opera just has severely limited functionality because of the particular website's design).

So it looks like switching to 32 bit is the only solution.

---

### Post by dhavalbbhatt on 2009-11-25
> **mousestalker said:**
> I do have flash and java. They are both as current as possible. I still can not view tiffs in firefox (although I can in opera, opera just has severely limited functionality because of the particular website's design).

So it looks like switching to 32 bit is the only solution.

I don't think this is a 32bit vs 64bit issue. I am sure there are certain things that are very specific to your scenario which are causing flash and jave to not work the way you want them to work. As a side, have you tried installing chorme? Chrome does a really good job with java and flash pluggins.

---

### Post by mousestalker on 2009-11-25
Chrome on linux? It isn't available through Synaptic.

I know that I can view and print tiff documents off of the GSCCCA website ([www.gsccca.org](www.gsccca.org)) in 32 bit. I know that with similarly upgraded plugins I can not on 64 bit.

Hence my query.

---

### Post by dhavalbbhatt on 2009-11-25
> **mousestalker said:**
> Chrome on linux? It isn't available through Synaptic.

I know that I can view and print tiff documents off of the GSCCCA website ([www.gsccca.org](www.gsccca.org)) in 32 bit. I know that with similarly upgraded plugins I can not on 64 bit.

Hence my query.

Yes, Chrome is available for Ubuntu. Follow the link here -

[http://ulyssesonline.com/2009/11/02/install-google-chrome-on-ubuntu-9-10/](http://ulyssesonline.com/2009/11/02/install-google-chrome-on-ubuntu-9-10/)

Again, I don't think this is a 32bit vs 64bit issue. It must be the way you have installed flash/java on your computer. I have had similar issues in the past, but I have been able to completely remove flash and re-install it again (I must admit that is a painful process though!).

PS: I just noticed you had "upgraded" to 9.10. That is a cause of many issues - I usually like to do a fresh install with any Ubuntu release.

---

### Post by mousestalker on 2009-11-25
I was able to view and print the site in Chromium. Thank you!

Now I can get my work done exclusively in Linux.

:D

---


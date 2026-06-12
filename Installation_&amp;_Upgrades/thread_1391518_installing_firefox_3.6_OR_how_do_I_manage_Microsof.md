---
title: "installing firefox 3.6 OR how do I manage Microsoft Adcenter in Ubuntu?"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by starsprout on 2010-01-26
Hi,

I'm trying to manage search ads at bing.com using linux, but MS says "incompatible browser" (running firefox 3.5.7) even though Microsoft says firefox is compatible. (huh!)

I've downloaded firefox version 3.6 but it's a tar.bz2 file and even after I unzip it I can't find a ./configure or make option, so I'm stuck.

How do I install Firefox 3.6 in Ubuntu 9.10?

OR

How do I manage search ads at Bing.com without using Windoze or Wine, or Virtual PC or any other emulator?

Thanks!

---

### Post by adam814 on 2010-01-26
You might try using the "User Agent Switcher" addon for Firefox to report your browser as IE7 on Vista or something like that.  Of course if it actually needs Windows-only stuff (ActiveX controls for example) it won't help.  But if they're simply denying you for having a browser report it's running on Linux it'll do the trick.

As for Firefox 3.6, there's a "Mozilla Daily Builds PPA" out there that will have 3.6 packages.  Most source packages have a file named README in the source directory that gives info on how to build and install it.

---

### Post by starsprout on 2010-01-26
> **adam814 said:**
> You might try using the "User Agent Switcher" addon for Firefox to report your browser as IE7 on Vista or something like that.  Of course if it actually needs Windows-only stuff (ActiveX controls for example) it won't help.  But if they're simply denying you for having a browser report it's running on Linux it'll do the trick.

As for Firefox 3.6, there's a "Mozilla Daily Builds PPA" out there that will have 3.6 packages.  Most source packages have a file named README in the source directory that gives info on how to build and install it.


That is an awesome idea! I will give it a try and report back...

Thanks!

---

### Post by starsprout on 2010-01-26
Well that was a neat trick! ;-)

The browser error disappears with user-agent switcher plugin. Thanks! I'll dig around tomorrow to see if it works all the way through (I'd hate to have to login to Windoze, ugh).

Still wondering how to install Firefox 3.6 in Ubuntu, but I'd call this thread resolved for now.

Thanks!!!

---


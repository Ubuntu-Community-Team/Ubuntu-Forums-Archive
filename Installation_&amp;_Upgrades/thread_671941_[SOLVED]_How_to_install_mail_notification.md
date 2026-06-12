---
title: "[SOLVED] How to install mail notification"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by SteveLaw on 2008-01-19
Hi,

Brand new to ubuntu.  Long time windows user, dual-booting to see if I can live without...

Anyway, I have multiple email accounts and I want some kind of notifier (I used Pop Peeper in Windows but I haven't even begun to figure out wine yet and wanted to go as "native" as possible for now).  

I found mail notifier which would seem to fit the bill, but...

I tried the tar.gz and followed the install instructions but I got "configure: error: C compiler cannot create executables".  So I then downloaded the ubuntu package and I get the error "Dependency is not satisfiable: libsal2"  What does that mean?  

How do I install it?  Is there a better alternative?  

Thanks for any help.

---

### Post by kostkon on 2008-01-19
Did you search the Ubuntu repositories for one? I know that there are some. Go to *Add/Remove* and do a search. If you don't find something you like, open *Synaptic* to search the full package listing of the repositories for one.

---

### Post by Partyboi2 on 2008-01-19
xlassie, xmailbox and coolmail are a few other ones.
You can install them by Synaptic Package Manager or
```
 sudo apt-get install <Package name>
```Change <Package name> to the name of the package


Edit: Welcome!

---

### Post by SteveLaw on 2008-01-19
Well that was easier than expected!

*sudo apt-get install mail-notification* worked.  I'll have a look at the others as well. 

Thanks to both.

---


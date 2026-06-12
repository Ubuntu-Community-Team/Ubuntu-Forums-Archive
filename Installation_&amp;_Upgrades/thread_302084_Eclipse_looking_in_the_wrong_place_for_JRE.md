---
title: "Eclipse looking in the wrong place for JRE?"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by lucasl on 2006-11-18
Hi,
I installed eclipse and when I try to run it, I get this error:
"A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java"

I'm guessing I just use ln, but I don't really know. Any ideas?

PS. I just used the package in Add/Remove.

---

### Post by DaveBorealis on 2006-11-18
> **lucasl said:**
> No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

Find out where the JRE or JDK was installed, and add it to Eclipse's path.  I'm rusty with Java nowadays, but somewhere there's a configuration file where you can add it.  Recently there was a thread posting the solution to this problem, so a search should turn up the specifics!

Best regards,
Dave

[edit] This link I believe answers your question, and it should have other info you might find of use: [http://ubuntuforums.org/showthread.php?t=201378]("http://ubuntuforums.org/showthread.php?t=201378")

---


---
title: "[SOLVED] Error during Distribution Upgrade (7.04 -&amp;gt; 7.10)"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by sakoman on 2008-07-03
Shortly after the upgrade begins I get the following error: "Failed to fetch [http://www.openembedded.org/dl/packages/Packages.gz](http://www.openembedded.org/dl/packages/Packages.gz) 302 Found"

I've checked and this file does not exit at openembedded.org.  Any idea why the Update Manager might be looking for this?  Or how to work around this error?

---

### Post by SkonesMickLoud on 2008-07-03
Clicking the link goes directly to a package download.

---

### Post by sakoman on 2008-07-03
I solved the issue by using the Synaptic Package Manager to remove openembedded.org from the repo list.

---

### Post by SkonesMickLoud on 2008-07-03
Good to hear.  Sorry I couldn't be more help earlier, beer was calling!

If you would, please mark this thread as solved.  It should be under "Thread Tools" at the top of the page.

---


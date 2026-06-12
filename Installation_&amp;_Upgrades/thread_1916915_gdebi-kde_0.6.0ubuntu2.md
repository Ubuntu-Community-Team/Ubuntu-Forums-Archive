---
title: "gdebi-kde 0.6.0ubuntu2"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by wjpowers on 2012-01-29
I was trying to upgrade kdebase-runtime to version 4.4.4.5-0ubuntu1.1.  I kept getting a dependency trail that went as follows:
kdebase-runtime -> kdelibs5 -> kubuntu-debug-installer -> kpackagekit ->
software-properties-kde -> install-package -> gdebi-kde -> gdebi-core

It turns out I do not have gdebi-kde 0.6.0ubuntu1 installed, but I do have gdbei-core 0.6.0ubuntu2 installed.  Apparently, I cannot install gdebi-kde 0.6.0ubuntu1 because it depends upon gdbei-core 0.6.0ubuntu1, which is not installed.  There is a gdebi-kde 0.6.0ubuntu2 available, but not from synaptic.  

So what should I do?  
Should I not upgrade kdebase-runtime now and wait until ubuntu has gdebi-kde 0.6.0ubuntu2 ready, or should I install the 0.6.0ubuntu2 version available off the web?

Thanks, bill powers

---

### Post by wjpowers on 2012-01-31
:p The problem was that I had too many related packages locked (pinned).  The issue appears to be resolved now.

---


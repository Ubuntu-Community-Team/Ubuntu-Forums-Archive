---
title: "how to automate 2 lines of shell during boot"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by doobya on 2006-02-28
Howdy,

I'm using a java software package called Confluence on ubuntu breezy badger.  To start it I need to log in and type 2 lines of code in a shell window.  What's a reasonable way to make this happen automagically when I turn the box on?  Confluence is a web application which I use remotely from other machines on the network.

doobya@dingleberry:/usr/local/bin$ export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
doobya@dingleberry:/usr/local/bin$ sudo confluence-2.1.4-std/bin/startup.sh
Password:

Cheers for the help
Chris

---

### Post by taurus on 2006-02-28
You can add PATH and export to your ~/.bashrc.

---


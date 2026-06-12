---
title: "how to install mozilla-mplayer in ubuntu 10.04?"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rukshanchristy on 2010-04-13
Hi   I have upgraded my ubuntu version from 9.10 to 10.04 and now I have a problem getting mplayer plugin to work in firefox.  It was working fine before the upgrade.

In ubuntu 9.04 when I browse a page which has divx streaming it shows a button "install missing plugins" and when i click it shows a list of plugins available (mplayer plugin was one of them), in 10.04 that list is empty.  

Then i tried the following:  

```
 $sudo apt-get install mozilla-mplayer 
```It gives me the following message
```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, 
or is only available from another source
E: Package mozilla-mplayer has no installation candidate

```could someone tell me how to resolve this issue?  

thanks in advance :)

---

### Post by splicerr on 2010-04-13
[FONT=monospace]mozilla-mplayer is deprecated, use gecko-mediaplayer instead.[/FONT]

---

### Post by overdrank on 2010-04-13
Moved to  Lucid Lynx Testing and Discussion :)

---

### Post by rukshanchristy on 2010-04-14
Hi splicerr,

Thank you. It solved my problem.

:)

---


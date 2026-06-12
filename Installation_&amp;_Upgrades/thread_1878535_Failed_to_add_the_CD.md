---
title: "Failed to add the CD"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by subehsharma on 2011-11-09
Just now a message popped up asking that there is some upgrade available(i'm already running 11.10) and when i agreed to upgrade i got the following :

Failed to add the CD

There was a error adding the CD, the upgrade will abort. Please report this as a bug if this is a valid Ubuntu CD.

The error message was:
'Unable to locate any package files, perhaps this is not a Ubuntu Disc or the wrong architecture?'

I've attached the screenshot of it as well. I am rushing for office so couldn't check on any related thread on the forum. I'd really appreciate if somebody could point me in the right direction,

---

### Post by zvacet on 2011-11-11
In synaptic>repositories> uncheck CD as repository and reload.

```
sudo apt-get update && sudo apt-get upgrade
```

---


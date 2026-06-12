---
title: "post-installation script error"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by LakatosI on 2010-04-23
So I recently reinstalled Ubuntu on my computer using Ubuntu, and I wanted to install Eclipse when during the download/install process there was a power-outage and my computer shut down. Now everytime I try to properly install any java package I get the following error when dpkg is run: subprocess installed post-installation script returned error exit status 2
 
Can anyone help me out here, because I have absolutely no idea how to fix this.

---

### Post by _0R10N on 2010-04-25
Did you tried to remove/fix broken packages? 

You can accomplish that, running

```
sudo aptitude -f
```

Kind regards!

_0R10N >>

---


---
title: "Flash player problem."
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by KevzJD on 2010-02-15
I forced an install for flash player 10 and now i tried removing and installing the free flash player thingy and now getting this error in the screenshot below, please help xD

---

### Post by tom4everitt on 2010-02-15
And what if you run: 

sudo apt-get install flashplugin-installer

which is what it says it needs...

---

### Post by KevzJD on 2010-02-15
Then I get this error in the screenshot.

---

### Post by tom4everitt on 2010-02-15
So its conflicting with adobe-flashplugin.

Hence try:

sudo apt-get remove adobe-flashplugin


(and then the stuff you did before obviously)

---

### Post by KevzJD on 2010-02-15
when doing that i get the error cannot find package adobe-flashplugin

---

### Post by Charlietje on 2010-02-15
Try this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

---

### Post by KevzJD on 2010-02-15
nope, get errors something about dependencies and amd654 deneb flash player :S

---

### Post by tom4everitt on 2010-02-16
Try removing everything that's causing you trouble. the problem seems to be that you have messed up your apts depencies, possibly by adding another software respository which was non-consistent with your old ones. It is always a little risky to add random respositories. 

Check your software sources (system->admin->software sources) and remove stuff that's not the original. If that doesn't help I'm afraid you might have to reinstall your entire system to fix this (and perhaps be more cautious with adding respositories next time, given this was the cause),

---


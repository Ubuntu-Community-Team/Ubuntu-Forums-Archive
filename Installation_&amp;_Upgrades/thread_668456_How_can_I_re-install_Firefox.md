---
title: "How can I re-install Firefox??"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by osonegro on 2008-01-15
I downloaded a add-on for firefox (no script) but when it installed it did something to Firefox and Firefox stopped loading.  I uninstalled the package but now it wont let me re-install it... help!!

---

### Post by Metaljaz on 2008-01-15
Try this site:

[http://www.techsupportalert.com/firefox_install.htm](http://www.techsupportalert.com/firefox_install.htm)

---

### Post by shane2peru on 2008-01-15
> **osonegro said:**
> I downloaded a add-on for firefox (no script) but when it installed it did something to Firefox and Firefox stopped loading.  I uninstalled the package but now it wont let me re-install it... help!!

what you probably need to do is move your firefox directory (you will loose all your bookmarks and settings) but let's see if that will work.  In the terminal try this:```
mv ~/.mozilla ~/.mozilla.backup 
```  that will move the whole folder (all your settings) to another folder then type this in the terminal```
sudo aptitude remove firefox
```
Next:
```

sudo aptitude install firefox

```
Then try and open Firefox again, if it works great, if not, post any errors and we will see what we can do to help further.

Shane

---

### Post by osonegro on 2008-01-18
Thanks, this has solved it.  Looks like I am learning more!

---

### Post by shane2peru on 2008-01-18
> **osonegro said:**
> Thanks, this has solved it.  Looks like I am learning more!

Glad to hear you got it!

Shane

---


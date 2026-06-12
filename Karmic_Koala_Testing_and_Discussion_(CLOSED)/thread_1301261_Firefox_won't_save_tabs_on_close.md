---
title: "Firefox won't save tabs on close"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gnuisancev3 on 2009-10-25
Maybe I've gotten to much used to vimperator.  But anyways, I'm using plain old firefox nowadays since my Karmic install, and when I close the browser and re-open it none of my previously open tabs open back up.

Under Preferences --> Main -->Start Up I have "When Firefox starts" set to "Show my windows and tabs from last time"

Yet when I close and reopen firefox, it's back to the Ubuntu Karmic Google page i have set as my home page.

Any idears?

---

### Post by lovinglinux on 2009-10-25
Type **about:config** in the address bar and check if the option **privacy.clearOnShutdown.sessions** is set to false. If it doesn't exist, then create a new Boolean entry, put **privacy.clearOnShutdown.sessions** in the name and set the value as **false**.

I think this should fix it, but I'm not sure.

---


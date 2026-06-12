---
title: "Karmic firefox 3.0.13 update lameness"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hardwarehank on 2009-08-09
I updated Karmic today, and tried a top-right firefox google search.  I got the ugliest custom google results page ever with no links to images, video, etc. and a big ad block at the top.  ***_Gross_***:

[http://www.google.com/cse?q=search+plugins+firefox&ie=utf-8&cx=partner-pub-2070091971271392:hsw1kx-3zxg&sa=Search](http://www.google.com/cse?q=search+plugins+firefox&ie=utf-8&cx=partner-pub-2070091971271392:hsw1kx-3zxg&sa=Search)

It's supposed to look like this:

[http://www.google.com/search?q=glenlivet+nadurra&ie=utf-8](http://www.google.com/search?q=glenlivet+nadurra&ie=utf-8)

I found out the problem is here:

/usr/lib/firefox-3.0.13/extensions/me001@canonical.com/searchplugins

If you simply type this, and restart firefox, everything is fixed:

```
sudo rm -rf /usr/lib/firefox-3.0.13/extensions/me001@canonical.com
```

**Please remove this "feature" from future firefox updates.  Thank you.**

---

### Post by GeorgeVita on 2009-08-10
From Firefox Menu:

Tools > Add-ons > Extensions > Disable

Multisearch
Ubuntu Firefox Modifications
Webfav (for UNR)

Regards,
George

---

### Post by Starks on 2009-08-10
There's a 26 page topic about this subject.

Please search before you post.

[http://ubuntuforums.org/showthread.php?t=1219501](http://ubuntuforums.org/showthread.php?t=1219501)

---


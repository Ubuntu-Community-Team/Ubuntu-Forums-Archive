---
title: "Flash Player Install?? Help Please."
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by gerrenj on 2010-06-27
Hello, I am very new to Ubuntu.  I tried it in the past couldn't figure it out, but decided to try it again with the new 10.4.  I really need to have flash player plugin installed, but I get this error 
[COLOR="DarkRed"]
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]


I even tried to go through the software center and the extra install through the help site from the firefox browser, but still get the error message.  What do I do.  I really want to give Linux a try but stuff like this a little discouraging.  Any help will be appreciated.

---

### Post by Revolutionary101 on 2010-06-27
I suggest you try to download and install it from Adobe's website.

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

However, I think this may be a bigger problem with dpkg (your installer) and it may have nothing to do with the package itself.

---

### Post by oldos2er on 2010-06-28
Open a terminal (Applications, Accessories, Terminal), and copy and paste this command into it ```
sudo dpkg --configure -a
```

---

### Post by serpentalis on 2010-06-28
I'm having a lot of the same issues. I put that into Terminal and nothing happened. No response at all.

---


---
title: "Flash Player 10.1?"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Voltage. on 2010-08-03
I'm having a problem with the new Flash and my Google Chromium installation. When I try to view videos, it says 'Missing Plugin.' it directs me to get.adobe.com, which tells me 'Your Google Chrome has the latest version of Flash Installed.' 

So... what do I do? The adobe website refuses to let me update it, claiming that I have the latest version, when clearly I don't.

P.S. I'm a Linux noob and I have no idea how things work, only that you can do lots of stuff with terminal. :S

---

### Post by Raymond2201 on 2010-08-03
hey there,

we can try reinstalling this from the repositories:

Yay! load the terminal and paste this in:

```
sudo apt-get install flashplugin-nonfree
```

hope this helps you.

---

### Post by Voltage. on 2010-08-03
Awesome, thanks. It turns out adobe lied, I didn't seem to have flash installed at all. Tested and working now! :D

---


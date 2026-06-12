---
title: "Clean installed Gutsy, now Thunderbird is gone..."
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by peterwr on 2007-11-27
Hi All

I just did a clean install of Gutsy. Obviously, it wiped all the optional stuff I'd installed - KDE and so on - but it also took off Mozilla Thunderbird. I've tried to reinstall, but it's not listed as an option in Synaptic. What happened to it and how do I get it back? 

TIA...

---

### Post by prodezigner on 2007-11-27
first make sure all your repos are enabled (/etc/apt/sources.list) and try...

sudo apt-get install thunderbird

I don't use Thunderbird, I use to though. I hope this helps.

---

### Post by viking777 on 2007-11-27
Look for Add/Remove programs in your start menu and open it. (if you can't find it press Alt/F2 and type adept_installer)

Click the two boxes marked 'show unsupported and proprietary software'

Let it reload then search for 'Mozilla' - it'll be there.

---

### Post by peterwr on 2007-11-28
Ha. Got it! Thanks, guys...

---


---
title: "Update manager error"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by Diptansu on 2010-03-15
When I am trying to check my updates through 'update manager' .. It is downloading up to certain limit .. then shows the following error ..

[B]An error occurred

The following details are provided:[/B]

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B9674A0E7B0FB2CA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EE6F9258A958418A
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


What I sd do? .. pls help ... :(

---

### Post by mcoleman44 on 2010-03-15
Are you using Intrepid or are you using Karmic or jaunty?

---

### Post by Diptansu on 2010-03-15
I am using Intrepid ..

---

### Post by pastalavista on 2010-03-15
```

gpg --keyserver keyserver.ubuntu.com --recv XXXXXXXXXXXXXXXX

gpg --export --armor XXXXXXXXXXXXXXXX | sudo apt-key add -
```

replace the X's with your key numbers and run both commands for each pubkey number

---

### Post by MelDJ on 2010-03-15
Try the link in my sig

---

### Post by slakkie on 2010-03-15
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

---

### Post by Diptansu on 2010-03-15
Err .. well .. what is 'key number' .. and how to find it ? .. :-k

---

### Post by pastalavista on 2010-03-15
B9674A0E7B0FB2CA -- EE6F9258A958418A -- 2EBC26B60C5A2783

from your error messages. maybe 'key codes' would have made more sense

(three separate 16 digit pub-key ID codes)

---

### Post by Diptansu on 2010-03-15
Lol .. :p

WOW ... thanks to all you guys .. this worked fine .. :D

---


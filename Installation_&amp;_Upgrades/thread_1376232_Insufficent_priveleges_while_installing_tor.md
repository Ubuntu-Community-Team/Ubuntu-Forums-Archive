---
title: "Insufficent priveleges while installing tor"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by shishir127 on 2010-01-08
I want to install tor on my laptop, and followed the directions on the tor website-http://www.torproject.org/docs/debian.html.en
So, I added the tor repository source, the gpg keys, and updated the sources. Now, when I run 'apt-get install tor' in the terminal, an error is displayed-
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Need help resolving this root user issue please.

---

### Post by zvacet on 2010-01-09
```
sudo apt-get install tor
```

---

### Post by shishir127 on 2010-01-09
Thanks. I looked up the 'sudo' command, and now i'm feeling silly :)

---


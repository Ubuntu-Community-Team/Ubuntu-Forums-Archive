---
title: "what's with edgy security repos?"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by elettronicha on 2006-10-31
I have this repo in my sources.list

```
deb [http://it.security.ubuntu.com/ubuntu/](http://it.security.ubuntu.com/ubuntu/) edgy-security main restricted 
```

and I get these errors when updating:

```
Err http://it.security.ubuntu.com edgy-security Release.gpg
  Could not resolve 'it.security.ubuntu.com'

...

Err http://it.security.ubuntu.com edgy-security/main Translation-en_US
  Could not resolve 'it.security.ubuntu.com'

...

Err http://it.security.ubuntu.com edgy-security/restricted Translation-en_US
  Could not resolve 'it.security.ubuntu.com'
Ign http://it.security.ubuntu.com edgy-security Release
Ign http://it.security.ubuntu.com edgy-security/main Packages
Ign http://it.security.ubuntu.com edgy-security/restricted Packages
Err http://it.security.ubuntu.com edgy-security/main Packages
  Could not resolve 'it.security.ubuntu.com'
Err http://it.security.ubuntu.com edgy-security/restricted Packages
  Could not resolve 'it.security.ubuntu.com'

...

```

Same issue changing "it." with "us.", no problem with the unlocalized repo (no prefix ".it" or ".us")

---

### Post by Zyphrexi on 2006-10-31
I haven't used localized repos for some time honestly. I think they did away with those in dapper.

---

### Post by elettronicha on 2006-10-31
Just the security ones?

---


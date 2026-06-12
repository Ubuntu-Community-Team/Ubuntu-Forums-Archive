---
title: "Aptitude errors"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by bravemosquito on 2007-04-24
**aptitude update** returns this on Feisty i386:

```
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by aptitude)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by aptitude)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by aptitude)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.4-6.so.3.53)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.4-6.so.3.53)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by /usr/lib/libsigc-2.0.so.0)
aptitude: /usr/lib/libstdc++.so.6: no version information available (required by /usr/lib/libsigc-2.0.so.0)
```

Any ideas what is this?

Edit: I found what caused this - the latest version of **binutils**, downloaded from 'gutsy' repo. **Binutils** removed g++ which is too strange. I had to downgrade the version to fix the errors.

---


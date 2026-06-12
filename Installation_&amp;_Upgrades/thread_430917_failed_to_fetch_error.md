---
title: "failed to fetch error"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by cynniesue on 2007-05-02
Hello. I have tried so many times and keep getting the following:
failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2Sub-process](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2Sub-process) bzip2 returned on error code (2) 
I do not have a clue what this is or means or what to do. I have this upgrade to the new one but this is all I keep getting after it looks like it is upgrading. Thank you very much if you can find time to help me.

---

### Post by jack1254 on 2007-05-02
What were you trying to do when this error occurred/what had you just done?

Did you copy/paste the error message or re-type it? If you re-typed it and missed the space between "bz2" and "Sub", then it looks like a problem with your network connection (the file is there, as long as the link ends at bz2)

---

### Post by zvacet on 2007-05-02
**system>administration>software properties**

If you use local server try with main,and vice versa.If still no luck try

```
sudo aptitude update
```

---


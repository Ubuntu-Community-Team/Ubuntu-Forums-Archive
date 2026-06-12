---
title: "Something is stopping me from updating my computer"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by chris90uk on 2007-06-02
It said that some new headers and image were available, so I tried to update the computer but it comes up with the error message shown in the attached screenshot (sorry it wouldn't let me copy and paste it from the updat thing for some reason). 

It seems that some Bengali fonts are stopping it from installing ANY new upgrade which is a little bit annoying. Any ideas on how I can sort this out?

Thanks a lot

[IMG]http://chris90uk.googlepages.com/Screenshot-15.png[/IMG]

---

### Post by abn91c on 2007-06-02
open a root terminal, then type sudo apt-get check, if it suggest a command to try do so. also you may try apt-get update or apt-get upgrade

---

### Post by chris90uk on 2007-06-02
> **abn91c said:**
> open a root terminal, then type sudo apt-get check, if it suggest a command to try do so. also you may try apt-get update or apt-get upgrade

Still getting 

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 31069 package `ttf-bengali-fonts':
 newline in field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I'm afraid.

---


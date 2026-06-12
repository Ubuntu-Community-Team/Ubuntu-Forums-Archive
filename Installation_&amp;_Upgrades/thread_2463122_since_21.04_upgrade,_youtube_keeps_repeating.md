---
title: "since 21.04 upgrade, youtube keeps repeating"
date: 2021-06-04
forum: Installation &amp; Upgrades
---

### Post by stevenjrees on 2021-06-04
Since upgrading from 20.10 to 21.04, playing youtube videos keeps repeating a few seconds every couple of minutes. 

I am running low latency kernel

---

### Post by monkeybrain20122 on 2021-06-04
Is it browser dependent? Does it happen only in Firefox or do you try a different browser too? What if you try with a different FF profile. To do this, close FF,  rename the hiidden file .mozilla to .mozilla-bk , you can do this in the terminal with the command
```
mv .mozilla .mozilla-bk
```, or open the file browser, press ctrl+H to show hidden file, find .mozilla and then rightclick > rename, then open FF and go to youtube to see whether your issue persists.

---

### Post by stevenjrees on 2021-06-04
happens to both chromium and firefox (both current and previous versions)

---


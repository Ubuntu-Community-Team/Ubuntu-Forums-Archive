---
title: "Update killed VMWare"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by champs on 2008-10-21
I was playing with VMWare today when I noticed the little circle symbol that means I needed to restart cause I received some updates the other day.

This afternoon, I tried to restart the VMWare, but it fails to start....

Any ideas ?

I'm using 8.04, kernel 2.6.24-21

---

### Post by champs on 2008-10-22
Well that was an overwhelming responce...........

Thankfully, I fixed it myself......

I noticed that when I looked up my current kernel to post above, the kernel had changed, must have been in amongst the updates that I just clicked and ignored......

Anyway, instead of clicking the icon on the screen, I opened terminal and tried to start it that way. It acknowledged that the application was installed but not configured for the current kernel.

```

cd /usr/bin/

```

```

perl vmware-config.pl

```

Just except all the default responses to the questions, and within two minutes, we have VMWare again.

---


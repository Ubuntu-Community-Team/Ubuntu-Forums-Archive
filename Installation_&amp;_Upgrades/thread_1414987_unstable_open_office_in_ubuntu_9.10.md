---
title: "unstable open office in ubuntu 9.10"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by petemol on 2010-02-24
Hi,
I have just installed the ubuntu 9.10 and if I copy the text from web page to open office, it just crash-dissapear:-) I can save the file when I just write the text, but if I copy some formatted text it crash.

Any ideas what should help?

Thanks

p.

---

### Post by mathgeek2000 on 2010-02-24
> **petemol said:**
> Hi,
I have just installed the ubuntu 9.10 and if I copy the text from web page to open office, it just crash-dissapear:-) 
Any ideas what should help?

Thanks

p.

Try replacing the included OpenOffice with the new OOO 3.20. That works corrrectly on my system. (Course I just rebuild it, so it's fairly new) any case - the formatted text appears in the body, and comments are off to the left.

---

### Post by Hagar Delest on 2010-02-25
Try first to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by snowpine on 2010-02-25
> **petemol said:**
> Hi,
I have just installed the ubuntu 9.10 and if I copy the text from web page to open office, it just crash-dissapear:-) I can save the file when I just write the text, but if I copy some formatted text it crash.

Any ideas what should help?

Thanks

p.

Have you updated your system since installing? 9.10 was released way back in October, and there have been lots of bug fixes since. Try running the Update Manager, or from the terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

A fully upgraded system is a good first step towards troubleshooting the problem.

---


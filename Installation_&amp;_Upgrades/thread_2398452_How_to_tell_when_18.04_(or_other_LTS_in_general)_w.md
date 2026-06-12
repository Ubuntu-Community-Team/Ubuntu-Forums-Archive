---
title: "How to tell when 18.04 (or other LTS in general) will appear in software updater?"
date: 2018-08-12
forum: Installation &amp; Upgrades
---

### Post by Replicon on 2018-08-12
Hey all,

Given that I have "For long-term support versions" selected on the "notify me..." setting on software updater, when can I generally expect a LTS to show up as an optional "upgrade" button?

I remember it taking a while, from the initial release. I found an "ask ubuntu" answer somewhere saying it's usually when the first point release (e.g. 18.04.1) comes out, but that's been out for a couple weeks now.

I tried to find out when I upgraded from 14.04 to 16.04, but google results are flooded with "how to upgrade to 18.04" haha. I was able to possibly estimate it by running:

```
ls -l /etc/ | awk '{print $6, $7, $8}' | sort | uniq -c | sort -n | tail
```

which has a disproportionately large number of results from August 26 2016, so I guess if that's right, then it's right around the corner....

... still, is there a published, official, "on this day, you WILL see the 'Upgrade to 18.04LTS' button on Software Updater" I can look at now for 18.04, and in the future for future LTS releases?

Thanks!

---

### Post by deadflowr on 2018-08-12
It'll be out after this is fixed:
[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html]("https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html")

---

### Post by Replicon on 2018-08-12
Thanks!

I don't think I would have been able to stumble upon/find that, were it not for asking here. Is there an official Ubuntu blog/status page that stays up to date about these things? :)

---

### Post by deadflowr on 2018-08-12
Me too, 
Thank kansasnoob for the due diligence of reading the mailing lists:
[https://ubuntuforums.org/showthread.php?t=2397260&p=13790715#post13790715]("https://ubuntuforums.org/showthread.php?t=2397260&p=13790715#post13790715")

---


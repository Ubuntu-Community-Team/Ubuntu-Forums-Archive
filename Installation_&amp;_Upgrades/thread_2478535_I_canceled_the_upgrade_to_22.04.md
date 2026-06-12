---
title: "I canceled the upgrade to 22.04"
date: 2022-08-29
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2022-08-29
I have 20.04, up to date, and I started the upgrade to 22.04.1, but canceled it because I can't trust it. Just before going ahead with the upgrade the progress window popped up the following:

```
Install (521)
No longer needed (29)
No longer approved by Canonical (19)
Remove (37)

```

I have hundreds of applications installed, many of which are not from the repositories. I need a complete list, so after the upgrade I can reinstall them, not just a number. The popup didn't mention any more than the above. How can I get a list of the actual damage this upgrade will do?

---

### Post by John Jason Jordan on 2022-08-29
I finally found a reference to /var/log/dist-upgrade/main.log, which supposedly has a list of files to be changed. Sadly, it was hopelessly incomprehensible. It was pages of text with no formatting or organization. Scanning through it I occasionally noted the name of one of my obscure installed applications, but I couldn't figure out if it was to be removed, changed, or what was going to happen to it.

I have complete rsync mirrors of / and /home from last night, so I finally decided that Ubuntu left me no choice. I proceeded with the upgrade using Update Manager. It took several hours to finish, and I had to sit in front of the screen the whole time to answer questions that kept popping up. Why can't it present all these questions at the beginning so I can answer them all and then go to lunch? Oh well. 

When it finally finished it took another couple of hours to fix things, and in that time I've tried only a dozen applications.

---

### Post by grahammechanical on 2022-08-29
For those who do not know, Canonical offers Extended Security Maintenance for Long Term Support (LTS) versions for an additional five years. So, Ubuntu 20.04 has standard support until April 2025 and Extended Security Maintenance until April 2030. ESM is free for personal use.

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

Regards

---


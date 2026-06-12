---
title: "OpenSSL"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2006-10-02
Ok, not being a coder, I don't know how critical this is, but apparently theres a vunerability in OpenSSL < 0.9.8d, and the irc channels I go to seem to think its quite a critical one.

Yet Ubuntu Dapper Drake is still using 0.9.8a.

I really don't like running vunerable SW on my machine, so can I ask when the repo's are going to be updated to give OpenSSL 0.9.8d?

Milambar

---

### Post by Jussi Kukkonen on 2006-10-02
> I really don't like running vunerable SW on my machine, so can I ask when the repo's are going to be updated to give OpenSSL 0.9.8d
Short answer: You aren't really that vulnerable, and the version number isn't the whole story.

The vulnerabilities fixed in 0.9.8d aren't *that* serious (at worst it's denial of service, as far as I can see). The critical ones you heard about are probably the vulnerabilities fixed in 0.9.8c -- *"Implementations may incorrectly verify the certificate"* --  that is serious.

The fixes in 0.9.8d are not yet in Ubuntu (they were released three days ago so that's not a surprise), but the more serious signature checking bug has been fixed. The version numbering that fooled you is something of a problem, but there are good arguments for following upstream version numbers and good arguments for not changing the version number if the only changes are security updates....

---

### Post by Milambar on 2006-10-02
Okay, thank you for your reply :) I will rest a bit easier now.

---

### Post by Jussi Kukkonen on 2006-10-02
It's good to be cautious. I forgot to mention that there's a sub-forum for security announcements:

[http://www.ubuntuforums.org/forumdisplay.php?f=20](http://www.ubuntuforums.org/forumdisplay.php?f=20)

---


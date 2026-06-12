---
title: "Evolution problem with Firefox 3.0"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by bardu on 2008-04-27
Clicking on a hyperlink in an email doesn't open the page in Firefox 3.0. I presume Evolution doesn't find Firefox 3.0. 

How can I fix it?

Thanks.

---

### Post by bardu on 2008-04-28
The solution on Ubuntu 8.04 is:

Preferences -> Preferred Applications -> Internet -> Web Browser set to 'Custom' and set command from /usr/lib/firefox/firefox %s to /usr/bin/firefox.ubuntu %s

---


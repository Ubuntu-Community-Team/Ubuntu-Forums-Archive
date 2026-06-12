---
title: "KDE Daemon (kdeinit4) segmentation fault in 12.04"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by jandac2011 on 2012-05-02
I upgraded from 11.10 to 12.04 on an old laptop (Fujitsu-Siemens). Every time I log in to KDE, the KDE deamon (kdeinit4 as a backtrace shows) crushes. I try to submit a bug report, but when I get "Login into the KDE Bugtracking System", and I press the Login button, I get an error message:
> Failed to communicate with kded. Make sure it is running.
It is not running. When I try running kded, nothing happens. The process does not show up in ps. When I try running kded4 with sudo, it runs, but I sill get the same error message when pressing Login button. When I run kded4 without sudo, I still get the same message, but after a long time, and the console shows that kio_http cannot communicate with kded_kcookiejar. Then I run kcookiejar and kcookiejar4, but it does not help either. They will not stay running.

kdeinit4 is running, and start_kdeinit is. There are more errors, but they are probably the result of the initial crush. What can I do to get rid of the bug? How can I run the cookie service?

---

### Post by jandac2011 on 2012-05-03
On my desktop computer that I luckily did not upgrade to 12.04, kcookiejar4 exists but it is not running, and there are no signs suggesting that it should be running. In 12.04, when I select "Configure Konqueror" from Settings menu, I get an error message about cookie service not running, in 11.10 there is no such error message and management tab appears in Konqueror configuration.

---

### Post by jandac2011 on 2012-05-12
It looks like updates solved the problem.

---


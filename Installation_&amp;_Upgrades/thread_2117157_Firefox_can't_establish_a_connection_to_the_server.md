---
title: "Firefox can't establish a connection to the server at localhost."
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by MJROCKR on 2013-02-17
i am not been able to access my local host when browsed by the firefox  and the browser displays the error Firefox can't establish a connection to the server at localhost.
The site could be temporarily unavailable or too busy. Try again in a few
    moments.If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.help me out!!!

---

### Post by efflandt on 2013-02-18
Maybe a silly question, but did you install **apache** or some other web server on your computer? If not, what would you expect to find on localhost (your own computer)?

See if [http://localhost:631/](http://localhost:631/) works (which would be the cups printing service).

It could be that firefox fixup is tripping you up. That may try to add www. prefix or .com suffix to names it thinks are incomplete.  In firefox location bar type **about:config** then Search: **fixup** and double-click **browser.fixup.alternate.enabled** so it becomes **false**. See if that helps.

---


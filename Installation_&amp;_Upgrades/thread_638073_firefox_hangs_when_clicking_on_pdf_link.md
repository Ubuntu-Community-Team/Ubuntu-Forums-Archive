---
title: "firefox hangs when clicking on pdf link"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-12-11
Whenever I click on a pdf link in firefox it never comes back. I just get the circle with the dots going round and round and when I click on firefox's 'X' button I get the "Not responding" window.

I check download actions and I have
PDF open with Adobe Reader 7.0

So, how do I get it to work.

999alfred

---

### Post by eggdeng on 2007-12-11
You could try typing ```
about:plugins
``` in the address bar to check if you have the nppdf.so plugin in the firefox/plugins directory. Do a ls -l on the plugins directory to make sure nppdf.so has the correct permissions: -rw-r--r-- , owned by root.

---


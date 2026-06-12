---
title: "Invalid command 'RewriteEngine'"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Rebajas on 2007-11-06
I'm still trying to get Apache2 set up - it all seems to be working but I get the following error relating to the .htaccess file I am using:

```
Invalid command 'RewriteEngine', perhaps mis-spelled or defined by a module
not included in the server configuration
```

Through the browser I am greeted by a 500 error - how do I install mod_rewrite or turn it on if it is a standard module?

Ta.

---

### Post by Belak on 2008-04-03
Sorry if this seen as a bump for a dead topic. I just wanted to make sure one of the topics on this forum (apart from the person running rails having this problem) had the solution.

It's as simple as running the following command in a terminal:
```
sudo a2enmod rewrite
```
This enables the apache module rewrite

if you want to know how to disable modules, or how I found this just check the manual for a2enmod.

-Belak

---


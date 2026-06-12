---
title: "squid 3 &amp; https cache"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by luca26 on 2014-11-27
Hello,
its possibile with squid3 caching https? youtube video etc?

Thanks
Luca

---

### Post by SeijiSensei on 2014-11-27
Yes, but it's very complex and requires installing SSL certificates in Squid and in the client browsers.  For the intrepid, read this: [http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

Many streaming video sites explicitly tell the browser not to cache the material sent.  I don't know if that's true for YouTube, though.  If you're trying to capture streams, there are better methods for that, but we [cannot discuss them here]("http://ubuntuforums.org/misc.php?do=showrules") because it would constitute "circumventing" YouTube's Terms of Service.

---


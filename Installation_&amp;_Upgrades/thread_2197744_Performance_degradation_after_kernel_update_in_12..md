---
title: "Performance degradation after kernel update in 12.04 LTS"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by pft42 on 2014-01-05
Hi,

I am running 12.04 LTS as a file server and a few other applications (mail, proxy, named, dhcpd ...)
Yesterday I experienced a dramatic performance degradation doing network access from Win clients. It way actually only a 10th of the usual performance. It affects smb transfers. Local disk access is fine.
After checking various things like network, client config etc. I reminded the recent kernel update to 3.8.0-35. rebooting to 3.8.0.-34 gave me the original performance without any other config changes.

Is there a bug in the recent upgrade or is it a feature I have to configure? What should I look for?

Thanks 
Thomas

---


---
title: "Upgraded to 22.04 and Auditd has changed major version, no mention in Readme"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by jimpye on 2022-04-23
All

Just a heads up, as this is not mentioned in the README for 22.04, the version of auditd has changed from v2.8.5 to v3.0.7.

The significant difference that has impacted my installation, using Puppet for configuration, has been the moving of the Audit Dispatcher into Audit.

As mentioned in this article [https://access.redhat.com/solutions/3806561](https://access.redhat.com/solutions/3806561) (paywall - but gives away enough information in the teaser) there is no /etc/audisp directory in v3.

Now trying to find documentation to see what configuration I need to change to get things to work again.

Cheers
Jim

---


---
title: "Best Cache for Dist-Upgrade"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by ogryn on 2011-10-11
Hi,

I know there are a couple of different options for caching .deb packages to a machine, but I've not yet found something that works well for Distribution Updates.

We have about 10 Ubuntu machines here that we want to update to 11.10 when it arrives but I don't want to download all the packages every time. 

When you run the update-manager -d, it replaces all your sources which then bypasses how things like apt-mirror seem to work. 

Any ideas on the best way to only have to download the packages once and update the other machines from the local network?

Thanks,
Dave

---

### Post by Lars Noodén on 2011-10-11
One way would be to use the package apt-cacher, or apt-cacher-ng, and configure the machines to use that as the proxy.

---


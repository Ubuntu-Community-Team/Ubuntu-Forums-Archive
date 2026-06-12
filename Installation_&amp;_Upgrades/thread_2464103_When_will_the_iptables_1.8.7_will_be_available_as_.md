---
title: "When will the iptables 1.8.7 will be available as &quot;apt update/upgrade&quot;"
date: 2021-06-24
forum: Installation &amp; Upgrades
---

### Post by atlantakid on 2021-06-24
Hi,
I am running Ubuntu  "Ubuntu 20.04.2 LTS" with "iptables 1.8.4-3ubuntu2 amd64" and would like to use ipset and iptables' --add-set option, which is not available in v1.8.4, can someone share when will the v1.8.7 be available as normal update/upgrade.

I know i get wget he latest source and do "configure/make" and to that route, but I rather wait for official update.

Thanks

---

### Post by MAFoElffen on 2021-06-24
I don't see that version (v1.8.7) of iptables in an 20.04 LTS repo, even in focal-proposed. I don't see it in any of the the repo's until 21.10, which is an Interim Release. So I would expect to see it "=>" in the Main LTS repo's in 22.04 LTS.

---

### Post by deadflowr on 2021-06-24
> can someone share when will the v1.8.7 be available as normal update/upgrade.
Probably never.
iptables is rarely updated. (of the currently 4 supported stable Ubuntu releases only groovy has had an update for it)
And it will most certainly never get upgraded to a newer version for any stable release.
You can always request an SRU for it following the guidance explained here:
[https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")
But don't hold your breath that it will get your requested update anytime, sooner or later.

---

### Post by rsteinmetz70112 on 2021-06-24
Most likely only security fixes and bugs will be backported and the version not increased. It may be included in a later version.

---

### Post by Tadaen_Sylvermane on 2021-06-24
[https://wiki.debian.org/nftables](https://wiki.debian.org/nftables)

Debian is moving toward the above so I don't expect iptables will get any more updates. I'd be surprised if Ubuntu didn't follow suit soon.

---

### Post by The Cog on 2021-06-24
I was going to mention nftables, but Tadaen_Sylvermane beat me to it.

My laptop is on 20.04 and I am running nftables. It works a treat, and has sets build in. I recommend using it.
[https://www.nftables.org/](https://www.nftables.org/)

---


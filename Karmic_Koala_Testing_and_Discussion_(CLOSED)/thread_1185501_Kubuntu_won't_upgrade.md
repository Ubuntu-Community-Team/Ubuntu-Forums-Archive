---
title: "Kubuntu won't upgrade"
date: 2009-06-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-06-12
I'm continuing my hate-hate relationship with kde4 this week. I thought I'd take a peek at how kubuntu is shaping up and so tried to upgrade my jaunty install to karmic. It insists there is no dist-upgrade available. Anyone have any insights for me?

I've tried apt-get dist-upgrade so far

---

### Post by taavikko on 2009-06-12
> **macroshaft said:**
> I'm continuing my hate-hate relationship with kde4 this week. I thought I'd take a peek at how kubuntu is shaping up and so tried to upgrade my jaunty install to karmic. It insists there is no dist-upgrade available. Anyone have any insights for me?

I've tried apt-get dist-upgrade so far

dist-upgrade doesn't upgrade release-version.
without manually changing sources.list.

please use "sudo do-release-upgrade --devel-release"
to upgrade. Set release prompt=normal, if not already to be able to do so.
(/etc/update-manager/release-upgrades)

---

### Post by macroshaft on 2009-06-12
I did also try do-release-upgrade as stated in the release notes but that didn't work either, that extra bit you added on the end appears to have done the trick. Thanks

---


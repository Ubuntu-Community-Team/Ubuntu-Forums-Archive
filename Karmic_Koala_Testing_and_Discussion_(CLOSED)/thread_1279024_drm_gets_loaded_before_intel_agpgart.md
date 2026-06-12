---
title: "drm gets loaded before intel_agpgart?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coolvibe on 2009-09-30
Hi,

Sometimes, drm gets loaded before agpgart-intel. This breaks KMS + compiz and makes X hellishly slow. Sometimes it gets it in the right order and all is fast again.

Is there any way I can hardcode that agpgart-intel gets loaded first before the i915 drm module? 

Before someone shouts "file a bug report", someone already did:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)

---


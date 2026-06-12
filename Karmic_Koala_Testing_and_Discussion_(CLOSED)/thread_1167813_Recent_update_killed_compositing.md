---
title: "Recent update killed compositing"
date: 2009-05-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crisnoh on 2009-05-23
A recent upgrade caused me to lose compositing capability.  I'm using intel graphics and would like some help diagnosing the problem.  Thanks.

---

### Post by fifth on 2009-05-23
I'd guess the intel driver is not being used, see the thread on X resolution problems, the updated intel driver is not being identified properly, you need to manually specify the intel driver in you xorg.conf file.

---

### Post by taavikko on 2009-05-23
```
xserver-xorg-video-intel (2:2.7.1-1ubuntu1) karmic; urgency=low

  * Merge from debian unstable, remaining changes:
    - Add lpia architecture
    - 103_quirk_intel_mb890.patch: quirk
    - 110_quirk_hp_mini.patch: quirk
    - 116_8xx_disable_dri.patch: DRI proved buggy on certain 8xx chips so
      this disables it.  The DRI probably needs re-testing to verify this
      patch is still needed, but it will be kept for now.
    - 117_quirk_thinkpad_x30.patch: quirk
  * Drop 119_drm_bo_unreference_needs_null.patch: upstream.
  * Re-enable the patch system, add quilt to build-deps.

 -- Timo Aaltonen <>  Fri, 22 May 2009 11:17:55 +0300

xserver-xorg-video-intel (2:2.7.1-1) unstable; urgency=low

  [ Brice Goglin ]
  * New upstream release.
  * Install the upstream NEWS file, closes: #524334, #524336.
  * Move the -dbg package to section debug.

  [ David Nusinow ]
  * Remove 01_gen_pci_ids.diff. The X server now uses an internal table to
    choose a driver during autoconfiguration.
    + Disable patch system and remove quilt from build-deps.

 -- Brice Goglin <>  Wed, 13 May 2009 07:14:50 +0200

```

---

### Post by crisnoh on 2009-05-23
Most recent xorg update fixed the problem.

---

### Post by tad1073 on 2009-05-24
updated 10 min ago and  xorg broke my compositing using newest nvidia driver w/compiz

new xorg works w/metacity but not compiz

---

### Post by Nullack on 2009-05-24
Composting breaks lots of things when it works anyway. Its always been broken.

---

### Post by jfernyhough on 2009-05-24
> **Nullack said:**
> Composting breaks lots of things when it works anyway. Its always been broken.Composting breaks down many things. It always ends up with a pile of sh*t. :D

:P

---


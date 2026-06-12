---
title: "Disable phased upgrades for PPA's"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by davidgasku on 2013-08-28
Hi, since phased updates were activated, some of the software doesnt update like it did before. I've got some PPA's with software that update very quickly, and I would like to disable phased updates in these.

Is there any way to do so? Thanks

---

### Post by grahammechanical on 2013-08-28
Phased updates? How do you know that you are a recipient of a phased update? I am sure that Phased Updates only apply to Stable Released Updates (SRU) which are very few. And have to meet strict conditions so as not to make the stable release of Ubuntu unstable.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

This blog post by the developer mentions what to do to opt out of Phased Updates. You will still get the update but you will not be among the first to get it. You will be among the last.

> One can opt out of the Phased Update process by adding  &#8216;Update-Manager::Never-Include-Phased-Updates &#8220;True&#8221;;&#8217; to the  configuration  file &#8220;/etc/apt/apt.conf&#8221;.

By the way, I do not think that Phased Updates apply to PPAs. That is not the reason for frequent updates to software installed through a PPA. The reason is progressive development. Untick the PPA in System Settings>Software and Updates>Other Software.

Regards.

---


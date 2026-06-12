---
title: "Kubuntu 12.04 boots in initramfs"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by beepbeep2709 on 2012-10-31
Hi Guys,

I have been facing issues with my Dell XPS L510x laptop. I am running Kubuntu 12.04 and I was using my laptop for quite sometime without any problems. However yesterday i started my laptop and it went into "initramfs" mode. 

Can anyone help me sort out this problem. I have tried running e2fsck (help through forums) and all, but it just does not let me run anything. Any help would be much appreciated to get this sorted.

Thanks...guys.

---

### Post by beepbeep2709 on 2012-11-01
Found a fix to the problem ....

Booted using a live cd and ran e2fsck -f on the partition. Rebooted the system and voila...it worked.

Hope this helps. :)

---


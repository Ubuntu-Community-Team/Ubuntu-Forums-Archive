---
title: "System hangs in /scripts/init-bottom"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by KailasNarendran on 2008-10-23
Hi! I'm running ubuntu from a CF card I've built from a previously working image.

I created the image from a Kingston CF/4G card. I dd'd the image onto a new CF/4GB-S2 card to boot from.

The initial problem was that the cards aren't the exact same size, so while it was booting it spit out stuff to that extent.  to fix that i ran fdisk, deleted my extended and swap partitions (2 and 5) (which were a few cylinders longer than the actual media) and re-created them with the correct length.

Now when it boots, it doesn't spit out the length errors, but it hangs at /scripts/init-bottom

Any ideas?  I've searched around and found that other people had similar issues (not with CF, but just in general, hanging at /scripts/init-bottom), but no resolutions.. i Have a feeling it has something to do with my partition resizing and stuff.

---


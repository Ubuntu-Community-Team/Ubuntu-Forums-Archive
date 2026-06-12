---
title: "Upgrading disabled Swap!"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by TheSandman on 2006-08-10
Well...
Upgrading to Dapper broke a great number of things for me, and i fixed most of them in a few days figuring it not much worthy of note. (though i've still not got sound working properly...blech)

But this is just plain bizzare.
I just realized i've got no swap!

After updating to Dapper it no longer mounts my swap on boot though the partition is still there.

It tries to boot hda5 as swap, it used to, and should, mount hda6 as swap.

Any idea why it suddenly tries to mount the wrong partition as swap?

---

### Post by TheSandman on 2006-08-10
Editing my fstab to mount it correctly solved it.

Still doesn't explain how it could happen.

---


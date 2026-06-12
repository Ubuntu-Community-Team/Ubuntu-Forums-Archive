---
title: "Why ext3?"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by zilla1126 on 2005-04-13
I usually use reiser, but xfs and jfs seem to be fine choices also.  Why does Ubuntu default to ext3?  I'm assuming the answer will be maturity; but reiser, jfs, and xfs are production quality and have been for a while.

Ext3 is slow and takes forever (in my experience) to scan for errors.

Thanks for your time.

---

### Post by dataw0lf on 2005-04-13
Why ext3? Because of the amount of tools available, and it's still the best all around filesystem.  ReiserFS has it's place, as do the others, but I think defaulting to one of these filing systems over ext3 is ridiculous.  They're still in their infancy.  And Reiser _isn't_ as stable as ext3. Reiser also slows down on larger files.  
It really depends on your workload, the purpose of the machine, and the intent of the partition.  ext3 is still, IMHO, the best 'default' filing system.

---


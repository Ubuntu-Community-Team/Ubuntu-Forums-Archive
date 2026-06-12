---
title: "Upgrading from Dapper to Edgy prompts for Feisty?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by nitewing98 on 2007-04-20
I've got the alternate (upgrade) CD for Edgy.  I'm upgrading from Dapper (eventually to Feisty, but I need to do Edgy first, apparently).  However, the upgrade-manager, whether using the CD or downloading via the 'net, prompts me for the Feisty CD.  Why?  If I click "cancel" then it aborts the entire upgrade.

I've been through this about 3 times now and am getting frustrated.  Any help or advice greatly appreciated.

---

### Post by K.Mandla on 2007-04-20
If you look in your /etc/apt/sources.list file, you might still have an entry for the CD in it. If you see one, comment it out with a hash mark (#). Update and try again; that should keep it from looking for a CD.

---

### Post by nitewing98 on 2007-04-20
Thanks for the info!  However (stupidly) I opted to just do a fresh install of Feisty on a separate partition, figuring that would be a faster route.

The partitioner is currently stuck at 50% while making the new partition, I hope it finishes and hasn't trashed my old data...

---


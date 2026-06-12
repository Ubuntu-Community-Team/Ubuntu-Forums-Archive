---
title: "2-6-20-16 - oh dear - can I undo it?"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-05-29
Hi,

can the update to 2-6-20-16 be undone?

I have commented out the 2-6-20-16 options in grub menu but would much rather remove the 2-6-20-16 altogether.

Many thanks,

David

---

### Post by old_geekster on 2007-05-29
I believe that you should be able to delete it in "Synaptic Package Manager".

---

### Post by rsambuca on 2007-05-29
Yeah, you can delete the kernels with Synaptic.  Search in Synaptic for "linux-image", and delete the kernels you don't want.  It should also update grub to get rid of the entries for you as well.

---

### Post by bapoumba on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				@ dryder: You should reboot on the -15 kernel if it works for you and wait for a fix on the -16.
Pasted the relevant bug report.

---

### Post by dryder on 2007-05-31
Thank you EVERYBODY :)

2.6.20-16 is now removed.

Thank you all for your help.

David

---


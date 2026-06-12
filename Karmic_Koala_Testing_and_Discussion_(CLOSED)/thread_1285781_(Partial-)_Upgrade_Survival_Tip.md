---
title: "(Partial-) Upgrade Survival Tip"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sophont on 2009-10-08
Here's a very easy tip how to avoid major breakage during testing.

Assuming you have at least 1 GB of RAM and you want to test drive a dev version like Karmic on your metal.

Install VirtualBox OSE (3.0.x is oin the Karmic repo).

Install another copy of Karmic in a VM.

Always do upgrades first on the VM. Reboot (the VM) and have a look at your favourite features. If it still boots in your VM and your most wanted features are still in working condition - do the updates on the main install.

There are a few limitations of course. A kernel update that works in the VM might fail on your metal (very rare though). And your VM will think it's connected to ethernet even if your machine is conected via wifi - so some wifi NM problems could get through.

But this will otherwise detect most major packaging and feature problems early and if the VM gets messed up - shrug - easily replaced (make a copy of the virtual harddrive file and it's fixed within a minute).

---


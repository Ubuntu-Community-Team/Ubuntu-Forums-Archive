---
title: "kenel update and reboot (?)"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2006-09-25
I have completed a number of Kubuntu and Ubuntu updates (6.06 desktop) and I think these have included updates that looked like kernel updates.

However, I did not see any comment to ask for a reboot, which puzzled me. In another disto (suse) which I also use, I notice that after a kernel update, there is a special note to call for a reboot.

Is there a special method of kernel update used in Ubuntu which does not need a restart from the user?

tia

---

### Post by gborzi on 2006-09-25
Every time I have updated my kernel, an applet just left of the notification area has appeared (its icon is two arrows in a circle), and a small window without border notifies the need to reboot. Clicking on this applets reboots the system. I don't know about a similar thing for kubuntu.

---

### Post by hajk on 2006-09-25
> **candtalan said:**
> I have completed a number of Kubuntu and Ubuntu updates (6.06 desktop) and I think these have included updates that looked like kernel updates.

However, I did not see any comment to ask for a reboot, which puzzled me. In another disto (suse) which I also use, I notice that after a kernel update, there is a special note to call for a reboot.

Is there a special method of kernel update used in Ubuntu which does not need a restart from the user?

tia

Well, there are updates and updates... If the kernel update is just a different Ubuntu patch of the installed kernel version (like 2.6.15-26) from 46 to 47, then the upgrade copies right over the installed version (which is in memory) and also over the kernel modules --> a reboot is then urgently required, and indicated by an icon, as the previous poster said. 

But, it could also be an update from kernel version 2.6.15-26 to 2.6.15-27, say -- in this case the new kernel is copied alongside the old one and installed as the default choice in Grub. There is no urgency to reboot, since the current (old) kernel still has access to all its modules, etc. The next time you (re)boot, the new kernel is used (by default), but the old kernel can still be chosen if you want to.

Hope this helps sort things out.

---

### Post by candtalan on 2006-09-25
Many thanks for the responses. I looked on a mulitiboot PC I have just now, still thinking, and saw that edubuntu needed an update including a kernel image update. Following it, yes, a warning message appeared - requiring a reboot.  It was very clear, and  immediately appropriate. I would previously have followed the warning request without any special memory of it I suppose, a natural thing. 

It had come to mind because the suse approach is not totally intuitive at present, with the warning to restart appearing before the update itself only, so the restart may be forgotten inadvertently. Being perplexed by this I had no recollection of similar in Ubuntu. Thanks again. And thanks Ubuntu.

---


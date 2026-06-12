---
title: "system not booting; upperleft cursor blink"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by wiz561 on 2011-09-07
Hi!

I installed Ubuntu 11.04 Server amd64 on my new system76 box.  I'm awaiting my cd-rom, so I setup a pxe server and preseeded a few questions so it looks at my local mirror.  

The problem is when it gets done and reboots, it doesn't boot up.  I can get into recovery mode just fine and everything works at that point.  I tried to re-install grub but that didn't fix it.

I discovered if I take off "vt.handoff=7", everything works fine and it boots normally.  

I was hoping somebody could explain why it doesn't boot with the vt.handoff=7 and if I should do anything else to fix it.

Thanks!

---

### Post by wiz561 on 2011-09-07
I did a search for vt.handoff and found a bunch of info on this.  The message can probably be deleted.

---


---
title: "Re-installing GRUB Loader after installing Xp over it"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by mohansathish on 2010-01-01
I dont know whether it had been posted already..
for reference...
when runs XP and UBUNTU on the same machine, sometimes, re-iinstalling XP will make initial GRUB loader not to work, so that ubuntu may be invisible.
to make it work properly, follw the instructions below..
**step1**:   insert the live CD
**step2**:   goto terminal (applications->accesories->terminal)
**step3**:   Get into GRUB (type: sudo grub)
**step4:**   type: find /boot/grub/stage1
              It will show where it finds the GRUB loader say (hd0,0)
**step5**:   type: if you having many ubuntu versions, it will show all of them like above
**Step6**:   type: root (hd0,0)---> varies according to your installed partition
**step7:   **type: setup (hd0)
**step7**:   type: exit 
**step8**:   now reboot and remove your live CD
          The boot screen will be back

---

### Post by 73ckn797 on 2010-01-01
You have not searched the forums? This would be recurring discussions forum material.

---


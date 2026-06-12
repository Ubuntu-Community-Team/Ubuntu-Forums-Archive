---
title: "Installing 16.04 in UEFI mode gives &quot;No Operating System Found&quot; on Lenovo K430"
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by dean.w.schulze on 2016-06-26
I installed Ubuntu 16.04 on a Lenovo K430 deskktop (BIOS date is 06/12) in UEFI mode.  At boot time it gives "No Operating System Found".  I've tried switching the BIOS Startup menu from Legacy to UEFI but both fail with the same message.  This is the second installation I've done on a UEFI system and UEFI seems to have really broken things.

What do I have to do to get this to boot?  


Thanks.

---

### Post by yancek on 2016-06-26
Get boot repair from the link below and run it after selecting the option to Create BootInfo summary.  Do not try to make any repairs but post a link to the output and someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kurt18947 on 2016-06-27
> **dean.w.schulze said:**
> I installed Ubuntu 16.04 on a Lenovo K430 deskktop (BIOS date is 06/12) in UEFI mode.  At boot time it gives "No Operating System Found".  I've tried switching the BIOS Startup menu from Legacy to UEFI but both fail with the same message.  This is the second installation I've done on a UEFI system and UEFI seems to have really broken things.

What do I have to do to get this to boot?  


Thanks.

I *think* that switching from UEFI to Legacy AFTER installing doesn't work. You would need to switch from UEFI to Legacy then install. Wait for someone more knowledgeable to check in. There's probably a way to install using UEFI and have everything working but I have no expertise there.

---

### Post by Rex Bouwense on 2016-06-27
I also blew my install on a UEFI machine as well.  I did find this by oldfred [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) (after I screwed it up) and am working through it now.  Perhaps it can be of assistance to you.

---

### Post by ubfan1 on 2016-06-27
In BIOS/UEFI Settings check the default order for boot type: either "Legacy first", or "UEFI first".  Since the Ubuntu install media boots both ways, if "Legacy first" was first, then the install was in legacy mode, even on a UEFI machine.  Better to put first the mode you want, or find some way to just use that mode.

---

### Post by dean.w.schulze on 2016-06-27
I was able to finally get Ubuntu 16.04 installed and working by going into the BIOS Startup menu and changing the boot to be Legacy (not Auto, not UEFI) and then doing a complete install after booting from Legacy.

UEFI is a curse.

---


---
title: "AMDGPU issue in liveCD and installation process"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by Roberto_Perico on 2017-10-07
Hi to all,
i recently tried to install Ubuntu on my new laptop (Lenovo Ideapad 320 15abr) which has the new AMD Radeon 530 graphic card. I've tried to install different versions (16.04, 17.04 and the daily build of the 17.10) but the problem is always the same: in liveCD or in the installation process, the mouse freezes after 20/30 seconds and i can't use it anymore, But i can still use the system with the shortcuts. I've tried also with the nomodeset flag, disabling fast boot and secure boot in the BIOS and with the legacy mode enabled but nothing. Once the system is installed, i can't login because it hangs at the login screen.
I think the problem is that my graphic card is too new for amdgpu driver. Is there a way to install Ubuntu or do i need to wait new drivers?
Thank you for your patience.

---

### Post by Mark Phelps on 2017-10-09
The problem is that running in LiveCD mode, you can't install AMD drivers -- because when you reboot, everything you did gets flushed from memory and you start over again from scratch.

---

### Post by wildmanne39 on 2017-10-09
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---


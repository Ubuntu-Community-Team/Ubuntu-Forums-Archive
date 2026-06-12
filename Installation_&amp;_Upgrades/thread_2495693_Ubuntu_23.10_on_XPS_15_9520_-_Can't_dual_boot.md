---
title: "Ubuntu 23.10 on XPS 15 9520 - Can't dual boot"
date: 2024-02-27
forum: Installation &amp; Upgrades
---

### Post by csete on 2024-02-27
I'm in the midst of setting up a Dell XPS 15 9520 to dual boot Windows 11 and Ubuntu 23.10.  I had this working fine yesterday, however after updating the BIOS today I'm no longer getting the GRUB menu, but directly boots into Windows 11.  I tried Boot Repair and, while it didn't show any errors, it also didn't fix the problem.  I tried that both with and without Secure Boot enabled.  One thing that was new and potentially interesting is that the Dell boot screen is now saying something about "Dell SafeBIOS".  I have no idea if that has any implications in this case.  

Boot-repair logs are here:  [https://paste.ubuntu.com/p/bygvNk7bv6/](https://paste.ubuntu.com/p/bygvNk7bv6/)

I'd appreciate any pointers to how I can restore my dual-boot.

Thanks,
Craig

---

### Post by csete on 2024-02-27
Never mind.  All I needed to do was reorder the boot order in the BIOS.

---


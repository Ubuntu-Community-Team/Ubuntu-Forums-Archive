---
title: "Dual boot with already installed Windows 10 Hard Drive"
date: 2020-08-19
forum: Installation &amp; Upgrades
---

### Post by bebizzy on 2020-08-19
I have a hard drive with Windows 10 already installed. I have Ubuntu running on another hard drive in my computer. Can I insert the Win10 hard drive and set up a dual -boot system? And if so, how do I go about setting up the boot option?

---

### Post by CelticWarrior on 2020-08-19
Welcome.

It isn't possible to answer your question without knowing the system or what you want to do.
BIOS or UEFI?
How and where was the Windows installed? If on some other machine then very likely it won't boot even as standalone.

---

### Post by Impavidus on 2020-08-19
A Windows harddrive can't be moved simply from one computer to another and still boot. That's how Microsoft designed it, to make it harder to use unauthorised copies. But if the Windows harddrive boots in your computer and both Ubuntu and Windows are installed in the same mode (BIOS or UEFI), it should dual doot as soon as both harddrives are inserted. Use the BIOS or EUFI settings to select the Windows drive and boot Windows, select the Ubuntu drive and boot Ubuntu. What's more, if update-grub detects the Windows system, it will make an entry for Windows in the grub menu, so you can boot them both via the grub menu and still fall back either of them when the harddrive with the other fails.

---


---
title: "DualBoot Ubuntu 12.04 and Win XP Pro"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by bromont on 2012-04-29
Hi,

I have Windows XP Professional installed on my system and I want to install Ubuntu 12.04 aside Windows. I have installed Ubuntu with no problems, but after rebooting, I don't have a boot menu. I can access Windows only.

I thank you for your support.

Claude

---

### Post by oldfred on 2012-04-29
Welcome to the forums.

Run this from terminal and see what it reports:

sudo update-grub

If it does not show XP being added to the menu then download and start Boot-Repair and Post Boot-Info from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---


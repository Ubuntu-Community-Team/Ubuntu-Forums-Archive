---
title: "After upgrade GRUB just says 'GRUB' and doesn't boot"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by urusaiyatsu on 2005-10-20
Hi all,

I have a dual boot system that worked fine under 5.04 Ubunutu/Kubuntu and XP Pro.

Did an upgrade from 5.04 to 5.10 in Ubuntu via apt-get. All ok. Rebooted into XP via GRUB ok, then later rebooted into Linux, Kubuntu went through it's upgrade process. Logged into Ubuntu and installed Beagle via Synaptic. No problem. Went to reboot into XP later and instead of the GRUB menu all get is a black screen with GRUB in the top left corner. I can CTRL+ALT+DEL and it tries to reboot and 'GRUB' appears again.

Any ideas why? What exactly would I be looking to repair in GRUB?

---

### Post by urusaiyatsu on 2005-10-21
Someone has suggested I replace the /boot/grub/menu.list file contents with the backup which Ubunutu apparently makes (menu.list~).

Does this sound like it would work?

---


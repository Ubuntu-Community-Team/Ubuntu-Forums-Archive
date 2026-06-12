---
title: "GRUB hangs after 10.04-&gt;12.04 online update"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by eadwacer on 2014-06-19
Just updated my old System76 desktop from 10.04 to 12.04 on my way to 14.04. Install went fine, but when I rebooted at the end it hung with a blinking cursor. I rebooted and held down [right-shift] and I got "GRUB loading" ...and a blinking cursor.

Possible contributing factor: I had had a problem after the latest Linux kernel update (-61?), and had edited the config file to (a) show my options on boot, and (b) boot to the prior version (-.60?) as default. During the upgrade I told it to use the old config file. 

I've read the stickypost on "I upgraded and now I have this problem" but I'm not quite ready to do that yet. I think there's a simple solution, if only I can get GRUB to boot. This is a pure Linux system, so it's not a dual boot issue.

---

### Post by oldfred on 2014-06-20
If only one drive and one system you can run the autofix, otherwise best to use advanced and choose system and choose drive to install boot loader into.
If simple fix does not work, it can also walk you thru a full chroot to uninstall grub & reinstall grub which usually fixes everything, but not often required.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that does not work post link to BootInfo report from Boot-Repair.

---

### Post by eadwacer on 2014-06-20
Thanks. I'll try that in the morning.

---

### Post by eadwacer on 2014-06-20
Boot Repair worked like a charm! It almost took longer to download than it did to fix. So now I have 12.04 running. This weekend I'll try moving up to 14.04.

Thanks for the quick and useful reply. I can always count on you guys.

---


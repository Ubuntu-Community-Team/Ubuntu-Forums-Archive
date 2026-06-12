---
title: "What's the secret with grub?"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by lgb on 2005-04-18
I've been playing around with different disros the past few day and multiple boot systems. The only success I've had with installs recognising other distro was with Ubuntu. Mepis, Fedora, and Kanotix did not recognise any other installs. Ubuntu will not see the Mepis install even though it recognises the ram utility from Mepis. So what's the secret? I've tried editing the menu list from Ubuntu using the same exact syntext with no success. I get an error #19 or 22. I have LBA enabled for the drives involved.

---

### Post by diebels on 2005-04-18
Need a bit more info:
fdisk -l
cat /boot/grub/menu.lst

---

### Post by lgb on 2005-04-19
My problem was that the menu.lst that i was editing was on hdb. It needs to be on the same drive as the mbr. I'll get this linux stuff figured out yet...:smile: Thanks!

---


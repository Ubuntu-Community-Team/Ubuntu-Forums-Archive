---
title: "Installation from HDD didn't create kernel - both 9.04 and 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by drakes on 2009-11-17
Hello, I have big problem with installing new Ubuntu. 

Problem:
both installer of 9.04 and 9.10 don't create any vmlinuz in /boot or link to it in / Installer also don't create grub menu entry for linux, only memtest and Win XP

How I installed Ubuntu:
I don't have CDROM, BIOS can't boot from USB drive. So I followed instruction in [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) I created new partion ext3 and using rsync -a coppied there iso immage. Then i booted from this image and begin installation on clean ext3 partition. Install failed because it couldn't unmount /cdrom, so I used umount -l /cdrom and install finished sucessfully. Exactly the same happens both for 9.10 and 9.04.

What was wrong:
After restart there were no menu entry for Ubuntu, only memtest and Windows XP. I tried to boot manualy from command line, but there were no vmlinuz in /boot

How can I solve this? How to make installer work, so it will create also vmlinuz? Or can I manualy copy some vmlinuz to my /boot and when boot it with some params?

Thanks for any advice, I'm trying to boot any new Ubuntu for 3 days now

---

### Post by presence1960 on 2009-11-17
9. Reboot and keep those fingers crossed. 

That is the last line of the instructions you linked.
To me that says it may or may not work. I would invest in an optical drive since you can't boot from USB.

---


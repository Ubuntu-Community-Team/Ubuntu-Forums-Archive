---
title: "How to install Ubuntu on External USB HardDrive"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by a6laso on 2008-05-25
I installed Ubuntu on an external USB HD, when I boot with external HD connected I can see the booting list and choose to start Win XP ( internal HD) or Ubuntu ( External)..

When I disconnect the external I got GRUB 21 error and can not boot to any OS.

What should I do to be able to boot XP without connecting the external HD ? or how to perform the installation ?


Regards

---

### Post by Pumalite on 2008-05-25
Fix your Windows MBR with you XP installation disk or Super Grub. When you reinstall; disconnect the internal drive or in step 8 go to 'Advanced Tab' and change (hd0) for /dev/xxx, where xxx is your external drive.

---

### Post by meierfra. on 2008-05-25
I wrote a howto for this situation.  Click on "Dual" in my signature.
(If you are using ubuntu 8.04 you also need to look at post 14 in that thread)

---


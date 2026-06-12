---
title: "nothing changed after install on second partition with xp (8.04)"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by h4lfl1ng on 2008-05-12
My Hard drive setup for the install:
[INDENT]hdd
[INDENT]XP PRO - ntfs(50%)[/INDENT]
[INDENT]/      - ext3 (45%)[/INDENT]
[INDENT]/boot  - ext3 (2.5%)[/INDENT]
[INDENT]swap   - ext3 (2.5%)[/INDENT][/INDENT]



I just installed ubuntu 8.04 with that setup. I had xp installed previously. Now the setup finished with no problems but all  get is my old bootup screen for xp.. no ubuntu boot screen. What am I doing wrong?

---

### Post by h4lfl1ng on 2008-05-14
bump! i just tried it again and this time i clicked "advanced" on the last settings window and it has a bootloader option, i set it to the same partition as the install, it didnt do anything.. should i set it to the /boot partition?

---

### Post by prshah on 2008-05-14
> **h4lfl1ng said:**
> My Hard drive setup for the install:
I just installed ubuntu 8.04 with that setup. I had xp installed previously. 

Did you remember to turn off virus protection in the BIOS (may also be called "Boot sector protection"; "Write protect boot sector"; "disallow boot sector changes", etc) _before_ install ?

Check the BIOS for the relevant setting, and, if in fact it doesn't allow change to the boot sector, toggle the setting so that you can make changes to the boot sector, then you should download and use a CD called "Super Grub CD" or something similar, or re-install GRUB using the live CD.

---

### Post by h4lfl1ng on 2008-05-14
i have the phoenix workstationBios v6.00PG and i dont see any settings of that nature.. i also looked at my manual and nothing in there either [http://www.dfi.com.tw/Upload/Manual/lputnf4%20847505101.pdf](http://www.dfi.com.tw/Upload/Manual/lputnf4%20847505101.pdf)

what else could it be? i've installed ubuntu on this system before (v6 and 7)

---

### Post by h4lfl1ng on 2008-05-31
bump? anyone?

---


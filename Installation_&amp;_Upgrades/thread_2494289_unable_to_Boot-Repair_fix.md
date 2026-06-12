---
title: "unable to Boot-Repair fix"
date: 2024-01-11
forum: Installation &amp; Upgrades
---

### Post by jua1976 on 2024-01-11
Hi 

This is my first post

I was cloning my old HD and suddenly the boot was broken

I was try to use boot-repair from
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)
I create this

[B]paste.ubuntu.com/p/fpWmYrjh8n/

anyone may help me?


thanks


[/B]

---

### Post by tea for one on 2024-01-11
Is the report from your old HD or cloned HD?

Do you have backups of your Windows and Ubuntu personal data?

---

### Post by jua1976 on 2024-01-11
cloned disk, old was 250gb, new 1Tb, ubuntu start, windows told boot partition too far from begginiing of disk 

how can i fix it?

---

### Post by tea for one on 2024-01-11
Which cloning software did you use?
Did you remove the original disk and install the cloned disk in the same PC?

Boot-repair will not be able to fix Windows boot problems.
Your Windows OS is installed in old-fashioned Legacy mode with msdos partition table.
I would doubt that current Windows repair tools will help because Windows 10 needs UEFI with GPT.

---


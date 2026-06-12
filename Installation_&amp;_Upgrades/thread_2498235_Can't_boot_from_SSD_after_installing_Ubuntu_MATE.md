---
title: "Can't boot from SSD after installing Ubuntu MATE"
date: 2024-06-05
forum: Installation &amp; Upgrades
---

### Post by probaroa on 2024-06-05
After installing Ubuntu MATE on my SSD, I am unable to boot from it. The system does not present an option to boot from the SSD. I have tried to use live USB of Ubuntu MATE to run the Boot-Repair tool, which suggested reinstalling GRUB2 into the MBR of sda. However, no ESP was detected, and it recommended creating a /boot partition at the start of the disk. I did that but it didn't solve the problem.

I have verified the health of my SSD using smartctl, and it appears to be functioning correctly.

Can you please help me solve this problem

---

### Post by oldfred on 2024-06-05
Boot-Repair suggests you post the pastebin link from its Summary report when asking for help.
You can from Boot-Repair just run report.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

What brand/model system? What video card/chip?

---

### Post by yancek on 2024-06-05
You need to run boot repair with the Create BootInfo Summary option and post the link you get when it finishes here as the information you posted will not help anyone to help you.
Information needed to start is Ubuntu the only OS?  If not what other OS?  Is it an EFI install?  When you access the BIOS firmware boot options, do you see an EFI boot option for ubuntu?  These and many other questions will be answered with the output of boot repair.

---


---
title: "2 drives 2 operating systems"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by badstroller on 2013-02-10
Hello. I am very very new to linux. Today I installed ubuntu on a western digital hdd along side my copy of windows 7 on an ocz ssd. After I installed ubuntu on my hdd i had problems accessing my windows partition on my ssd. After a few hours of screwing around trying to figure out how to access the partition on my ssd, I made a linux live boot-repair usb and ran it. It fixed my bootloader problems and i can now access both operating systems. My question is, If I uninstall ubuntu from my hdd to use my hdd for storage space for windows, will I have problems with booting up windows again? If so, does anyone have any suggestions on how to possibly fix them? Thank you for your time.

---

### Post by darkod on 2013-02-10
It depends whether windows bootloader was left on the ssd or replaced with grub2. If it was replaced by grub2, it will not boot if you delete the ubuntu partition. You will need to restore windows bootloader first and then delete ubuntu.

You can check which bootloader is on both disks by creating the bootinfo summary using boot-repair. The bootloaders are specifying right on the top of the results.

Also, in windows create the rescue cd (I think the option is in the Backup & Restore tool), which can help you boot from it and repair windows bootloader problems.

---

### Post by n4pgw on 2013-02-10
> **badstroller said:**
> Hello. I am very very new to linux. Today I installed ubuntu on a western digital hdd along side my copy of windows 7 on an ocz ssd. After I installed ubuntu on my hdd i had problems accessing my windows partition on my ssd. After a few hours of screwing around trying to figure out how to access the partition on my ssd, I made a linux live boot-repair usb and ran it. It fixed my bootloader problems and i can now access both operating systems. My question is, If I uninstall ubuntu from my hdd to use my hdd for storage space for windows, will I have problems with booting up windows again? If so, does anyone have any suggestions on how to possibly fix them? Thank you for your time.

I have run Ubuntu on a second drive from Windows every since I started using it about 4 years ago.  I have removed the Ubuntu drive and windows continued working, (if that's not an oxymoron).  The thing is that I still had the OS boot options and had to choose the windows option each time (which scrolls down every core update.)

I never uninstalled ubuntu, but I did start a new version on another HDD installed and removed the old ubuntu to format for a data drive.

---


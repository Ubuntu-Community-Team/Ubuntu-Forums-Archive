---
title: "Ubuntu installtion on a already dual boot system"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by RYaNzx on 2010-06-14
Hi im new to linux and after wiping vista off my laptop and using ubuntu i love it.

I want to install it on my main Desktop but im a gamer and will keep win 7 64bit.

my desktop is already dual boot with win 7 64 bit and xp 32bit ...can i just install ubuntu and have it be triple boot ...will it do this automaticly ?

---

### Post by darkod on 2010-06-14
It can, but you have to be aware that windows combines the boot files if you have two or more versions. This is a limitation of windows. At the moment you are selecting your OS from the windows bootloader.
After you install ubuntu and use grub2, it will have only one Windows entry, and in a second menu it will allow to select 7 or XP. That is because grub2 can't split the combined windows boot files now.

Otherwise, just create unallocated space not belonging to any partition, and install there. If resizing the win7 partition, it's best to use the windows Disk Management, and reboot win7 few times to do its disk checks. Only then install ubuntu.

---

### Post by RYaNzx on 2010-06-14
"Otherwise, just create unallocated space not belonging to any partition,  and install there. If resizing the win7 partition, it's best to use the  windows Disk Management, and reboot win7 few times to do its disk  checks. Only then install ubuntu."

this sounds good but what will the boot loader look like? still the linux ,win to win7/xp ?

---

### Post by darkod on 2010-06-14
The bootloader will be grub2 on the MBR and you should get a second menu to select between xp/7 once you select windows in grub2 menu.

---


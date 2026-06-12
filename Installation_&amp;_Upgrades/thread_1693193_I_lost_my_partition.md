---
title: "I lost my partition"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by ozonora on 2011-02-22
Hi all,

I'll try to explain my problem. I have a hard disk with 4 primary partitions. After having Windows 7 installed on partitions 1, 2 and 4, I installed Ubuntu 10.04 in the 3rt partition. Therefore, GRUB replaced the Windows boot loader (if it is called that way).

Last week, I formatted the partition 1 and installed Windows 7 again.

I had two problems:
1. I could not choose between Windows or Ubuntu.
2. I could not choose which Windows installation to use.

I solved the first problem reinstalling GRUB from a Live CD. The problem is that I could choose between Ubuntu or my new Windows installation but I couldn't load the previous Windows.

Therefore, I used the Windows CD to repair the boot. I said: "I'll fix the Windows boot first, so that I can choose between the three of them, and latter I'll replace GRUB".

The thing is that, using Microsoft's tools to repair the boot, now I cannot install GRUB... because my Ubuntu installation has disappeared. From Windows, I can see the 50 GB partition usable, and GRUB can't find my Ubuntu installation.

I don't know if Ubuntu has irremediably disappeared or if it can be fixed. And I would also like to know why Microsoft deleted this partition if it happened.

Thanks a lot.

---

### Post by Quackers on 2011-02-22
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---


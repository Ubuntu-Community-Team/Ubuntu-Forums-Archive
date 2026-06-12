---
title: "Dual Booting Windows 7 and Ubuntu on Two Harddrives"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by wafic01 on 2010-02-01
Hello
I have this problem , i Have two Hard-drives a WD 500Gb Sata with windows 7 installed and an IDE Maxtor 40Gb mounted as slave .I want Ubuntu to be installed on the Maxtor.I usually used to choose grub to be installed on the MBR of the first one , but that meant that every time i needed to reinstall windows or Ubuntu i Would loose both of them , i need some help telling me how to do so , without  effecting the boot loader of the windows but still capable of booting both.Story made short , if i disconnect any of the hard drives i would still be capable of booting into the other.
Thank you

---

### Post by darkod on 2010-02-01
When you are installing ubuntu, at the last screen before clicking Install, click on Advanced and select the bootloader (grub) to be installed where you want. During the install in step 4, if you notice that your IDE is called /dev/sdb for example, just select grub to be installed on /dev/sdb (without any numbers, not /dev/sdb1 or similar).
And that's it. Grub2 will go there and leave your windows bootloader on /dev/sda.

If you already have them installed, you don't have to reinstall ubuntu. Just boot it and you should be able to install grub2 on the IDE with (assuming it's called /dev/sdb, adjust as necessary):

sudo grub-install /dev/sdb

You could also use the cd and the live desktop but the commands are slightly different.

After installing grub2 to the MBR of the IDE disk, if grub is also on the MBR of your windows disk, you can reinstall windows MBR on that disk using instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You have instructions there how to reinstall grub using the livecd too.

---


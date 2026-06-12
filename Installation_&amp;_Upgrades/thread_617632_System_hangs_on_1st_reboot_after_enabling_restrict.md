---
title: "System hangs on 1st reboot after enabling restricted driver for Nvidia"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by hammudi on 2007-11-19
i installed ubuntu gutsy with the live cx with no problems (i have to edit the kernel before booting ubuntu and add "all_generic_ide" at the command line since i have ubuntu installed on my 2nd hdd). i ran the update then activated the restricted driver for nvidia. when asked to reboot i did so but then it hangs after the ubuntu logo and status bar, not even a command is available. when i select recovery console i end up at busybox with (initramfs) and a cursor. i can't use sudo since it says sudo not found. how do i disable the restricted driver? can it be done from grub? i have a dual boot setup with windows xp. my card is an nvidia geforce go 6600 (laptop)

---

### Post by Smartpal on 2007-11-20
check this out....

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

there's a specific bug for this....

---


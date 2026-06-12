---
title: "updating ubuntu to 10.04, grub install devices?"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by arctyler on 2012-06-25
i am a complete newb when it comes to ubuntu, windows on the other hand im not that bad at, but about 2-3 years ago i installed ubuntu to try it out with my friends help, and he serperated the hard drive space so when i boot my PC i can select which operating system i want to use, either windows 7 or ubuntu, and now i am going to update it and start using it again and i almost got it updated and i have a screen that says "configuring grub-pc" then it says "GRUB install devices:" then for the choices i have /dev/sda then -/dev/sda5 then i have /dev/sdc and each of them have a whole list of confusing things in parenthesis after them, which one do i choose? dont forget that i am a complete newb and just about have no idea what i am doing on linux

---

### Post by darkod on 2012-06-25
The /dev/sda, /dev/sdb, etc are the disks, in order how BIOS detects them on the board they get named a, b, c, etc.

If it has a number after the letter, then it's a partition on that disk. So, sda5 for example is partition #5 on the first disk.

The grub2 bootloader usually goes to the MBR of the disk, not to a partition. And it would usually be the first disk, sda, but this can vary with multiple disks and depending how your system is set up.

So, you can try /dev/sda first. Note that in a textual menu the selection is usually done with Space, not Enter. You hit Space so that a * mark appears to mark it as selected, and then you hit Enter to continue. Otherwise if you only hit Enter it can continue with nothing selected.

---

### Post by arctyler on 2012-06-25
thanks man, it was /dev/sda

---


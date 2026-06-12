---
title: "how to make live cd with custom kernel"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2010-01-16
Hello,
    I am using ubuntu 8.04 and i am trying to make iso image cd with running kernel. i know that there is documentation in ubuntu website in"how to make live cd" but the thing is this is my custom kernel. i have my own configuration. so i want this kernel to be work in live cd. so please help me how to do it.
                 Thank you

---

### Post by shariefbe on 2010-02-01
Hello,
   I followed the Link [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) to make mu own live distribution. But in that i saw one step (ie)
"You will need a kernel and an initrd that was built with the Casper scripts. Grab the from your chroot. Use the current version. Note that as of 9.10, the initrd is in lz not gz format... This may cause problems with GRUB2.

cp chroot/boot/vmlinuz-2.6.**-**-generic image/casper/vmlinuz

cp chroot/boot/initrd.img-2.6.**-**-generic image/casper/initrd.gz" 
But in the above step i dont know what is this "casper script". Because i didnt find any kernel image and initrd image in /boot folder. So please help me. How to create "kernel image and initrd image" in /boot folder.

---


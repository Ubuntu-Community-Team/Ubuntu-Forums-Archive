---
title: "Installing another distro from Ubuntu using .ISO file"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by helm10101 on 2016-02-05
Hello,

If I want to try another Linux distro, on empty space on my hard drive, is there a way to do that, without creating a bootable USB/CD?
Can I simply download the .ISO file and maybe install directly from it?

Thanks!

---

### Post by yancek on 2016-02-05
> If I want to try another Linux distro, on empty space on my hard drive,  is there a way to do that, without creating a bootable USB/CD?

Yes.  See the link below.  This will only work with Grub2 as explained and doesn't work with all Linux distributions but should work with most Ubuntu derivatives.  You will need to manually create the menuentry to boot the iso.  Usually works better if installing to a second drive but should work on the same hard drive.  Make sure you have unallocated space or a partition on which to install and select the correct partition during install.

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by ian-weisser on 2016-02-05
It is possible, as yancek has pointed out.
However, it is not recommended for unskilled users.
If you are (or want to become) experienced at troubleshooting GRUB and partitions, then go right ahead.

Why go through all the effort of installing without trying it first?
There are easy ways:
- Create a Virtual Machine (Virtalbox is in the Ubuntu repositories), and launch the install ISO in the VM for your trial.
- Create the a USB-based trial and installer and boot.

Try first, then decide if it's worth installing.

---

### Post by helm10101 on 2016-02-06
Thank you!
I guess I will be using a USB instead :KS

---


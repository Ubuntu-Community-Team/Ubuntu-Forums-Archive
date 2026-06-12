---
title: "facing problem to install nvidia driver"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by khubele on 2019-12-20
hi team ,
i have 3 pc which has nvidia 1050ti ubuntu 18.04,i5 8gen intel, i am trying to install nvidia driver ,but when i installed succefully then i connect with my hdmi cable to the gpu hdmi slot my computer is not starting, same problem i am facing with more 2 computer . can u plzz help me to identify how i can solve this issue.

thanx 

your ubuntu user

mohit

---

### Post by oldfred on 2019-12-20
Is nVidia driver already installed?
Very newest versions (19.10) of Ubuntu will offer to install proprietary drivers, now including nVidia.

But older installs (18.04), still need nomodeset to boot first time into your install, so you can add nVidia driver. Or boot with recovery mode & use command line to install nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---


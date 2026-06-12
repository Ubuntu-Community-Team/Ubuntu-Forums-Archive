---
title: "Problem solving boot-missing issue"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by efeiras on 2016-10-10
Good afternoon,

first of all, thank yo in advance for your help.

Due to an error while cleaning old kernels in my Ubuntu Server 16.04, I let the installation without any kernel and boot.

I try to solve the problem with different tutorials I found in the web, but nothing works.

Last I tried is to run a liveUSB with boot-repair tool, but it seems to be hanged while this message is in the screen: "purge kernels then reinstall last kernel mapper/********-vg-root (ins). This may require several minutes..."

Here is a boot-info log: [http://paste.ubuntu.com/23302094/](http://paste.ubuntu.com/23302094/)

I don't know what else to say...

Thank you again.

---

### Post by Impavidus on 2016-10-10
You can try running a live disk and use chroot: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
Scroll to "Update failure" and run those commands. Instead of /dev/sda1, use your root partition. I think yours is encrypted, but I hope you can find it. Don't forget to mount your /boot partition (/dev/sda2) at the right place too (at /mnt/boot/) and your EFI partition, somewhere between step 3 and 7. Then use apt to install the kernel packages. That should run update-grub automatically.

Note that I never tried this myself, so be careful.

---

### Post by efeiras on 2016-10-11
> **Impavidus said:**
> You can try running a live disk and use chroot: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
Scroll to "Update failure" and run those commands. Instead of /dev/sda1, use your root partition. I think yours is encrypted, but I hope you can find it. Don't forget to mount your /boot partition (/dev/sda2) at the right place too (at /mnt/boot/) and your EFI partition, somewhere between step 3 and 7. Then use apt to install the kernel packages. That should run update-grub automatically.

Note that I never tried this myself, so be careful.

Thank you for your answer...finally the issue is repaired...I tried that method before writing here, but for sure I made something wrong.

Wait never have to do again...:rolleyes:

---

### Post by Impavidus on 2016-10-12
Great. Could you mark this thread as solved? Thread tools (top of page) -> mark as solved.

---


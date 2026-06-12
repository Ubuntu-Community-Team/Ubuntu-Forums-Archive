---
title: "can't boot to Windows 8 after updated Ubuntu 16.04"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by ahmedo047 on 2017-12-26
I have Ubuntu 16.04 and Windows 8.1 on my computer. I couldn't boot to Windows 8 after updated Ubuntu 16.04.
I followed the instructions in this link to solve the issue but that didn't help.
[https://sites.google.com/site/easylinuxtipsproject/6](https://sites.google.com/site/easylinuxtipsproject/6)

Everything seems OK but when I press "Windows Boot Manager ( on /dev/sda/2), Windows doesn't start. What can I do to fix the issue?

By the way, the parts of my disk are here:
sudo fdisk -l

Device          Start        End   Sectors   Size Type
/dev/sda1        2048     616447    614400   300M Windows recovery environment
/dev/sda2      616448     821247    204800   100M EFI System
/dev/sda3      821248    1083391    262144   128M Microsoft reserved
/dev/sda4     1083392  841461759 840378368 400.7G Microsoft basic data
/dev/sda5   841461760 1687535615 846073856 403.5G Microsoft basic data
/dev/sda6  1687535616 1691807743   4272128     2G Linux swap
/dev/sda7  1691807744 1953523711 261715968 124.8G Linux filesystem

---

### Post by leunam12 on 2017-12-26
That tutorial is intended for when you lose the ability to boot back into Ubuntu after a windows update. What you have to do is boot into Windows recovery partition and run the automated startup repair tool. The way you boot into recovery depends on your computer, sometimes in the temporary boot menu you have the option to boot into recovery console. Sometimes you have to press F8 repeatedly when you turn your computer on. If you cannot access your recovery console, then you need a recovery disk. If you don't have a recovery disk, the link below may help you.

[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)

---

### Post by oldfred on 2017-12-26
Grub really only boots working Windows.
Or Windows cannot need chkdsk nor be hibernated.
And Windows updates may turn Fast Start up back on which is always on hibernation.

Can you directly boot Windows from UEFI boot menu, often f10 or f12?
Or direct boot and f8 to get into Windows repair console?

---


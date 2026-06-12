---
title: "Windows 7 Starter and Ubuntu 9.10 do not play nicely in a dual boot"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by webster922 on 2009-12-01
Hello, I just installed Ubuntu 9.10 on my netbook and the installation went smoothly. The only new thing was Grub (1.97 beta 4 I think), and besides the cosmetic issue of Ubuntu being listed first, there were no problems. That is until I booted back into Windows 7. It booted fine but next startup there was a problem with Grub. Now Grub keeps saying:

GRUB loading.
error: unknown filesystem
grub rescue>

It also gives me the option to type in text. I think it has to do with the Windows 7 loader. But I need two answers to this question:

1- How do I restore the bootloader (Windows or Grub) to access Windows 7 and Ubuntu, and
2- How do I prevent this from happening again with different Linux installations or Grub updates?

Any help is appreciated as I cannot access anything but the Grub error on my computer.

---

### Post by oldfred on 2009-12-01
This link has how to reinstall all the boot loaders:

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Is this by any chance a HP or Dell? The new grub2 is larger than old grub or windows boot loader and some serial number info or data is hidden the the unused part of the MBR that now grub2 needs.
HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by webster922 on 2009-12-02
I downloaded the Windows 7 repair disc from [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) and used unetbootin to burn it to a USB drive as my netbook (it is an HP) doesn't have a optical drive. But the unetbootin bootloader only provided one option called Default. Whenever I pressed enter to boot into Default (I thought it was the Windows 7 Restore Disc) the bootloader would only reset its 10 second countdown. I need to know how to transfer the restore disc iso to the USB drive and boot into Window's repair.

---

### Post by webster922 on 2009-12-02
After reinstalling Ubuntu, Grub worked and I went to restore the disk knowing that Windows 7 would corrupt Grub again if I didn't. So I'm back at factory defaults and will install Ubuntu and other distros again. Two final questions (hoping that I don't have to start a new post):

1- How can I use Window's bootloader with Linux, rather than using Grub (Skip Grub Installation)?

2- Anyone know if EasyBCD will work for this sort of thing or have any tips on using it?

---

### Post by phillw on 2009-12-02
> **webster922 said:**
> After reinstalling Ubuntu, Grub worked and I went to restore the disk knowing that Windows 7 would corrupt Grub again if I didn't. So I'm back at factory defaults and will install Ubuntu and other distros again. Two final questions (hoping that I don't have to start a new post):

1- How can I use Window's bootloader with Linux, rather than using Grub (Skip Grub Installation)?

2- Anyone know if EasyBCD will work for this sort of thing or have any tips on using it?


Easy BCD states that it can dual boot with linux etc.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I've never used it - but that site has links to how it works.

Including screen-shots and the all important instructions.

Regards,

Phill.

---

### Post by webster922 on 2009-12-03
Thanks for the replies. I will reinstall Ubuntu after I find out how to keep the Window's bootloader default.

---

### Post by wilee-nilee on 2009-12-03
> **webster922 said:**
> Thanks for the replies. I will reinstall Ubuntu after I find out how to keep the Window's bootloader default.

I can appreciate your wanting to keep with a bootloader that your familiar with but even if there is a way to use the windows bootloader without having Ubuntu installed inside via wubi it is not a good scenario in that the windows setup is way more likely to be problematic and actually become broke which will leave you with windows or Ubuntu.

You are going to be better using a known way to fix this rather then the one your trying to achieve.

---


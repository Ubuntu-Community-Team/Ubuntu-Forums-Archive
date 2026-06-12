---
title: "Windows 7 EFI problem - how to proceed after Boot Repair"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by CraigD92 on 2012-09-17
I recently installed Ubuntu 12.04 alongside Windows 7 on my laptop. After I did this I couldn't boot into Windows 7. I got an error regarding an 'invalid EFI path'. After a bit of searching the forums, I found out about Boot Repair. I ran this in my Ubuntu partition and it has fixed the problem. I can now boot into Windows 7.

In GRUB I now have Ubuntu (this works), memory test, Windows 7 and Windows 7 recovery options (neither of which work) and three "by Boot Repair" options, two of which boot into Windows 7 and one of which does nothing.
I am wondering how to proceed from here.

Is there a way I can safely dual boot a linux distro (namely Ubuntu or a variant) and Windows 7 without having to use the Boot Repair? I am asking this as I'd like to try a experiment with a few distributions such as the upcoming Elementary OS Luna, but I am worried about what might happen.

And if it is possible to do this, is it safe to delete my Ubuntu partition and install something else alongside Windows? On other machines I have gone about this by deleting the Ubuntu partition from within Windows, booting into the Windows Recovery partition and running a command which removes GRUB. However, now the Windows Recovery partition is not accessible, so I am wondering how to proceed.

Here is the URL from the Boot Repair [http://paste.Ubuntu.com/1211025/](http://paste.Ubuntu.com/1211025/)

Any help is much appreciated.

---

### Post by oldfred on 2012-09-19
You need to check that other distributions will install in UEFI mode. Not all do yet.

Grub2 has a bug with UEFI dual booting. I creates a BIOS/MBR chain load entry not a UEFI entry. Boot Repair finds the Windows boot files and creates a correct chain entry. I think Yann was not sure which Windows boot files worked so he created entries for all of them. You can manually edit 40_custom to remove entries that do not work and turn off os-prober so grub update does not create the invalid dual boot entry. You can turn it on again later when they fix it. Not sure if with UEFI it will add any other entries or not (probably not). You may have to manually add those.

When installing with UEFI you have to use the 64bit version. And when booting liveCD or USB you should get two choices, one is BIOS/MBR and the other UEFI. If Windows is UEFI then you need to use UEFI to boot liveCD to get it to install in UEFI mode. But some systems have the new UEFI but Windows is still in BIOS/MBR mode, so everyone is not the same.

---

### Post by YannBuntu on 2012-09-19
Hello
> **CraigD92 said:**
> I recently installed Ubuntu 12.04 alongside Windows 7 on my laptop. After I did this I couldn't boot into Windows 7. I got an error regarding an 'invalid EFI path'.

Please login to your Launchpad account, then mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

> **CraigD92 said:**
> three "by Boot Repair" options, two of which boot into Windows 7 and one of which does nothing.

Is it the "memtest.efi" option?

> **CraigD92 said:**
> Is there a way I can safely dual boot a linux distro (namely Ubuntu or a variant) and Windows 7 without having to use the Boot Repair? I am asking this as I'd like to try a experiment with a few distributions such as the upcoming Elementary OS Luna, but I am worried about what might happen.

All distros using GRUB>=1.98 (including variants and derivatives of Ubuntu>=12.04) should be ok with UEFI, so you can use Boot-Repair or the detailed procedure described here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If i were you, i would not delete Ubuntu. I would install the other system in dualboot (so you can choose Ubuntu/Windows/Elementary in the GRUB menu).

> **CraigD92 said:**
> On other machines I have gone about this by deleting the Ubuntu partition from within Windows

How???
Windows should not be able to access nor delete Ubuntu.

> **CraigD92 said:**
> now the Windows Recovery partition is not accessible

I don't know why you want to use Windows Recovery, but you can check if there is a Recovery entry in your BIOS. Be careful, the Windows Recovery will probably delete your data.

---


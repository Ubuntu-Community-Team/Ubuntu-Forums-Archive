---
title: "Unable to setup Windows 10 + BitLocker / Ubuntu 20.04 + LUKS dual boot"
date: 2021-12-08
forum: Installation &amp; Upgrades
---

### Post by 5e-hb5ntu-we on 2021-12-08
Hi,

I'm closely following this guide: [https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

Difference being that I have an NVMe drive while the author has a SATA SSD.
I have TPM disabled (using BitLocker with a PIN) and Secure Boot enabled.

No matter which options I choose during Ubuntu install (Install third party drivers yes/no, ...), the setup always breaks with "Executing grub-install /dev/nvme0n1 failed".

Why does it fail? How can I fix it?

I have attached some relevant screenshots (I hope).

Booting Windows 10 is working fine at this point.

Thanks!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289605&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289606&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289607&stc=1[/IMG]

---

### Post by tea for one on 2021-12-08
My comments are simply observations rather than specific advice as I do not dual boot with encryption.
> **5e-hb5ntu-we said:**
> 
I have TPM disabled (using BitLocker with a PIN) and Secure Boot enabled.
The guide states
>  Under Security, TPM Security [COLOR="#0000FF"]must[/COLOR] be enabled if you want to easily set up BitLocker in Windows.
I disabled Secure Boot. I’m not sure if this is absolutely required, and you can try leaving it on or re-enabling it when you’re done if you want.

Secondly, if Bitlocker is active when you install Ubuntu, then your EFI partition (nvmeon1p1) file may be unavailable as a target for grub?
Perhaps try with Bitlocker temporarily disabled?

---

### Post by 5e-hb5ntu-we on 2021-12-08
Yeah, having TPM on makes it easier to setup BitLocker, but it works as good with TPM off when setting some group policies before enabling BitLocker. After all, the Windows installation works just fine, so TPM is not  the the culprit here.

The ESP nvme0n1p1 is not encrypted, the ESP is never encrypted as to my knowledge.

---

### Post by tea for one on 2021-12-08
I do not know if the ESP on nvme0n1 is encrypted or not but Bitlocker may prevent it being visible to the Ubuntu installer.

This is why I suggested that you try to install Ubuntu with Bitlocker [COLOR="#0000FF"]temporarily[/COLOR] inactive.

I assume that this is a brand new installation of Windows 10 and Ubuntu and that there is no personal data in either OS.

If there is personal data installed, do not forget your backups.

---


---
title: "Impossible to install Ubuntu on HP Probook 470 G4 from USB flash drive"
date: 2018-01-03
forum: Installation &amp; Upgrades
---

### Post by s-highlander on 2018-01-03
Anybody has installed Ubuntu on HP Probook 470 G4 ? No matter what I do with boot options in BIOS the laptop does not recognize the bootable USB drive with Ubuntu image.

---

### Post by ubfan1 on 2018-01-03
Does the USB work on other machines?  Did you hashcheck the ISO you downloaded?  How did you create the USB install media?

---

### Post by RobGoss on 2018-01-03
Have you tried a different USB port there might be something wrong with the one you're using

---

### Post by tf4545 on 2018-01-03
First things first... What other OS's are installed on the machine in question?

---

### Post by s-highlander on 2018-01-04
Eventually I have figured out that disabling secure boot resolves the issue.

---

### Post by RobGoss on 2018-01-04
> **s-highlander said:**
> Eventually I have figured out that disabling secure boot resolves the issue.

Thanks for sharing your findings I'm sure it will help others with the same issue. If you've your problem you can mark this thread as solved

---

### Post by s-highlander on 2018-01-06
The reason why this installation did not went smooth was that I disabled the "Use Microsoft Key" in BIOS -> Advanced -> Secure Boot. The "Microsoft Key" is the key which was issued by Microsoft and is used by Ubuntu to sign the UEFI bootloader. As a result secure boot did not trust bootloader from Ubuntu distribution. When I enabled "Use Microsoft Key" back , then I could load Ubuntu from USB even with secure boot enabled.
I use BIOS term, however it is not correct anymore because my Probook is shipped with UEFI which replaces BIOS. I confirm that Ubuntu works fine on Probook G4 470  with UEFI and secure boot.

---


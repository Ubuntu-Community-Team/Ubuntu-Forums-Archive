---
title: "Installing as a Dual Boot with Windows 10"
date: 2018-12-11
forum: Installation &amp; Upgrades
---

### Post by esutton2 on 2018-12-11
On the instructions I found for doing this on your website there is section that says normal install,you are supposed to
turn off secure boot .
3 times I have tried to install Ubuntu 18.04 LTS but the section normal install,you are supposed to turn off secure boot does not appear .So it wants to use the whole disk,and I never get to section Install Ubuntu alongside Windows Boot.

How do I Install Ubuntu alongside Windows Boot??

---

### Post by yancek on 2018-12-11
You turn off Secure Boot in the BIOS.  Immediately on boot, you should see an option to acess BIOS or Setup and there should be an option there.  Location of it varies with manufactturer.

Make certain fastboot and hibernation are disabled in windows before booting Ubuntu and I would suggest you read the Ubuntu documentation at the link below on dual booting with windows 10

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-12-11
Many systems do not call it UEFI Secure boot.
My system calls it "Windows" or "Other" and in fine print in manual it says use "Other" if installing Windows 7 as Windows 7 does not support UEFI Secure Boot.
But you still want to be sure to boot in UEFI mode. When Secure boot is off, you may be able to boot in UEFI mode or legacy/BIOS/CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---


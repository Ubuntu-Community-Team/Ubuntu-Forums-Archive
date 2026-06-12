---
title: "I trying to install ubantu but i am getting this message."
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by golchha-niraj on 2016-09-15
I trying to install ubantu but i am getting this message "The 'grub-efi-amd64-signed'Package failed to install into /target/". without the grub boot loader.the installed system will not boot.


i am already turn off the secure boot mode and legancy mode. please help me.please send me how to remove this type of problem.

---

### Post by QIII on 2016-09-15
So you are trying to install in UEFI mode?  Is this a single or multiple boot system?

Prior to attempting to install, did you create and EFI System Partition (ESP) at /boot/efi?

Please do not ask the community to provide help via email.  You asked the question here.  Please have the courtesy to the community to complete your request for support here.  If you do not, the community will be robbed of an opportunity to learn.

---

### Post by golchha-niraj on 2016-09-16
ok,Thank you.

i am installing in windows 8 but i did not work.please help me how to that please tell me steps

what i did i tell you...first i make separate partition of 20Gb then create a bootable pen drive by using usb universal software , it work but it give error in installation.

this type of error "The 'grub-efi-amd64-signed'Package failed to install into /target/". without the grub boot loader.the installed system will not boot.

yes i am trying to install ubantu in UEFI mode.please tell me how to do that

---

### Post by golchha-niraj on 2016-09-16
Hi, how to install ubantu in windows 8 in UEFI mode with single boot system ?
i am already turning off the Secure mode and Legancy mode? but it giving error in installation "The 'grub-efi-amd64-signed'Package failed to install into /target/". without the grub boot loader.the installed system will not boot.
 
please tell me how to do this?

---

### Post by oldfred on 2016-09-16
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You may need chkdsk or dosfsck on the ESP - efi system partition. Sometimes that gets corrupted. But lets review details in Summary Report first.

---

### Post by golchha-niraj on 2016-09-17
thanks oldfred.i solve problem but problem is different one.drive is locked

---

### Post by oldfred on 2016-09-17
Drive is locked or ESP is locked?
Drive locked may be setting in UEFI/BIOS.
Locked ESP may need chkdsk from Windows or dosfsck from Linux. See 
 man dosfsck

---


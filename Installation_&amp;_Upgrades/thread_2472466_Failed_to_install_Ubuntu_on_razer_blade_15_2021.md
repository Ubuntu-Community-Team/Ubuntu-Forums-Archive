---
title: "Failed to install Ubuntu on razer blade 15 2021"
date: 2022-02-28
forum: Installation &amp; Upgrades
---

### Post by ziminz19 on 2022-02-28
I just received my new laptop Razer blade 15 and tried to install Ubuntu 20.04 alongside with the preinstalled windows10. I make the ISO to a usb drive, disabled the fast boot and secure boot in BIOS, and fast startup in windows10. Then, I boot the ISO from my usb and started the installation. But when it came to storage, it only detected 8.2 GB storage, which is exactly my usb drive's storage, and told me that there wasn't enough room to install. But I already freed 400GB storage from the SSD by shrinking the volume of disk in windows' Disk Mangement. What should I do now? It drives me nuts.

---

### Post by ziminz19 on 2022-02-28
Any help?

---

### Post by tea for one on 2022-02-28
New hardware generally needs a newer kernel.
Perhaps try Ubuntu 21.10 in a live session.
You may have to wait for Ubuntu 22.04 in April 2022?

You can run this [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) so that other users may see the hardware details.

---

### Post by ziminz19 on 2022-02-28
I tried 21.10 too, it still didn't work. It's always the same problem-cannot detect my SSD when installing. Do you think reinstall windows10 will help in this situation?

---

### Post by tea for one on 2022-02-28
> **ziminz19 said:**
> I tried 21.10 too, it still didn't work. It's always the same problem-cannot detect my SSD when installing. Do you think reinstall windows10 will help in this situation?

No idea about re-installing Windows because we do not know the status of your system.
Is it encrypted?
Disable Bitlocker?
Do you have 12th Generation Intel?
Is Intel Optane present?
Does Ubuntu see your SSD in a live session?
Did you disable TPM or PTT?
Did you boot Ubuntu in UEFI mode?

A lot of questions can be answered if you run the script indicated in post 3?

---

### Post by ActionParsnip on 2022-02-28
Be sure to shutdown Windows then cold boot to the USB. Windows does weird things to disks when you reboot. You may want to resize the NTFS partition in Windows to make unpartitioned space which you can then use to hold the install of Ubuntu. You may also want to run a full chkdsk on the NTFS partitions to make sure they are consistent and without issues.

---

### Post by ziminz19 on 2022-03-01
> **tea for one said:**
> No idea about re-installing Windows because we do not know the status of your system.
Is it encrypted?
Disable Bitlocker?
Do you have 12th Generation Intel?
Is Intel Optane present?
Does Ubuntu see your SSD in a live session?
Did you disable TPM or PTT?
Did you boot Ubuntu in UEFI mode?

A lot of questions can be answered if you run the script indicated in post 3?
I just run the script on live mode and got the .txt file. I compress it into a zip file so that I could attach it to the website. I'm sorry it took so long. I hope this information would help. Thanks a lot!

---

### Post by ziminz19 on 2022-03-01
> **ActionParsnip said:**
> Be sure to shutdown Windows then cold boot to the USB. Windows does weird things to disks when you reboot. You may want to resize the NTFS partition in Windows to make unpartitioned space which you can then use to hold the install of Ubuntu. You may also want to run a full chkdsk on the NTFS partitions to make sure they are consistent and without issues.

I believe the free space on my SSD is unpartitioned since it shows "unallocated" in the device manager. I tried cold boot to the USB too, but it still didnt recognize my SSD. Weird

---

### Post by tea for one on 2022-03-01
Thank you for supplying the system-info report.
Unfortunately, as you mentioned earlier, there is no information about your internal drive and it is not yet recognised by the Ubuntu installer.

Therefore, something is creating an obstruction.

Double check your UEFI settings - TPM and/or PTT?
Any other UEFI security settings?
Do you possibly need UEFI updates?
Or firmware updates for the internal drive?

What is the make/model of the internal drive?

---

### Post by mIk3_08 on 2022-03-01
> **ziminz19 said:**
> I just received my new laptop Razer blade 15 and tried to install Ubuntu 20.04 alongside with the preinstalled windows10. I make the ISO to a usb drive, disabled the fast boot and secure boot in BIOS, and fast startup in windows10. Then, I boot the ISO from my usb and started the installation. But when it came to storage, it only detected 8.2 GB storage, which is exactly my usb drive's storage, and told me that there wasn't enough room to install. But I already freed 400GB storage from the SSD by shrinking the volume of disk in windows' Disk Mangement. What should I do now? It drives me nuts. Try another new release of Ubuntu or another new Ubuntu flavor. Good luck and cheers

---

### Post by ziminz19 on 2022-03-02
> **tea for one said:**
> Thank you for supplying the system-info report.
Unfortunately, as you mentioned earlier, there is no information about your internal drive and it is not yet recognised by the Ubuntu installer.

Therefore, something is creating an obstruction.

Double check your UEFI settings - TPM and/or PTT?
Any other UEFI security settings?
Do you possibly need UEFI updates?
Or firmware updates for the internal drive?

What is the make/model of the internal drive?
1. I believe my laptop has TPM 2.0 activated, but I'm not sure about PTT since BIOS doesn't give any information about whether PTT is enabled or not.
2. In BIOS, I have Legacy USB support disabled, Intel VMD Technology disabled, fast boot disabled, secure boot disabled, CSM support disabled.
3. I believe the UEFI is up to date, which is AMI version 1.10
4. The internal SSD is NVMe CA6-8D1024, and have the latest drive (Checked in Device Manager).

Hope this will help!

---

### Post by df42 on 2022-03-02
Having exactly the same issue right now.

It may be related to: [https://bugzilla.kernel.org/show_bug.cgi?id=214035](https://bugzilla.kernel.org/show_bug.cgi?id=214035)

I'm trying the latest build now to see if the kernel update solves the issue.

---

### Post by df42 on 2022-03-02
[https://cdimage.ubuntu.com/daily-live/current/jammy-desktop-amd64.iso](https://cdimage.ubuntu.com/daily-live/current/jammy-desktop-amd64.iso)

This latest live version correctly detects all drives and partitions :)

UPDATE:

Installation successful, simply choosing "Install alongside windows..." has chosen the correct unallocated partition aswell.

---

### Post by tea for one on 2022-03-02
@df42 - The bugzilla report and your successful outcome is very informative.

Hopefully, ziminz19 can download and try the 22.04 release currently still in development.

---

### Post by df42 on 2022-03-12
So after a few days of using latest live and a lot of errors, I can not recommend using it in current stage. Nevertheless 21.04 works fine, everything above causes issues. So rn id recommend to direct install 21.04 iso and stay on it till April lts version

---


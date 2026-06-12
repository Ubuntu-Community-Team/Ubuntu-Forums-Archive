---
title: "Ubuntu 22.04 Install doesn't detect nvme drive"
date: 2022-11-14
forum: Installation &amp; Upgrades
---

### Post by moelharrak on 2022-11-14
hi, 
I'm trying to install Ubuntu 22.04 in a new Lenovo T14 Gen 2 (i7-1165G7) Laptop using a USB drive, the issue is that the nvme drive is not detected.
any idea ?
thank you

---

### Post by tea for one on 2022-11-14
Double check any/all of these settings:-

_UEFI settings_

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

_Windows 10/11 settings_

Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage

---

### Post by oldfred on 2022-11-14
Do you just have NVMe drive as internal drive?
Have you updated UEFI firmware & SSD firmware.
If dual booting with Windows that may be done, automatically.

Agree with tea for one's suggestions, but now some new systems do not need AHCI mode.
I have new Dell with i5-11320H chip & only NVMe drive. I forgot to change to AHCI, left Secure boot on, had to turn bitlocker off, but system installed without issue. There is a Intel VMD driver that is used. It says "RAID" but is for one drive & may be same as Windows driver.

VMD driver shows as: 
Intel Volume Management Device NVMe RAID Controller

---

### Post by moelharrak on 2022-11-15
Hi ,
thank you for the reply.
I'm not able to find most of the options mentioned , I did only disable secure boot and TPM.
Just to clarify the situation , the laptop has been bought with windows installed, As usually do , I tried to reinstall the laptop with Ubuntu only, after the disk partitioning an error occur and the installation stopped, When I try again the install , no drive is detected, I even tried with windows and also no drive is detected.
UEFI BIOS Version : N34ET48W(1.48)
Embedded Controller Version: N34HT39W(1.39)
ME Firmware version: 15.0.23.1706
CPU Type: 11 th Gen Intel(R) Core (TM) i7-1165G7
UEFI Secure boot : Off

---

### Post by yancek on 2022-11-15
>  I did only disable secure boot and TPM.

Are you keeping windows?  Which release of windows do you have?  I have windows 10 and if I disable TPM, windows won't boot but the Linux installs will.  This is on an HP though so I don't know if that will be a problem on your Lenovo.

How many drives do you have?  Is windows on the nvme and is that where you want to install Ubuntu?  Is the drive detected in your BIOS firmware?  I would first check to see that hibernation is disable and see if that makes a difference.  If you follow the suggestions in post 2, make sure you make not of exactly what you did and the order in which they were done in case of future problems.  Might try one setting at a time.i

---

### Post by moelharrak on 2022-11-15
I'm not sure if you did understand my explanation.
the Laptop has bought with Windows , I DID resinstall with Ubuntu (erased Windows), When I did partition the drive and apply the changes, and during the installation an error occur and the install stopped. When I try to install again , no drive is detected, I did also try to install using Windows and the same issue no drive is detected.
I have only one drive nvme 512G

---

### Post by tea for one on 2022-11-15
As neither Windows nor Ubuntu can see the nvme drive, it could be a hardware problem.
Can you open the PC and check the connections?

If you boot into a live Ubuntu session and attach a second USB, can Ubuntu see the second usb in the file manager?

---

### Post by moelharrak on 2022-11-15
I think that the issue is with the SSD , I did some research and find out that seems there is an issue with KIOXIA SSD with Linux, some people lost their hard drive while trying to install Linux.
That seems weird but apparently there is an issue with KIOXIA hard drives and Linux

---

### Post by tea for one on 2022-11-15
> **moelharrak said:**
> I think that the issue is with the SSD , I did some research and find out that seems there is an issue with KIOXIA SSD with Linux, some people lost their hard drive while trying to install Linux.
That seems weird but apparently there is an issue with KIOXIA hard drives and Linux
The loss of a SSD after trying to install Ubuntu - That is awful.

Perhaps you need to update the SSD firmware?
Kioxia and Lenovo are members of the Linux Vendor Firmware Service (LVFS), so there may be some hope.
[https://fwupd.org/lvfs/search?value=kioxia](https://fwupd.org/lvfs/search?value=kioxia)

---

### Post by yancek on 2022-11-15
> I'm not sure if you did understand my explanation. 

There wasn't much to understand as your initial post was not very informative, only the name of the computer and that you were trying to install Ubuntu and the drive wasn't seen

Questions asked which you have not answered:
Is the drive seen in your BIOS firmware?
Which release of windows, 11, 10 something else?
Did you disable hibernation before overwriting windows?
How did you partition the drive?  Did you use the Ubuntu installer?
If you were initially able to boot and install Ubuntu and got an error, why did you not post what the specific error was?  That would have been helpful.
 
>   I even tried with windows and also no drive is detected.

What did you use to do that as you previously indicated that you had installed Ubuntu over windows?

The first thing I would check is to verify the drive is recognized in the BIOS.  If it is not, then no operating system will see it either.

---

### Post by mIk3_08 on 2022-11-16
> **moelharrak said:**
> When I did partition the drive and apply the changes, and during the installation an error occur and the install stopped. When I try to install again , no drive is detected, I did also try to install using Windows and the same issue no drive is detected.
I have only one drive nvme 512G Have you checked your UEFI/BIOS utility settings. Is your nvme available their? That is impossible it went missing when trying to install Ubuntu. Did you try to remove the nvme storage, detach, disconnect and reconnect the device storage in your machine? If you did try to disconnect and reconnect the nvme storage maybe you have not properly place or attached it correctly. Try to check it. Regards and cheers.

---

### Post by MAFoElffen on 2022-11-16
> **moelharrak said:**
> I think that the issue is with the SSD , I did some research and find out that seems [COLOR=#ff0000]there is an issue with KIOXIA SSD with Linux[/COLOR], some people lost their hard drive while trying to install Linux.
That seems weird but apparently there is an issue with KIOXIA hard drives and Linux
**Kioxia BG5 SSD with firmware 1106ANLA or earlier may become permanently undetectable:** Lenovo says that may happen with any Linux, Windows 10 or 11... But specifically mentions Ubuntu 20.04 LTS:
[https://support.lenovo.com/us/en/solutions/ht514140-kioxia-bg5-ssd-may-become-permanently-undetectable-after-installing-large-software-packages-or-handling-large-files-and-bios-will-display-a-2100-or-2102-error-ubuntu-20044-lts](https://support.lenovo.com/us/en/solutions/ht514140-kioxia-bg5-ssd-may-become-permanently-undetectable-after-installing-large-software-packages-or-handling-large-files-and-bios-will-display-a-2100-or-2102-error-ubuntu-20044-lts)  

Which also mentions that if Lenovo, they will replace the drive. Even if out of warranty (If Lenovo), I would call support and quote that service report and try to have them be good on their word. They admitted the specific equipment was at fault. If not Lenovo, I would contact Kioxia support. (([EMAIL="KAI_SSD_WARRANTY@KIOXIA.COM"]KAI_SSD_WARRANTY@KIOXIA.COM[/EMAIL] & [EMAIL="KAI_SSD_TECHHELP@KIOXIA.COM"]KAI_SSD_TECHHELP@KIOXIA.COM[/EMAIL]))

And there was a firmware update to those specific drives that will prevent it, if flashed before that happens:
[https://fwupd.org/lvfs/devices/com.lenovo.bg5-nvme-ssd.firmware](https://fwupd.org/lvfs/devices/com.lenovo.bg5-nvme-ssd.firmware)

---

### Post by tea for one on 2022-11-16
Very useful information excavated by MAFoElffen. That must have taken a bit of time.
Hopefully, the OP can pursue a replacement drive.

---


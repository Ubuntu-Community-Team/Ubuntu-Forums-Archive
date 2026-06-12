---
title: "Unable to install ubuntu 20.04 using USB stick"
date: 2023-12-05
forum: Installation &amp; Upgrades
---

### Post by suntofu on 2023-12-05
I am trying to install ubuntu 20.04 through a USB stick (using UEFI).
My current setup is using Intel NUC8i7BEH. I am currently using Intel Iris Graphics 655 in the NUC. The Ubuntu iso file I am using is called ubuntu-20.04.6-desktop-amd64. 


When I boot up the NUC, I would press f10 to enter the boot manager(I think that is what its called) and then boot the USB device. At the grub page, I choose the option "try or install ubuntu" and had to change quiet splash to "noacpi acpi=off" and then I boot. It would bring me to the home page when I would select try ubuntu. If I were to select install ubuntu I would be able to go through the entire process until the installation part where I would get the error:


````
Unable to Install GRUB in /dev/nvme.
```


So after searching the internet for answers, I tried to solve this issue by using boot-repair. However, boot-repairs gives me another error: 


    ````

   [FONT=var(--ff-mono)]An error occured during the repair[/FONT]
   Error:NVram is locked(ubuntu  not found in efibootmgr)
   .... 
   Locked-NVram detected
```I have tried (and I apologise if I missed out something because I genuinely can't rmb anything rn)


 1. Resetting my BIOS
 2. Updating my BIOS to the latest version
 3. Disabling UEFI password 
 4. Disabling secure boot and fast boot


So far I have not seen an actual solutions as many people seems to recommend different things but one of the more common things was talking about the EFI causing some issues. May I ask are there any solutions to solving either one of these problems?

EDIT 1: Added more details of my situation

---

### Post by tea for one on 2023-12-05
Post the link to your boot-repair report so that we can see full details.

---

### Post by oldfred on 2023-12-05
Also here:
[https://askubuntu.com/questions/1494988/i-cant-install-ubuntu-20-04-through-usb-stick](https://askubuntu.com/questions/1494988/i-cant-install-ubuntu-20-04-through-usb-stick)

If very new computer, you may need 22.04 LTS or 23.10. To have latest kernel & drivers for a new system.
But 22.04 lighter flavors will work on older systems also. I used Kubuntu 22.04 on my 2006 laptop where full Ubuntu would not work.

---

### Post by oldfred on 2023-12-05
You mention Locked NVRAM issue.
While not for a NUC, often issues across UEFI are similar.

We are seeing a lot more "locked NVRAM" issues. But none have posted an exact answer or reason.
Locked NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)


HP PROBOOK with preinstalled WINDOWS 11. Locked NVRAM Larger ESP
[https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr](https://askubuntu.com/questions/1490046/grub-install-fails-at-the-end-of-ubuntu-22-04-installation-on-a-uefi-based-hp-pr)

---

### Post by suntofu on 2023-12-05
The computer Im using is around 5 years old I think. It is a NUC8i7BEH

---

### Post by oldfred on 2023-12-05
Some NUC info. But I do not use a NUC, so cannot test or really know anything other than what others have posted.
How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)
Updated drivers for Hades Canyon
[https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay](https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay)

---

### Post by tea for one on 2023-12-05
> **suntofu said:**
> ```

   [FONT=var(--ff-mono)]An error occured during the repair[/FONT]
   Error:NVram is locked(ubuntu  not found in efibootmgr)
   .... 
   Locked-NVram detected
```
In your UEFI settings, disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)

---


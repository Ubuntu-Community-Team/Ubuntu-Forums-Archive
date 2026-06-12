---
title: "Ubuntu installer does not recognize SSD"
date: 2018-12-24
forum: Installation &amp; Upgrades
---

### Post by mancolric on 2018-12-24
Hello,

The Ubuntu 18.04.1 installer does not recognize the SSD hard drive, where I have a pre-installed version of Windows 10 that I want to erase.

According to the posts[INDENT][https://ubuntuforums.org/showthread.php?t=2380454,]("https://ubuntuforums.org/showthread.php?t=2380454")
[/INDENT]
[INDENT][https://askubuntu.com/questions/932997/why-cannot-the-ubuntu-installer-recognize-my-ssd](https://askubuntu.com/questions/932997/why-cannot-the-ubuntu-installer-recognize-my-ssd),
[/INDENT]
I have enabled AHCI Sata Mode and disabled secure boot, fast boot and Windows hibernation, but nothing worked.

System details:[INDENT]Intel i7-8750H
SSD (not detected by the installer): 256 GB INTEL® 760p M.2 NVMe PCIe SSD
SSHD (detected by the installer): 500 SSHD SEAGATE FIRECUDA
[/INDENT]

Apparently, the BIOS doesn't detect the SSD either.


Could you please help me?

Thank you
---

---

### Post by oldfred on 2018-12-24
Many SSD also need firmware updated.

But if UEFI/BIOS does not see it, then no software can either.
Double check motherboard and how NVMe device is connected.
Some UEFI also have settings to turn on/off a drive. You may want to also check those.

---

### Post by mancolric on 2018-12-25
The pre-installed version of W10 does see the SSD, so it must be well connected. However, if I try Ubuntu without installing and use GParted, the SSD drive doesn't show up. I don't see any options in the BIOS to turn off/on the Drive.

---

### Post by oldfred on 2018-12-25
Then have you updated UEFI & SSD firmware?

[https://downloadcenter.intel.com/product/134583/Intel-SSD-760p-Series-256GB-M-2-80mm-PCIe-3-0-x4-3D2-TLC-](https://downloadcenter.intel.com/product/134583/Intel-SSD-760p-Series-256GB-M-2-80mm-PCIe-3-0-x4-3D2-TLC-)

---

### Post by mancolric on 2018-12-27
I am trying to update the SSD firmware. I have downloaded the iso file in the link [https://downloadcenter.intel.com/download/28174/Intel-SSD-Firmware-Update-Tool?product=134583](https://downloadcenter.intel.com/download/28174/Intel-SSD-Firmware-Update-Tool?product=134583), burned it to a bootable USB and run the USB from UEFI. Then I see the message "GNU GRUB version 2.00... Minimal BASH-like line editing is supported... grub>". What do I have to do now?

---

### Post by oldfred on 2018-12-27
If you are getting grub you probably are reverting to your system?
Did you extract ISO or copy it to flash drive?
Not sure what tools the ISO expects.
Did it have more detailed instructions somewhere?

---

### Post by mancolric on 2018-12-27
I only see the grub console when I attempt to boot from the SSD controller bootable USB. Otherwise, Ubuntu (which I have installed provisionally at the SSHD) starts fine.

I have burned the ISO file to the USB as indicated in the post [https://fossbytes.com/create-bootable-usb-media-from-iso-ubuntu/](https://fossbytes.com/create-bootable-usb-media-from-iso-ubuntu/) (I chose the third way).

I think the USB is fine because I can start it from Virtual Box. However, it stucks there in "Decompressing Linux... done... Booting the kernel".

I was wrong when I said the BIOS didn't recognize the SSD. It does recognize it but I didn't see it.

The only way I have found for Ubuntu to recognize my SSD is to close the screen and to open it again. After sleeping, Ubuntu is perfectly able to see my SSD.

---

### Post by mancolric on 2018-12-27
Here are more detailed instructions: [https://www.intel.com/content/www/us/en/support/articles/000020439/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000020439/memory-and-storage.html)

---

### Post by oldfred on 2018-12-27
It is interesting that you have to boot Intel update tool with Legacy boot mode.

Intel was the developer of EFI (now UEFI v1) which then became UEFI. And UEFI has been the standard on Apple Mac since Apple converted to Intel chips. And Microsoft made UEFI standard on PC when it released Windows 8 five years ago.

---

### Post by mancolric on 2018-12-27
My BIOS menu is very limited and it doesn't seem to allow me to switch between Legacy/UEFI modes. What I see is the classical BIOS menu, so I think I must be bootuing from BIOS.

The fact that Ubuntu is able to detect the SSD after sleeping doesn't have anything to do with the problem?

---

### Post by mancolric on 2018-12-27
Following the post [https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19](https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19), I have added the modification
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvme_core.default_ps_max_latency_us=200"
[FONT=arial]to the /etc/default/grub file in the SSHD, and updated grub with [FONT=courier new]sudo update-grub.[/FONT]

Now, the Ubuntu OS installed in the SSHD detects the SSD since I boot the computer.

I have tried the following. I have booted from the USB and selected "Try Ubuntu". The live Ubuntu didn't recognize the SSD. Therefore, I slept the computer and awaked it. Then, the live Ubuntu was able to see the SSD, and I installed Ubuntu in the SSD. However, I am unable to modify the grub file of the SSD's installation and, then, I am unable to succesfully boot the SSD partition.

Do you know how can I fix this problem?[/FONT]

---

### Post by oldfred on 2018-12-27
You can edit grub2's boot parameters the same way you edit for the nomodeset boot parameter which is one of the most common required parameters.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Instructions above should be changed to use sudo -H with any graphical app like gedit.
[SIZE=1]sudo -H gedit /etc/default/grub
or 
sudo nano /etc/default/grub
[/SIZE]

---

### Post by mancolric on 2018-12-28
Thank you very much, Oldfred, it worked by changing grub booting options.

I am going to mark the post as [Solved] but, before, I am going to summarize all the process so that the post can be helpful to other people in the future.

---

### Post by mancolric on 2018-12-28
Steps to make Ubuntu see the SSD and to install Ubuntu there:

1) Boot from the USB with Ubuntu's live installation.

2) When the grub's menu appears with the options, "Try Ubuntu", "Install Ubuntu", press "e" and you will be able to edit grub's booting options. You will see something similar to this: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters).

3) Go to the "linux" line and, after ```
quiet splash
```, add the words[FONT=arial] ```
[SIZE=3]nvme_core.default_ps_max_latency_us=200[/SIZE]
```[/FONT] (see also [https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19](https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19)). Then press Ctrl+X to boot with these new option included.

4) The Ubuntu installer should now be able to see the SSD. Proceed to install.

5) Steps 1 to 4 only manage to make the Ubuntu installer to see SSD. The new Ubuntu SSD installation will present the same problem: it will not be able to see the SSD at all and will not be able to boot properly. Thus, when booting the new Ubuntu SSD installation for the first time, press "e" at the grub menu ("Ubuntu", "Advanced options for Ubuntu", etc) and repeat steps 1 to 3.

6) Now the Ubuntu SSD installation should be able to boot properly, but the previous modifications are only provisional. In order to make the booting option [FONT=arial]```
[SIZE=3]nvme_core.default_ps_max_latency_us=200[/SIZE]
```[/FONT] permanent, open the grub file[INDENT]```
sudo nano /etc/default/grub
```
[/INDENT]
make the modification[INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvme_core.default_ps_max_latency_us=200"
```
[/INDENT]
save the file, and update the grub[INDENT]```
sudo update-grub
```

[/INDENT]
7) Enjoy!

---


---
title: "Ubuntu does not boot after second system install of Ubuntu on SSD (with another Ubunt"
date: 2019-08-15
forum: Installation &amp; Upgrades
---

### Post by tellapu on 2019-08-15
The setting up of the new computer has been not been smooth so far and before I do more harm, I would be happy to get more input. The system has SSD and HDD and I wanted to install Ubuntu 19.04 with the USB installer on the SSD (LVM + LUKS). **But it did not recognise the SSD and installed Ubuntu on the HDD**. This worked worked fine but I realised it only after the installation that Ubuntu is on the wrong disk. I tried to find some guidance on the internet but did not much but to j**ust install Ubuntu again but this time on the SSD**. But the **SSD would not recognized by the Ubuntu Installer** although the pre-installed Windows would still start normally. 

After the start of the USB installer I would see a quick error: Couldn't get size:0x800000000000000e.
The error is probably not related to the SSD:
[https://bugzilla.redhat.com/show_bug.cgi?id=974841](https://bugzilla.redhat.com/show_bug.cgi?id=974841)
[https://ubuntuforums.org/showthread.php?t=2424000&highlight=couldn%27t+size](https://ubuntuforums.org/showthread.php?t=2424000&highlight=couldn%27t+size)

I followed some tips to make the SSD visible:
- Windows fast startup turned off ([https://askubuntu.com/questions/843153/unable-to-mount-windows-10-partition-it-is-in-an-unsafe-state](https://askubuntu.com/questions/843153/unable-to-mount-windows-10-partition-it-is-in-an-unsafe-state))
- Secure boot (UEFI) turned off
- Start "Install Ubuntu" with nomedeset added
[https://askubuntu.com/questions/1095766/ubuntu-bootable-drive-couldnt-get-size-0x800000000000000e-modsign-couldnt](https://askubuntu.com/questions/1095766/ubuntu-bootable-drive-couldnt-get-size-0x800000000000000e-modsign-couldnt)
[https://elementaryos.stackexchange.com/questions/10000/elementary-os-wont-boot-past-live-cd-screen](https://elementaryos.stackexchange.com/questions/10000/elementary-os-wont-boot-past-live-cd-screen)
But only **when I changed the SATA mode from RST(RAID) to AHCI in the UEFI it worked **([https://askubuntu.com/questions/1072478/ubuntu-18-04-fail-to-recognize-my-second-nvme-ssd?rq=1](https://askubuntu.com/questions/1072478/ubuntu-18-04-fail-to-recognize-my-second-nvme-ssd?rq=1))
**The second installation went well**, I could choose on which harddisk I wanted to install Ubuntu 19.04 (LVM+LUKS). BUT ...
When I wanted to boot the computer then, it seemed to try to start with the **SSD but stopped with a squeaking sound**, then it starts the **HDD** (called ubuntu in the UEFI) which then shows a **black screen with GRUB command line**.

Following [https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/) respectively [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/), **I ran the Boot repair but it could not help**. This was the **Paste of diagnostics: **[http://paste.ubuntu.com/p/tynzDQmQND/](http://paste.ubuntu.com/p/tynzDQmQND/)

And this is the output after the repair trial: [http://paste.ubuntu.com/p/PspwxnBZgT/](http://paste.ubuntu.com/p/PspwxnBZgT/)
Nothing has changed it seemed.
Before I attempt to reinstall and maybe reformat the HDD, I did not find any other guidance yet, [B]I hope to get some input from you before I make things worse. \\
Thanks in advance very much![/B]

---

### Post by yancek on 2019-08-15
Your 1.8TB drive shows as sda and you have an EFI partition there with the necessary Grub/EFI files.  This partition is sda1.
Your 2nd install to the SSD which shows as /dev/nvme0n1 also has an EFI partition /dev/nvme0n1p1
If you want to boot the SSD, you need to set it to first boot priority from the boot options in the BIOS.  Have you done that?

The output of efiibootmgr shows several options, one of which is Ubuntu which is the install on the hard drive "Boot0002" and I believe the SSD is Boot0004.  You can try 
setting this with the efibootmgr or doing it in the BIOS.  The BIOS would probably work better?

2 things I notice in the boot repair which are problematic.  First, the boot repair output does not show the grub.cfg file which should be on the root filesystem partition 
of each drive.  THis file contains the Grub boot menu.  Not sure why that doesn't show.  If they don't exist, the systems won't boot but it might be they were just not 
detected by boot repair for some reason.  Use your install USB/DVD to mount each system partiton to verify there is a grub.cfg file in the /boot/grub directory of each 
root filesystem.

The second thing is that there is a reference in your post to windows and an entry in the efibootmgr output to a windows entry but no other sign of a windows system installed?

---

### Post by tellapu on 2019-08-15
@yancek Thanks a lot for your reply! The **goal** for my Dell Inspiron 7580 is to install **Ubuntu** (LVM/LUKS) on the **SSD** and use the **HDD** (LUKS-encrypted) for the **bigger files** (e.g. Video, Pictures, Download, ...). Therefore I don't need the Ubuntu system on the HDD and wondered whether I should just format the HDD clean.

> **yancek said:**
> Your 1.8TB drive shows as sda and you have an EFI partition there with the necessary Grub/EFI files.  This partition is sda1.
Your 2nd install to the SSD which shows as /dev/nvme0n1 also has an EFI partition /dev/nvme0n1p1
If you want to boot the SSD, you need to set it to first boot priority from the boot options in the BIOS.  Have you done that?

The output of efiibootmgr shows several options, one of which is Ubuntu which is the install on the hard drive "Boot0002" and I believe the SSD is Boot0004.  You can try setting this with the efibootmgr or doing it in the BIOS.  The BIOS would probably work better? 

Yes, I set the SSD as the first option in the BIOS and I think system tries to boot from the SSD but **the SSD stops with a squeaking sound**, then it tries to boot from the **HDD** as the option (called ubuntu in the UEFI) which then shows a **black screen with GRUB command line**.
Interestingly in the BIOS the **SSD** is **called** *"UEFI: BC501 NVMe SK hynix 128GB, Partition 1"* but the **HDD** *"ubuntu"*.

> **yancek said:**
>  2 things I notice in the boot repair which are problematic.  First, the boot repair output does not show the grub.cfg file which should be on the root filesystem partition of each drive.  THis file contains the Grub boot menu.  Not sure why that doesn't show.  If they don't exist, the systems won't boot but it might be they were just not detected by boot repair for some reason.  Use your install USB/DVD to mount each system partiton to verify there is a grub.cfg file in the /boot/grub directory of each root filesystem.

I will try to **mount the system** partition especially on the SSD (I will need to figure out how to mount it as I have not done this yet). I don't really need the system on the HDD, should I still try to find the **grub.cfg** on the HDD anyway?

> **yancek said:**
> The second thing is that there is a reference in your post to windows and an entry in the efibootmgr output to a windows entry but no other sign of a windows system installed?

Yes, this is weird! Windows 10 was on the SSD (pre-installed from Dell) which was overwritten with Ubuntu on the second install and therefore there was a **Windows Boot Manager **in the BIOS boot sequence and it is still there. I "unticked" it from the boot sequence, though. Shall I enable it again? Should I find a way to delete it?

---

### Post by tellapu on 2019-08-15
@yancek Thanks again for your fast reply as it triggered some thoughts! As I was writing the last message to you I was let to integrate the model name of the laptop as I had **"Ubuntu problems" in the past that were specific for a laptop model**. After writing the message I searched the internet "Ubuntu on** Dell Inspiron 7580**" and booting problems and I found first a discouraging page:
[https://certification.ubuntu.com/hardware/201807-26317/](https://certification.ubuntu.com/hardware/201807-26317/), it says: 
"**Standard images of Ubuntu may not work** at all on the system or may not  work well, though Canonical and computer manufacturers will try to  certify the system with future standard releases of Ubuntu."
This is weird as the special image would work and why would Dell not feed the changes back into the community and Canonical? Why can they not offer the special image to download?

But I also found another thread which seemed to me it could be helpful: 
[https://askubuntu.com/a/920272/30631](https://askubuntu.com/a/920272/30631)
I followed the answer, not thinking of an USB-drive but of my SSD. The only difference was that I had to choose **FS1: (FSO: did not work, it booted the Grub probably from the HDD)**

And it magically **worked**! **Hallelujah**! :KS
I checked the boot and efi partition (of the SDD) and they both have **grub.cfg**.
Now I have to deal with the encrypted HDD but this can wait till tomorrow as it is time to sleep for me.
Thanks again for your inspiration!

---

### Post by yancek on 2019-08-15
Glad it worked for you and good luck with the encryption.

---


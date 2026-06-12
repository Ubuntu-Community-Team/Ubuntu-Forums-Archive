---
title: "Ubuntu 24.10 boot loader cannot be seen at all in Asus EUFI"
date: 2024-10-20
forum: Installation &amp; Upgrades
---

### Post by Mr Bean on 2024-10-20
Hi I have tried twice now to install Ubuntu 24.10, both using the erase full disk option on a 4TB NVME. 

The first time I did ZFS + Encryption, the second time I did LVM + Encryption

Both times it created a FAT32 boot efi partition but neither time was my Asus motherboard able to detect this or boot from it. 

Secure Boot is enabled and Windows is running off a SATA drive. 

The motherboard only detects the Windows boot loader. It has no problems booting off the USB installer. 

ROG Strix B550-A gaming motherboard with BIOS version 3607

I think maybe it could be a Secure Boot issue but I don't want to break my Windows install. My Windows install is not encrypted but if I mess with Secure Boot settings in the motherboard I worry I could still break it. 

Looking for some guidance.

---

### Post by yancek on 2024-10-20
Is this 4TB drive new or had you used it before?  What version of windows are you using?  Is windows an EFI install?  I don't know that Secure Boot would be an issue but windows should be able to boot with it On or Off and you should be able to turn it Off or On quite simply in the BIOS.

---

### Post by Mr Bean on 2024-10-20
Windows is EFI, the 4TB drive was previously used for file storage but I recreated the file system a couple of times

---

### Post by Mr Bean on 2024-10-25
I would like to if possible leave secure boot on and have ubuntu work with secure boot. It is supported right?

---

### Post by tea for one on 2024-10-26
> **Mr Bean said:**
> I would like to if possible leave secure boot on and have ubuntu work with secure boot. It is supported right?
Both Windows 10/11 and Ubuntu 24.04/24.10 will boot with Secure Boot enabled or disabled.

When your PC cannot see your nvme disk with Ubuntu, it's worth checking other security features e.g.
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
PSP (Platform Security Processor)
Device Guard 
OS Optimised Defaults 
Lock UEFI BIOS Settings
Boot Order Lock
Enable Microsoft 3rd Party UEFI CA

---

### Post by Mr Bean on 2024-10-26
I had a look around the EUFI and I am pretty sure it is set up correctly, I did not want to change anything, so I just installed Linux Mint with secure boot and that worked first time, no hassle.  I often find when dealing with Linux and specific hardware it is better to just keep trying distros until one works, rather than faff around trying to make a specific one work. In my mind, the fact that Mint worked proves the issue is Ubuntu. 

I've been an Ubuntu user for a long time, but I am not loyal to it in the sense that I will refuse to use anything else. To me having any working Linux desktop with secure boot is more of a priority than figuring out why Ubuntu specifically did not work.

This is the second time in recent memory that the Ubuntu installer has prevented me from using Ubuntu. The last time was a small intel webserver and in that case Debian installer worked. I was sincerely expecting the opposite result, that Ubuntu installer would be the most polished.

---


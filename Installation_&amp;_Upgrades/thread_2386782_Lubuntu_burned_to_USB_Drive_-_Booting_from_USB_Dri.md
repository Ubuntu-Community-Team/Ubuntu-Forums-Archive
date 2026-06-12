---
title: "Lubuntu burned to USB Drive - Booting from USB Drive runs Windows instead"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by nutik02 on 2018-03-10
Hi, I'm trying to install Lubuntu as Windows has become increasingly unreliable for me. My Tablet PC lacks the minimum requirements for it, and it frequently crashes. I burned Lubuntu 16.04.3 LTS (same result with 17.10.1) with Pendrivelinux, and my computer found the option to boot from SanDisk (the USB). I attempt to boot with that, but it goes directly to Windows.

[https://www.amazon.com/RCA-W101-V2-Detachable-Blue/dp/B018C68P96](https://www.amazon.com/RCA-W101-V2-Detachable-Blue/dp/B018C68P96) here is the computer I got.

Non-overclocked, it says my processor is only 1.33GHz.
I only have 1 GB of RAM.
I'm not fully sure with graphics card, but I'd assume it falls under "Integrated."

Does anybody know other things I can try to do? :)

---

### Post by Mark Phelps on 2018-03-10
From what I read, your tablet DOES meet the minimum requirements for Win10 -- but just barely.

That said, if I had my way, every one of these OEMs that sold Win10 PCs with only 32GB of "drive space" would be shut down!  That simply does NOT WORK with Win10 and Microsoft's policy of forcing major Win10 versions on their userbase every few months!  The HP Stream line of laptops suffers from the same problems.

My guess, from your description, is that your tablet is trying to boot from the USB stick but failing in the process and falling back to boot from the next device -- the "disk" (which is actually 32GB of memory stick).  

You should try booting from that USB stick in another PC to confirm it actually works.  IF it does, then it looks like you're stuck with the tablet running Win10.

---

### Post by oldfred on 2018-03-10
Is this one of the systems with 32 bit UEFI, but is 64 bit system?
Those were configured back when Linux did not have 32 bit UEFI, so they wanted a Windows only system.

The 32 bit UEFI boot is not in the download, you have to down load the 32 bit file, bootia32.efi and copy that onto flash drive.
The standard UEFI 64 bit boot loader for external devices is bootx64.efi.

Details on downloading file for booting 32 bit UEFI.
[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)
[https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188](https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188)
[https://ubuntuforums.org/showthread.php?t=2254317](https://ubuntuforums.org/showthread.php?t=2254317)

Many instructions are older and have you compiling your own, you now just need to download grub bootloader for 32 bit and rename to bootia32.efi.

---

### Post by nutik02 on 2018-03-10
> **Mark Phelps said:**
> From what I read, your tablet DOES meet the minimum requirements for Win10 -- but just barely.

That said, if I had my way, every one of these OEMs that sold Win10 PCs with only 32GB of "drive space" would be shut down!  That simply does NOT WORK with Win10 and Microsoft's policy of forcing major Win10 versions on their userbase every few months!  The HP Stream line of laptops suffers from the same problems.

My guess, from your description, is that your tablet is trying to boot from the USB stick but failing in the process and falling back to boot from the next device -- the "disk" (which is actually 32GB of memory stick).  

You should try booting from that USB stick in another PC to confirm it actually works.  IF it does, then it looks like you're stuck with the tablet running Win10.

Hi! I tried this, and it had still taken me to Windows on the other computer. That means that this computer still has potential! :)

---

### Post by nutik02 on 2018-03-10
> **oldfred said:**
> Is this one of the systems with 32 bit UEFI, but is 64 bit system?
Those were configured back when Linux did not have 32 bit UEFI, so they wanted a Windows only system.

The 32 bit UEFI boot is not in the download, you have to down load the 32 bit file, bootia32.efi and copy that onto flash drive.
The standard UEFI 64 bit boot loader for external devices is bootx64.efi.

Details on downloading file for booting 32 bit UEFI.
[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)
[https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188](https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188)
[https://ubuntuforums.org/showthread.php?t=2254317](https://ubuntuforums.org/showthread.php?t=2254317)

Many instructions are older and have you compiling your own, you now just need to download grub bootloader for 32 bit and rename to bootia32.efi.
 
Hi, with trying the instructions on the first link, I got it to appear! However, now it boots up the GRUB 2.00 Shell, although the expected installer did not properly load, even after creating grub.cfg.

---


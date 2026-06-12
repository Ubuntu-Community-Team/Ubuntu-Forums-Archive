---
title: "How to REPLACE Windows with Ubuntu (UEFI, secure boot)?"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by gnugu on 2016-05-04
Hi All,
most of the posts I have seen are trying to install Ubuntu side by side with Windows.

Here is what I have:
Brand new Dell Vostro 3458 BTX, Windows 10 Home 64bit. In boot options it used to show "Windows Boot Manager". My [BIOS settings are as such]("http://www.dell.com/support/article/us/en/04/SLN301754/en#BIOS").
I have USB with UbuntuGnome 16.04LTS. I have created the USB with UNetbootin as well as [this method]("http://ubuntuforums.org/showthread.php?t=2299040").
Both of the methods do boot USB as UEFI.
I have replaced Windows 10 with said Ubuntu Gnome. When I pull USB stick out and reboot, there is no UEFI option to boot.

I put the USB back, boot to it, start GParted and my /dev/sda1 is fat32 EFI System Partition. My /dev/sda2 is EXT4, /dev/sda3 is linux-swap and a bit of unallocated. Nautilus shows all possible files on HD.

What am I missing?

Any help appreciated. Thanks!

UPDATE:
I [have even added new boot option]("http://kbimg.dell.com/library/KB/DELL_ORGANIZATIONAL_GROUPS/DELL_GLOBAL/REC/FY2016/XPS13BIOS1.PNG") based on [this article]("https://wiki.debian.org/UEFI#Booting_a_UEFI_machine_normally") pointing to /EFI/ubuntu/gtubx64.efi and when selected, it does not boot.

---

### Post by oldfred on 2016-05-04
From live installer add Boot-Repair and run report.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by gnugu on 2016-05-04
Here is [Create Bootinfo summary]("http://paste.ubuntu.com/16222476/").

---

### Post by RobGoss on 2016-05-04
Are you wanting to just replace **Windows 10** with **Ubuntu**? if so it's really a easy method just use the whole disk and choose to wipe the entire disk and install Ubuntu.16.04

---

### Post by gnugu on 2016-05-04
RobGoss, yes, that's what I did. Doesn't boot.

---

### Post by RobGoss on 2016-05-04
How did you install Ubuntu USB or DVD?

And did you change anything in your BIOS in order to install Ubuntu?

If you're trying to install Ubuntu as the only OS you should not have to change anything in your BIOS as long as you can boot from that USB drive and follow the instructions for the installation that Ubuntu has provided. If i'm on Windows I always use [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for my installations

---

### Post by gnugu on 2016-05-04
Ok, after reading [this]("https://wiki.debian.org/UEFI#UEFI_Secure_Boot"), I have disabled Secure Boot and it does boot.

I think [I remember reading somewhere that 16.04LTS does support Secure Boot]("https://wiki.ubuntu.com/SecurityTeam/SecureBoot#Introduction").

---

### Post by RobGoss on 2016-05-04
So are you able to boot up Ubuntu?

---

### Post by gnugu on 2016-05-04
Yes, RobGoss, I can now boot it up. Will do updates, and proprietary updates and try to turn [secure boot on and test]("https://wiki.ubuntu.com/SecurityTeam/SecureBoot#Introduction"). Right now secure boot is off and and all the other settings are as per this thread, and it works.

---

### Post by RobGoss on 2016-05-04
Thanks GREAT welcome to Ubuntu my friend I hope you enjoy one of the best Linux desktops out today....

---

### Post by gnugu on 2016-05-04
Uh, I've been using Ubuntu for years now :). This is the first time Secure Boot bit me. Thanks!

---

### Post by gnugu on 2016-05-04
I'm back to confirm, that even after all updates, and third party sw updates, [this must be disabled]("http://kbimg.dell.com/library/KB/DELL_ORGANIZATIONAL_GROUPS/DELL_GLOBAL/REC/FY2016/XPS13BIOS3.PNG") for system to boot.

---

### Post by RobGoss on 2016-05-04
> **gnugu said:**
> I'm back to confirm, that even after all updates, and third party sw updates, [this must be disabled]("http://kbimg.dell.com/library/KB/DELL_ORGANIZATIONAL_GROUPS/DELL_GLOBAL/REC/FY2016/XPS13BIOS3.PNG") for system to boot.

You're referring to** Secure boot **correct? I believe I've read that this is one of requirements following installation

---

### Post by gnugu on 2016-05-04
Yes, Secure Boot must be disabled. [Last sentence in IMPORTANT paragraph here]("https://wiki.ubuntu.com/SecurityTeam/SecureBoot#Introduction") threw me off.

Thanks for your help.

---

### Post by RobGoss on 2016-05-04
Your very welcome glad you got it all sorted out

---


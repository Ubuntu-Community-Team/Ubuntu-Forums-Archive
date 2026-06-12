---
title: "Stuck just before the partitioning part"
date: 2022-02-21
forum: Installation &amp; Upgrades
---

### Post by noack9 on 2022-02-21
Hello.
For a week, I am trying to install Ubuntu 21.10, but it gets stuck at the part that you choose if its going to be a minimal install, if it is going to install the codecs and if you want to install updates (I guess it is called the other software part). I know it has been asked by some people some time ago, but in my case it just doesn't work. I can't unmount the drive at Gparted and KDE partition manager in case of Kubuntu (its greyed out), tried every possible combination of UEFI and BIOS mode and tried the latest LTS version with no success.

I tried installing Kubuntu, Xubuntu and Ubuntu MATE too, without success. And I doubt it is a problem with my computer, considering it already had debian-based distros and some other distros installed before.

My computer is a Dell Inspiron 5547 with 8gb of RAM and a i5-4210U CPU. And yes, I am trying to dual boot with Windows 10.

Thanks in advance.

---

### Post by ubfan1 on 2022-02-21
Windows on a 2014+ machine is in UEFI mode, so forget about the legacy option, you want Ubuntu in the same mode.  UEFI/Win implies a GPT partitioned disk, so no practical limit on the number of partitions you may make.  Did you shrink the Windows partition (from within Windows) successfully?  I'd skip any downloads offered until the install succeeds.  Fast Boot from the Windows power options needs to be off too.

---

### Post by noack9 on 2022-02-22
> **ubfan1 said:**
> Windows on a 2014+ machine is in UEFI mode, so  forget about the legacy option, you want Ubuntu in the same mode.   UEFI/Win implies a GPT partitioned disk, so no practical limit on the  number of partitions you may make.  Did you shrink the Windows partition  (from within Windows) successfully?  I'd skip any downloads offered  until the install succeeds.  Fast Boot from the Windows power options  needs to be off too.


Yeah. I have a 180 gb free for ubuntu and hibernation and fast boot is off. It just blinks 'preparing ubuntu drivers' and then gets stuck there, I can't create the ext4 partition for ubuntu. From what I read, it is something with the 100mb fat32 efi boot partition (that is supposed to have to folder inside the efi folder, Windows and ubuntu one after the install) and for some reason, the installer doesn't like it (that's why it gets stuck just before the partiton phase, I guess).

---

### Post by oldfred on 2022-02-22
Windows fast start up is a Windows setting & that also must be off. It can lock all Windows partitions.
A few systems also have UEFI settings to prevent modification of the ESP - efi system partition. Check UEFI.
Similar to this in Lenovo:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

---

### Post by noack9 on 2022-02-22
> **oldfred said:**
> Windows fast start up is a Windows setting &  that also must be off. It can lock all Windows partitions.
A few systems also have UEFI settings to prevent modification of the ESP - efi system partition. Check UEFI.
Similar to this in Lenovo:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.


Yeah man, I did what the the thread said. Everything is in GPT, windows fast boot and hibernation are off, I am trying to install it in UEFI mode and the computer is in UEFI mode only and Secure Boot is off. Its really strange this happening, considering that I already installed Debian, Manjaro and Linux Mint in dual boot with windows without any problems, and Ubuntu is the only one with this problem, (I like testing around with distros). Of course, cleaning the efi partition right after the uninstall to prevent problems.

---

### Post by MAFoElffen on 2022-02-24
According to the Dell Inspiron Communtiy:

> BIOS Dell: 00.03.08 (UEFI) The 5547 has a lot of "issues"[https://certification.ubuntu.com/hardware/201401-14542/](https://certification.ubuntu.com/hardware/201401-14542/) Certification notes

Updates required

This  system requires all available updates to be applied in order to work  properly.  Proprietary Drivers Required.  Installation of proprietary  AMD video driver is required for full functionality.  Touchpad gestures  From 2-finger touchpad gestures, only scrolling and tapping work on this  system. Legacy Boot Mode Required  This system was certified using  Legacy Boot Mode for certification. The use of EFI or "Auto" boot modes  may or may not work properly. Slow Resume from Suspend.  This system  does not not meet canonical performance criteria for resuming from  suspend, but suspend/resume is functional and other functionality is not  affected. BIOS   Dell: X18 (UEFI)


---

### Post by noack9 on 2022-02-24
> **MAFoElffen said:**
> According to the Dell Inspiron Communtiy:

Yeah. I have upgraded my uefi bios to the last version available a long time ago and I did try to install the system in legacy mode, without sucess. And I mean, this computer is 7 years old(the Dell post is from 2014,the laptop was pretty new at that time), I guess it should be working fine now, considering that other debian-based distros work fine and Debian too works fine.

---


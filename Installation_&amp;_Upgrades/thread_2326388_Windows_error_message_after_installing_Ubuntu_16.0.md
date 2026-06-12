---
title: "Windows error message after installing Ubuntu 16.04"
date: 2016-05-31
forum: Installation &amp; Upgrades
---

### Post by sam-pownall on 2016-05-31
My current windows 10 operating system broke so I decided to change my operating system to ubuntu. 

I used a USB to install ubuntu on my SSD, choosing to delete everything on the SSD and install Ubuntu 16.04. Installation runs smoothly and after it has finished it asks me to restart the computer. 

However when I restart I receive a windows error message "Your PC/Device needs to be repaired" regarding a file WINDOWS/system32/winload.exe. Error code 0xc000000e. 

Can anyone help me find out why I am still receiving a windows error message after I have wiped my SSD to do do a clean install?

Thank you.

---

### Post by grahammechanical on 2016-05-31
I can give you a guess. The UEFI settings utility is still expecting Windows 10 to be installed on that machine. If Ubuntu is the only OS on the machine then we will not get a Ubuntu boot menu (Grub). It is my guess that the message is appearing as part of the checks that the motherboard does before loading an OS.

You do not say if Ubuntu is loading or not. You may have one of those UEFI settings utilities that has been coded by the OEM to specifically load a Windows boot loader by looking for a label such as "Windows." This is against the UEFI specification. I do not know if this is the situation and I am unclear on the precise steps to solve it.

Others will help. Especially, if you tell us the make & model of the computer.

Regards.

---

### Post by oldfred on 2016-05-31
> Especially, if you tell us the make & model of the computer.
+1

Can you in UEFI change boot order to make ubuntu entry first.

Or can you select one time key often f10 or f12, check manual to choose what to boot and choose ubuntu entry. You may have two Ubuntu entries one is shimx64.efi and the other grubx64.efi. Shim is for Secure boot but works for normal UEFI boot.

If Windows is totally gone, you will need to remove /EFI/Microsoft folder in ESP - efi system partition and UEFI entry in NVRAM. But some systems are hard coded to only boot that entry by description. If you have that we change description from ubuntu to Windows in UEFI and can still boot Ubuntu.

---

### Post by sam-pownall on 2016-05-31
Hi guys, thanks for your help.

It turns out when I installed windows originally. it put the bootloader on the wrong disk. No idea why but deleting that and reinstalling ubuntu fixed my problem.

---


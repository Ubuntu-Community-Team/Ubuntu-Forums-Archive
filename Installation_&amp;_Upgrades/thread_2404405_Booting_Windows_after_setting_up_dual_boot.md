---
title: "Booting Windows after setting up dual boot"
date: 2018-10-23
forum: Installation &amp; Upgrades
---

### Post by elrokas on 2018-10-23
Hello everyone,

Today I set up dual boot with Windows and Xubuntu. I followed the article here [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)
As the article said in the end by computer booted into Windows by default after I changed the legacy boot back to the UEFI one. So, I ran the command bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi as recommended. However, this did not solve the problem rather now the computer was stuck on 'PXE over IPv4' and not booting at all. Seeing that I changed back into legacy boot and now I can successfully boot into Xubuntu.

I would really like to be able to boot back into Windows. Any help would be greatly appreciated.

---

### Post by yancek on 2018-10-23
> Seeing that I changed back into legacy boot and now I can successfully boot into Xubuntu.


It is possible to install Linux in Legacy/CSM mode on a GPT disk but that won't work with windows as a GPT drive needs to be UEFI for windows.  It appears you have a Legacy install of Xubuntu and an EFI install of windows and the only way to change to boot from one OS to the other is through the BIOS.  When you were installing Xubuntu, was your windows drive with its partitions recognized?  To avoid this you should be able to disable Legacy in the BIOS when you already have a windows EFI install.  You can determine whether your Xubuntu installed system is Legacy or EFI by copying/pasting the below command into a terminal and hitting the enter key.

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

Can you boot Xubuntu and mount the efi partition and navigate through the directories to see if you have one names ubuntu?  If not, you need to either re-install EFI.  Ubuntu documentation on dual booting with windows EFI, read through at least the first part, General Principles.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by elrokas on 2018-10-24
The Windows partition was not recognized. The problem was that I downloaded a image for 32bit Ubuntu because I thought 64bit is AMD exclusive and I have an Intel processor.

I ran the code and got 'Legacy boot on HDD'. I should probably mention that I installed Ubuntu on my D disc and not C, where the Windows files are stored.

Finally, I did mount the efi partition and, unfortunately, Ubuntu was not there.

---

### Post by yancek on 2018-10-24
If you want an EFI install of both so that you have the option on boot from Grub to select either windows or Xubuntu, you need to re-install using the 64bit and do an EFI install of Xubuntu.  A Legacy Grub will not boot an EFI install of windows.  The fact that you are using Intel rather than AMD is irrelevant.

Not sure where you saw "D" disk, from your windows install?  You won't see any drive/partition with that nomenclature in Linux/Ubuntu.

The output from the command and the fact that there is no ubuntu directory on the EFI partition confirm you have a Legacy install.  I don't think there is any other option than to download the 64bit Xubuntu and re-install.  Before beginning the new install, you might disable Legacy/CSM in the BIOS.

---

### Post by oldfred on 2018-10-24
The 32 bit version is Legacy only. You need to reinstall using 64 bit version and if Windows is UEFI, then boot Ubuntu installer in UEFI boot mode.
Do not do anything in BIOS/CSM/Legacy boot mode.
And boot of flash drive will have two options UEFI or Legacy. You always want UEFI.

See also instructions in link in my signature.
Particularly:
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

       The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)
[https://askubuntu.com/questions/641112/confused-about-amd-intel](https://askubuntu.com/questions/641112/confused-about-amd-intel)

---

### Post by elrokas on 2018-10-25
Thanks for the advice!
I reinstalled the 64 bit version and everything now works perfectly.
It might be interesting that I first (before reinstalling Xubuntu) got windows to boot by inserting a USB with Windows which allowed me to run the following command in the command prompt:

bcdedit /*set* {*bootmgr*} path \EFI\Microsoft\Boot\bootmgfw.efi

---


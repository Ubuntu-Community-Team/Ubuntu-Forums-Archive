---
title: "Error after successful installation (UEFI)?"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by JaZZyCooL on 2013-07-02
hello guys,
    I successfully installed ubuntu alongside windows 8 and able to boot into ubuntu using UEFI mode, but not able to boot into windows 8, although it shows entry for it but when I press it. It shows me this error

```

error : Unknown command 'drivemap'
error : invalid file path

Press any key to continue .....

```

I tried installing grub2 but it still the main grub tends to remain the same 1.99, Although it asked where I want to install I selected on sda but after selecting it asked me continue without installation?. I guess I was not able to select the correct option inside the terminal. 

I was alsoo thinking of using boot-repair but the problem is I want to have the ubuntu grub as the master grub as I am also installing crunchbang for which ubuntu grub will identify and add the entry to the OS without any troubles. That is I want to have ubuntu grub as my master grub, so that I can boot into ubuntu, crunchbang and windows 8, in UEFI mode and not changning everytime I turn on my computer.

Your help is highly appreciated.

---

### Post by oldfred on 2013-07-02
Only a few Linux work with secure boot. So I do not know if crunchbang will work? Were you installing Ubuntu in UEFI mode or BIOS mode. In UEFI mode you install grub to efi partition, but in BIOS mode you install to the MBR. But if in BIOS mode you cannot easily dual boot Windows 8 as it only boots in UEFI mode and you have to go into BIOS and change each time you change operating systems.

Your other thread:
[http://ubuntuforums.org/showthread.php?t=2159278](http://ubuntuforums.org/showthread.php?t=2159278)

---

### Post by JaZZyCooL on 2013-07-02
No sir, I have installed ubuntu in UEFI mode. The only further solution I am looking for is to install crunchbang and boot all the OS with the same grub without changing the boot mode everytime.

---

### Post by oldfred on 2013-07-02
Do not know about crunchbang, does it say it will boot with UEFI and then does your Windows boot with secure boot off? Then it may work.

But only a few Linux have secure boot working and many Windows only boot with secure boot. 
 Under Windows 8 Secure Boot, all PCs, no matter what operating system they actually run, must include several Microsoft-owned keys. 
 The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

---


---
title: "Replacing Windows with Ubuntu on a new netbook"
date: 2017-02-26
forum: Installation &amp; Upgrades
---

### Post by aneblanc on 2017-02-26
Hello,

I just bought an HP Stream 11 with 32gb/4GB/Celeron 3060. I was told there is not really enough room for a dual boot. 
Is there a possibility to save windows 10 on a memory media before writing it over with Ubuntu 16.04. I would then have the possibility to revert the notebook to factory state in case of need.
Thank you.

---

### Post by RobGoss on 2017-02-26
Hello and welcome, The HP streams are very limited for disk space and won't do well as a dual boot unless you use maybe a micro SD card to install Ubuntu 

If you want to just install Ubuntu on that machine I would also recommend something lighter like **Lubuntu,** with the limited resources you have it might be the best option. Once you've created the live media just choose to use the entire **disk space** for your installation


I't been a while since I've used Windows and** ISO** files were not available at that time, nowadays you have the option to download a **ISO** file for your Windows operating system in case it's needed as long as you have a registered licensed copy you should be good to go

**Windows ISO download**
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)

---

### Post by oldfred on 2017-02-26
I think this is one of the 32 bit UEFI even though system is 64 bit. And is UEFI class 3 or no CSM/BIOS boot.

Linux did not have a 32 bit UEFI boot loader, so Microsoft and vendors thought they could make a Windows only system and lock uses in.
Then Linux did come out with a 32 bit UEFI, but had to separately compile it. Then some pre-compiled versions were made available, but standard distributions do not have that as a default.

 Linux on the HP Stream tablet
[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188) 

Older:

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=2189855"]http://ubuntuforums.org/showthread.php?t=2189855
[/URL]
 32-bit UEFI Support Proposed For Ubuntu Linux bootia32.efi
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE) 

[URL="http://ubuntuforums.org/showthread.php?t=2189855"]
[/URL]

---

### Post by aneblanc on 2017-02-26
> **oldfred said:**
> I think this is one of the 32 bit UEFI even though system is 64 bit. And is UEFI class 3 or no CSM/BIOS boot.

Linux did not have a 32 bit UEFI boot loader, so Microsoft and vendors thought they could make a Windows only system and lock uses in.
Then Linux did come out with a 32 bit UEFI, but had to separately compile it. Then some pre-compiled versions were made available, but standard distributions do not have that as a default.

 Linux on the HP Stream tablet
[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188) 

Older:

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=2189855"]http://ubuntuforums.org/showthread.php?t=2189855
[/URL]
 32-bit UEFI Support Proposed For Ubuntu Linux bootia32.efi
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE) 

[URL="http://ubuntuforums.org/showthread.php?t=2189855"]
[/URL]

Sorry, I really did not understand much of your answer. Could you tell me if you need additional information from me to give me an answer to my question? I just want to remove Windows 10 from my laptop and replace it with Ubuntu 16.04. I would like to keep Windows 10 on a memory in case I need to reinstall it later. I have been using Ubuntu on other machines for many years and I am very pleased with it. I am really not a specialist. Thank you

---

### Post by oldfred on 2017-02-26
I think the link has the details you want.

I have not installed a 32 bit UEFI version and that is a bit more complicated.

---

### Post by him610 on 2017-02-27
> save windows 10 on a memory media before writing it over

Have you considered purchasing a spare 32GB SSD for Linux to replace your current 32GB Win10 SSD?

---

### Post by aneblanc on 2017-02-27
> **him610 said:**
> Have you considered purchasing a spare 32GB SSD for Linux to replace your current 32GB Win10 SSD?

I don't know if it is possible to replace anything on this computer. I have read that everything is soldered on. I have bought a 64GB SDXC that seems to work.

---

### Post by aneblanc on 2017-02-27
I now have saved a copy of Windows 10 on an 8GB USB stick. I am about to create an 8GB USB stick to install Ubuntu 16.04 after formatting the eMMC drive. After OldFred's post I am a bit worried that it won't work. Wish me good luck! I let you know how it goes.

---


---
title: "Ubuntu 22.04 Dual-boot Win11 Asus ProArt ACHI Issues"
date: 2022-06-11
forum: Installation &amp; Upgrades
---

### Post by d-ayle-t on 2022-06-11
Hello,

I think my problem is specific to my ASUS bios on an Asus ProArt Studio with Windows 11 installed. I've followed the Ubuntu directions on changing RST to ACHI, but every time I try to reboot into Windows safe mode, it just returns me to the BIOS screen. I'm hesitant to install Ubuntu without knowing that I can boot into Windows and have it install ACHI drivers. Do I need to disable FastBoot as well? Has anyone successfully accomplished this dual boot setup with this laptop or similar?

Thanks,
-K

---

### Post by tea for one on 2022-06-11
Here is some info [https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

### Post by yancek on 2022-06-11
Why are you trying to into windows safe mode rather than the standard boot?  Does that not boot?

Why would you not be able to boot into windows after installing Ubuntu?  The big problem is users not installing in the same mode:  UEFI or Legacy.  If windows is installed in UEFI you should install Ubuntu UEFI.  Safest method is to disable the windows hard drive before installing.  If you are installing to the same hard drive that won't work.  Have you ever installed any Linux OS?  Have you read any tutorials on booting both windows and Ubuntu?  There are quite a few sites with tutorials.

 [https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)

---

### Post by isopticon on 2022-06-11
You are right with not installing Ubuntu on your machine, there is always a risk of breaking Windows for good. The safest option is to run Ubuntu on Windows under WSL.
Alternatively run Ubuntu Virtual Machine under Windows. This gives much better experience as you can switch between the systems in seconds.
Dual boot was and still is very risky.
Hope this helps

---

### Post by grahammechanical on 2022-06-11
> Do I need to disable FastBoot as well?

Yes, most definitely! Be aware that a Windows update will re-install fastboot. Windows creates the effect of a fast boot by not shutting down the machine but by putting it into hibernation. This will prevent Linux/Ubuntu from reading the Windows file system. The Linux boot loader (Grub) will not be able to load Windows.

P.S. I do not think this is correct:

> The safest option is to run Ubuntu on Windows under WSL.

Windows Subsystem for Linux is not designed to run a full distribution of Linux. Not even Ubuntu.

> WSL enables you to use Linux tools, like Bash or Grep, completely  integrated with Windows tools, like PowerShell or Visual Studio Code,  with no need to dual-boot.

[https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install)

> The Windows Subsystem for Linux lets developers run a GNU/Linux  environment -- including most command-line tools, utilities, and  applications -- directly on Windows, unmodified, without the overhead of  a traditional virtual machine or dualboot setup.

[https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)

Regards

---


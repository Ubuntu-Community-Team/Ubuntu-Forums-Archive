---
title: "Installing Filmora with Wine 9.0 on Ubuntu 22.04"
date: 2024-11-25
forum: Installation &amp; Upgrades
---

### Post by agonzalesc on 2024-11-25
Hi.

Has anyone been able to install Filmora on their Ubuntu using Wine? I tried with Filmora 14, 13, and 12; and it does install fine, but when starting the program it freezes with many errors in the console.


Only Filmora 11 gave me an error during installation, that it couldn't find the system32/ie4uinit.exe which I understand belongs to Internet Explorer, but it won't let me install that browser in 64bits, I already tried with winetricks using **WINEARCH=win32** but it tells me that all my wine installations are 64bits and it can't install it.

[IMG]https://blog.letsgodev.com/wp-content/uploads/2024/11/ieuni.png[/IMG]

```
gonzalesc@pucco-hp:~$ winetricks ie8
Executing mkdir -p /home/gonzalesc
------------------------------------------------------
warning: You are using a 64-bit WINEPREFIX. Note that many verbs only install 32-bit versions of packages. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Using winetricks 20210206 - sha256sum: 0f21da98811e0bfda16a7d6d6b8e860a9cedbd4e836c7dd9b02f068d3092ee2e with wine-9.0 and WINEARCH=win64
Executing w_do_call ie8
Executing mkdir -p /home/gonzalesc
------------------------------------------------------
warning: You are using a 64-bit WINEPREFIX. Note that many verbs only install 32-bit versions of packages. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Executing load_ie8 
------------------------------------------------------
warning: This package (ie8) does not work on a 64-bit installation. You must use a prefix made with WINEARCH=win32.
------------------------------------------------------

```
I managed to install Filmora 9 about 8 months ago I remember and everything worked fine, but now I can't find that version on the internet.

Thanks

---

### Post by 1fallen on 2024-11-25
My friend the only link I could find was this: [https://drive.usercontent.google.com/download?id=1KOxIRVL0U7HnqXwzfCHlv2DrFgukE4NN&export=download](https://drive.usercontent.google.com/download?id=1KOxIRVL0U7HnqXwzfCHlv2DrFgukE4NN&export=download)
Please check it your self though.

Here is the scan report: [https://www.virustotal.com/gui/file/f52e6ea61cb64c56cb059a6584dc5e5fcbbe02c898cc658870efe6c78a3976c9](https://www.virustotal.com/gui/file/f52e6ea61cb64c56cb059a6584dc5e5fcbbe02c898cc658870efe6c78a3976c9)

It scanned fine for virus and malware, They are pushing hard for 14 with AI

---

### Post by agonzalesc on 2024-11-25
Uh. Te same error..

[IMG]https://blog.letsgodev.com/wp-content/uploads/2024/11/error2.png[/IMG]

Regards

---

### Post by 1fallen on 2024-11-25
This was the version you wanted, if it still don't work I have no clues for you, you already said earlier that it ran fine on 22.04 Jammy.

Either use it in Windows, or use something native to Linux, or install Windows in a VM and use it there.

Sorry there is nothing for me to suggest that hasn't been already suggested in your other Threads

I know it won't run in a Wayland Session.

---

### Post by 1fallen on 2024-11-26
BTW It works fine in my KVM Windows 10, and Filmora 14

---

### Post by agonzalesc on 2024-11-26
Hi.
What KVM are you using? Virtualhost?

Thanks

---

### Post by 1fallen on 2024-11-26
> **agonzalesc said:**
> Hi.
What KVM are you using? Virtualhost?

Thanks

No I have not used VirtualBox in many many years now. (If I understood you corerectly)

More info found here: [https://www.packetcoders.io/what-is-the-difference-between-qemu-and-kvm/](https://www.packetcoders.io/what-is-the-difference-between-qemu-and-kvm/)

This is an older quote, but still relevant today.

KVM is a Linux kernel module. It is a type 1 hypervisor that is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V)[1]. But what is full virtualization, you may ask? When a CPU is emulated (vCPU) by the hypervisor, the hypervisor has to translate the instructions meant for the vCPU to the physical CPU. As you can imagine this has a massive performance impact. To overcome this, modern processors support virtualization extensions, such as Intel VT-x and AMD-V. These technologies provide the ability for a slice of the physical CPU to be directly mapped to the vCPU. Therefore the instructions meant for the vCPU can be directly executed on the physical CPU slice.[2]

It is a great tool for testing, and so much more. A KVM switch saves hardware costs, save your space and make multi-device integration easier. You can easily switch among different devices.

[SUP][URL="https://www.packetcoders.io/what-is-the-difference-between-qemu-and-kvm/#fn2"]


[/URL][/SUP]

---

### Post by ActionParsnip on 2024-11-26
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=20071](https://appdb.winehq.org/objectManager.php?sClass=application&iId=20071)
or
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=17761](https://appdb.winehq.org/objectManager.php?sClass=application&iId=17761)

It doesn't work in WINE

---

### Post by agonzalesc on 2024-11-26
Hi,
I was able to install it using KVM/QEMU.

Thanks for the help!

---

### Post by 1fallen on 2024-11-26
Nice.

---


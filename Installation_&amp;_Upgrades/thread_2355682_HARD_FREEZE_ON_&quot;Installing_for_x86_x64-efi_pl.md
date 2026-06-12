---
title: "HARD FREEZE ON &quot;Installing for x86_x64-efi platform.&quot;"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by melogenesis on 2017-03-15
Hello guys :)

I have any linux distro installing problem.

When i tried to install ubuntu, ubuntu mate, kubuntu and manjaro linux (I've tried both 32 and 64bit versions), i am having hard freeze problem and i cant do anything except restart.

My laptop is Acer N3350 &#304;ntel processor, 4GB Ram, 500gb hardisk
I think the problem is about BIOS.
I tried many things like EFI, Secure boot...
My bios version is 1.08

Can anyone help me please?
I just want to install any linux distro especially ubuntu :).

---

### Post by ajgreeny on 2017-03-15
I believe Acer machines require a password or "Trusted" boot file of some sort.
See [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
and in that the section saying
> Systems that only boot Windows from UEFI.
Per UEFI standard you should be able to boot any entry in UEFI boot menu. But some vendors have modified UEFI code to only boot the Windows efi file. The UEFI looks for the Windows file name and only boots it. (Note for Acer, it requires "trust" settings in UEFI)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI with the 64bit version with secure boot on. A few systems will only boot with UEFI and secure boot on or with CSM (BIOS) if secure boot is off. Best to test system to see which modes it boots in. In secure boot mode it will only show/allow systems that have secure boot. You may have to change UEFI settings or set password to allow other devices to boot.
I have no personal experience of any of this in my machines which all dealt with UEFI without a problem.

---

### Post by melogenesis on 2017-03-15
[COLOR=#DD4814][FONT=Ubuntubeta][COLOR=#C61919][ajgreeny]("https://ubuntuforums.org/member.php?u=27747")[/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]  Thank you so much for quick reply :)

i actually had an another acer netbook one year ago but i had no problems with it.
anyway,

[/FONT][/COLOR]i am going to have a look at that. I really love this forum.
i will send a message you after researching again ty so much.
[COLOR=#000000][COLOR=#DD4814]
[/COLOR][/COLOR][COLOR=#000000][COLOR=#DD4814]
[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG][COLOR=#C61919][ajgreeny]("https://ubuntuforums.org/member.php?u=27747")[/COLOR][/COLOR] [/COLOR]

---

### Post by melogenesis on 2017-03-15
so what should i do firstly?

or where should i start from :)

as far as im concerned i can access my bios and SECURE BOOT is off at that moment , i can run any linux from USB and run like a live disk, but when i want to install im facing with this problem :(

---

### Post by ajgreeny on 2017-03-15
See if this thread helps.
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)

---


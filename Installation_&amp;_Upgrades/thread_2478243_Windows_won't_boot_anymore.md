---
title: "Windows won't boot anymore"
date: 2022-08-20
forum: Installation &amp; Upgrades
---

### Post by eRCaGuy on 2022-08-20
My Linux partition is LUKS-encrypted. My dual-boot Windows /dev/sda2 partition is Veracrypt-encrypted. 

I can't log into Windows anymore. It brings up a blue screen that gives me some selection options and if I choose "Continue to Windows 8" or whatever it restarts back to the grub boot menu again, in an endless circle. 

Here is my pastebin output of `boot-repair` after following [these instructions]([https://help.ubuntu.com/community/Boot-Repair):](https://help.ubuntu.com/community/Boot-Repair):)

[https://pastebin.ubuntu.com/p/N3H2BXSmgg/](https://pastebin.ubuntu.com/p/N3H2BXSmgg/)

Should I run the recommended boot-repair fixes?

---

### Post by TheFu on 2022-08-21
> **eRCaGuy said:**
>  Should I run the recommended boot-repair fixes?

NEVER!

I'm a little surprised that you setup 2 different encryption methods in a dual boot situation.  If it were me, I'd run 1 OS with that encryption on the hardware and run the other OS inside a virtual machine.  Mixing MS-Windows and any other OS is asking for boot troubles, since MSFT commonly thinks they are the only OS on a computer and breaks booting with their software updates from time to time.

---

### Post by tea for one on 2022-08-21
As you have already booted into Ubuntu, I doubt that boot-repair will fix a Windows boot problem.
Generally, you need Windows tools to fix Windows problems.

Having said that, I notice that you have also installed rEFInd.
Do you use Grub or rEFInd to boot?
Can you drop into an EFI shell and locate the Windows boot instruction - /efi/Microsoft/Boot/bootmgfw.efi

Before attempting any repair, please ensure that you have backups of your personal data from both Ubuntu and Windows.

---


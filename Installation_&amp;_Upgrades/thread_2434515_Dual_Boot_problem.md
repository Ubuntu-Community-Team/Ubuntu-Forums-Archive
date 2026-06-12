---
title: "Dual Boot problem"
date: 2020-01-07
forum: Installation &amp; Upgrades
---

### Post by alvinrr on 2020-01-07
I installed for dual boot Ubuntu 18.04 on my Windows 10 PC. and when my PC needs to restart, it booted straight to Windows 10 and did not show the grub menu.
Now I typed this in command prompt "bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi" and restarted the PC. The problem is it is now boots straight to Ubuntu without the grub, and when I used grub customizer, it doesn't show the windows boot manager.

In the boot manager in UEFI, when I click windows, it boots to Ubuntu.

sorry for my English..
Please help.

---

### Post by slickymaster on 2020-01-07
*Thread moved to **Installation & Upgrades**.*

---

### Post by CelticWarrior on 2020-01-07
Do not complicate things (yet) with additional software and doing things you don't know. Typically doing that makes things worse.

Just boot Ubuntu again, run ```
sudo update-grub
``` and reboot. What happens now?

---

### Post by alvinrr on 2020-01-07
same thing happened, I have the grub now, but it shows no windows OS.

it only shows

Ubuntu
additional ubuntu ...
mem test ...
mem test ,......

---

### Post by CelticWarrior on 2020-01-07
That means you have Windows and Ubuntu installed in different modes -or- Windows is semi-hibernated due to Fast Startup...

Now... Please open UEFI settings and check if you can select "Windows bootloader..." instead of "Ubuntu" (in the Boot menu). If you can then it should boot Windows directly. If so, disable Fast Startup. Shutdown. Boot again and change the boot order back to "Ubuntu" and if necessary repeat the command in the previous post.

---

### Post by alvinrr on 2020-01-07
I already disabled fast startup when I installed Ubuntu. 
about selecting  windows boot loader, when I clicked windiws, it boots to Ubuntu.

Just booted up, and nothing happens.

---

### Post by CelticWarrior on 2020-01-07
Fast Startup is a Windows feature, do not confuse it with Fast Boot, a firmware (UEFI) setting...

So, right now, you need to repair Windows because, apparently, the command you tried first screwed the Windows bootloader (that's what happens when we mess with things we don't understand). 

Please boot the Windows installation media of the same Windows version and follow instructions for repairing. Once your Windows is booting directly again, all you need to do is change the boot order back to Ubuntu and run the command.

---

### Post by Impavidus on 2020-01-07
> **alvinrr said:**
> I already disabled fast startup when I installed Ubuntu.
That doesn't mean a lot. Windows can automatically turn it back on during updates and doesn't inform the user about it.

---


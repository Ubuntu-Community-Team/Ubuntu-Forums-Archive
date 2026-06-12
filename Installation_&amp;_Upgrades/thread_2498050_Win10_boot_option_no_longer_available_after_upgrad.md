---
title: "Win10 boot option no longer available after upgrade to 22.04"
date: 2024-05-28
forum: Installation &amp; Upgrades
---

### Post by infleqtioncameronmorris on 2024-05-28
Hello,

Any guidance or advice would be greatly appreciated.

I have been running a dual boot Win10 / Ubuntu 20.04 for a number of months with no issues. Until recently I would have a grub boot menu defaulting to Ubuntu 20.04, but could choose a Win10 partition and it worked fine with no issues.

Recently I upgraded to Ubuntu 22.04 and since then, no grub menu is displayed on boot - we just boot directly into Ubuntu 22.04.

I've tried a few things advised on forum posts to others in a similar situation...

```
sudo os-prober
```
This returns nothing

I can see the Win10 drive, all the files are still present and look healthy.

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy


```

The summary of Boot-Repair is also attached to this post. nvme0n1p3 is indeed the partition I would like to restore!

Many thanks
Cameron

---

### Post by tea for one on 2024-05-28
os-prober is used in your grub file.
Assuming that your Windows 10 is working OK and neither hibernating nor encrypted
Boot into Ubuntu and open a terminal
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]# Originally hidden[/COLOR]
GRUB_TIMEOUT=10 [COLOR="#0000FF"]# Originally 0[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"]# Add this line[/COLOR]
```
```
sudo update-grub
```
Did Grub find the Windows Boot Manager?

Edit: I've just noticed that boot-repair states LegacyWindows detected (line 288)
However, you have EFI\Microsoft\Boot\bootmgfw.efi (line 101)

I'm not sure if editing Grub will be the solution, but, worth a shot

---

### Post by oldfred on 2024-05-28
Your ESP has no /EFI/Microsoft folder in your ESP nvme0n1p1?
That is what grub uses to find Windows boot.
And you have UEFI boot entry that refers to booting from ESP but it would also need that Windows folder.

Normally suggest booting Windows directly from UEFI, but without folder in ESP that will not work.
You need a Windows repair flash drive or recovery drive and run Windows repair commands to recreate the boot entry in the ESP. Be sure to do repairs in UEFI boot mode.

---

### Post by tea for one on 2024-05-28
> **oldfred said:**
> Your ESP has no /EFI/Microsoft folder in your ESP nvme0n1p1?
Yes, good spot, oldfred - I completely missed it.

I can't quite believe that the Microsoft folder in the ESP was removed by the Ubuntu installation process?

---

### Post by jeremy31 on 2024-05-28
You may be able to create the \EFI\Microsoft\Boot\ directory and copy the files from nvme0n1p3 \Windows\Boot\EFI and it might work.  Otherwise the repair will have to be done from a Windows Recovery disk or Windows 10 ISO

---

### Post by csae2608 on 2024-05-28
> **tea for one said:**
> os-prober is used in your grub file.
Assuming that your Windows 10 is working OK and neither hibernating nor encrypted
Boot into Ubuntu and open a terminal
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu [COLOR=#0000FF]# Originally hidden[/COLOR]
GRUB_TIMEOUT=10 [COLOR=#0000FF]# Originally 0[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR=#0000FF]# Add this line[/COLOR]
```
```
sudo update-grub
```
Did Grub find the Windows Boot Manager?

Edit: I've just noticed that boot-repair states LegacyWindows detected (line 288)
However, you have EFI\Microsoft\Boot\bootmgfw.efi (line 101)

I'm not sure if editing Grub will be the solution, but, worth a shot


thank you, this has been very helpful;

on my older computer , 24.04 would out of the gate not allow the grub menu to come after the installer has correctly suggested to install 24.04 alongside Windows 7 on the free partition of the SSD.
by changing these parameter you suggested, the windows entry and grub menu became visible on restart/boot.

---

### Post by infleqtioncameronmorris on 2024-05-29
Thank you everyone for the replies, I have managed to restore the dual boot.

1 - With a Win10 deployment (Win10_22H2_EnglishInternational_x64v1.iso) USB, go in the command line and follow "Repair EFI Bootloader in Windows 10" of [https://www.dell.com/support/kbdoc/en-uk/000124331/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc#instructions](https://www.dell.com/support/kbdoc/en-uk/000124331/how-to-repair-the-efi-bootloader-on-a-gpt-hdd-for-windows-7-8-8-1-and-10-on-your-dell-pc#instructions)

n.b. the instructions in my case jump to "Rebuild the BCD store in Windows 11 and Windows 10 (Version 1709 and newer):" without running the [bootrec /FixBoot] command

2 - This became the default boot option, so reverted the BIOS config to boot into "ubuntu" (or grub, etc)

3 - Now [sudo os-prober] found the install, and [sudo update-grub] rebuilds grub so no need to toggle boot options in BIOS.

I'm none the wiser as to why 20.04 -> 22.04 process would have caused this. Many thanks for all your comments which lead me to a successful outcome.

---


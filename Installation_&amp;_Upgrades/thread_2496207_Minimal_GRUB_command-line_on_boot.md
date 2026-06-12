---
title: "Minimal GRUB command-line on boot"
date: 2024-03-18
forum: Installation &amp; Upgrades
---

### Post by defaultcitizen on 2024-03-18
Hello,

Whenever I do a cold boot it seems there is a moment where I receive a command-line interface for GRUB. Then I type "exit" to proceed with the boot where GRUB shows the selection list properly. 
This began after I needed to disable SecureBoot temporarily. Is there something else I needed to do before enabling SecureBoot?
Do I have two GRUBs installed somehow?

This is a dual boot installation with Windows 11 and Kubuntu 23.10.

I've run boot repair twice now and it hasn't changed this behaviour. In either case, boot repair tried these options:

> [COLOR=#111111][FONT=monospace]The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of[/FONT][/COLOR]sda2,
using the following options:  nvme0n1p2/boot/efi [COLOR=#111111][FONT=monospace]Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups[/FONT][/COLOR]

sda2 being where Kubuntu is installed and nvme0n1p2 is where Windows 11 created the EFI partition.

[https://paste.ubuntu.com/p/VPW5p3pDQq/](https://paste.ubuntu.com/p/VPW5p3pDQq/)

---

### Post by oldfred on 2024-03-18
You show UEFI Secure boot on.
But have some old BIOS boot loaders in MBRs.
Windows in nvme0n1 and sdc, grub in sda. Those will never work and really never should have been installed there.
As long as you do not attempt to boot in old BIOS mode, having boot code in MBR is ok as never used with UEFI boot.

Not sure if you have Ubuntu installed in UEFI Secure boot mode. It may be trying to boot and then switching?
The reinstall of signed grub should have worked, but you may have need to reinstall signed kernel in advanced mode of Boot-Repair?

Make sure UEFI is set to boot in UEFI mode, but with Secure boot on that should be only option.

Report did not show output of efibootmgr which it normally does.

Post this in code tags.
sudo efibootmgr -v

---

### Post by defaultcitizen on 2024-03-18
SecureBoot was enabled when I installed Kubuntu and Windows months ago and GRUB was seemingly fine. However recently I needed to run memtest86+ and I did a BIOS update.
Also, this ASUS UEFI lets me choose between [Windows UEFI Mode] and [Other OS]. I set it to [Other OS] while I was using memtest86+ only.

I'm not exactly sure what resides in sdc but it may be related to the Microsoft Store or Xbox Games service. Windows might have created this automatically.

Here is the output of that command:

```
[FONT=monospace][COLOR=#000000]BootCurrent: 0005[/COLOR]
Timeout: 1 seconds
BootOrder: 0005,0000
Boot0000* Windows Boot Manager  HD(2,GPT,6465f541-ec1d-44fe-a22a-2c5224f26603,0x60700000,0x32000)/File(\EFI\MI
CROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.
c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...s................
Boot0005* ubuntu        HD(2,GPT,6465f541-ec1d-44fe-a22a-2c5224f26603,0x60700000,0x32000)/File(\EFI\UBUNTU\SHI
MX64.EFI)[/FONT]
```

Should I try running the reinstall of the signed kernel in advanced mode of Boot-Repair?

Thanks for your assistance.

---

### Post by oldfred on 2024-03-19
If it worked before & you installed in UEFI mode with Secure Boot on, it should be correct.

UEFI entries look normal.

The change to "Other OS" was probably the issue.
BIOS boot only works with Secure boot off.

My old motherboard said to use "OtherOS" to boot Windows 7 In UEFI mode, as it does not support UEFI Secure boot.
With the OtherOS setting you can install in UEFI (Secure boot off) or old BIOS boot mode.

---

### Post by defaultcitizen on 2024-03-20
Where do I select in Boot-Repair to reinstall signed kernel in advanced mode?

Does this mean because I had the UEFI set to [Other OS] temporarily for a few boots, that should I reinstall my Kubuntu?

---

### Post by oldfred on 2024-03-20
Changing to OtherOS should not have made any difference unless you totally reinstalled system.

Boot-Repair has advanced options where you can choose what to do.
tps://help.ubuntu.com/community/Boot-Repair & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by defaultcitizen on 2024-03-21
Is this option on the "GRUB options" tab in Boot Repair? Is it "Purge kernels then reinstall last kernel"?

---

### Post by oldfred on 2024-03-21
Yes, but also check complete reinstall of grub.
And before any major change, make sure your backup is current.

---

### Post by defaultcitizen on 2024-03-21
First, I think I should clarify I've been using Boot Repair while running the currently installed Kubuntu, not from a Live USB.

When I ran Boot Repair with the purge kernels and purge GRUB (assuming that's what you meant by complete reinstall), it ran through the GRUB section seemingly without issues but became inactive when purging the kernels.
I assumed I should try again but in Live. Here's what that produced:

> Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 23.10 entry (nvme0n1p2/efi/ubuntu/shimx64.efi file) !
Please disable SecureBoot in the BIOS. Then try again.


[https://paste.ubuntu.com/p/jBrgWFTJ3J/](https://paste.ubuntu.com/p/jBrgWFTJ3J/)

---

### Post by oldfred on 2024-03-21
We have seen more & more locked NVRAM issues. And not one easy solution.
were you running from UEFI boot?
Do you have latest UEFI firmware from vendor?

You may need to manually mount /sys/firmware/efi/efivars which I do not think Boot-Repair does.
It seems that older systems had efivars in with kernel, but newer have it in /sys/firmware.
UEFI settings or include in chroot mount -t efivarfs none /sys/firmware/efi/efivars
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)


But many systems have a setting in UEFI to prevent unauthorized updates.
Dell Locked BIOS
[https://ubuntuforums.org/showthread.php?t=2489447](https://ubuntuforums.org/showthread.php?t=2489447)
HP Zbook 15 NVRAM locked, install issues multiple settings
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
MSI locked the boot order in the BIOS.
In the MSI UEFI BIOS Setting, Toggle from Advanced Mode to Basic Mode. Bottom of list                   
 MSI B450M Pro-Vdh Max Unable to install Ubuntu (Black Screen)  UEFI update required
[https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556](https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556)
add "--no-nvram" to the "grub-install" command 
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)

---

### Post by defaultcitizen on 2024-03-23
Yes, I have the latest UEFI from ASUS. I upgraded it recently for RAM testing purposes, default settings were loaded and the problem began.

I've checked the motherboard UEFI manual and there isn't any password settings that I've use or are on by default. My board is the ASUS PRIME Z690-P D4.

Secure Boot does have these options:

> Secure Boot Mode
This option allows you to select the Secure Boot mode from between Standard or
Custom. In Custom mode, Secure Boot Policy variables can be configured by a
physically present user without full authentication.
Configuration options: [Standard] [Custom]


In this case, it's set to Custom. This enables some key management section that I've left untouched.

I'll try using the --no-nvram option for grub-install, from the Live USB.

---

### Post by defaultcitizen on 2024-03-23
I ran this command while running the Live USB ```
ls /sys/firmware/efi/efivars
``` 
and it generated lots of output. So that means the USB is running in UEFI mode?

However, I'm not sure to proceed.

```
[FONT=monospace]
[/FONT][FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo su - [/COLOR]
root@kubuntu:~# modprobe efivars 
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-9-generic
[/FONT][FONT=monospace][COLOR=#000000]root@kubuntu:~# mount -t efivarfs none /sys/firmware/efi/efivars [/COLOR]
mount: /sys/firmware/efi/efivars: none already mounted or mount point busy. 
       dmesg(1) may have more information after failed mount system call.[/FONT]

```

---

### Post by oldfred on 2024-03-23
The efivars is mounted in mount command, so one of default mounts. 
```
[FONT=monospace][COLOR=#000000]efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000][/COLOR][/FONT]
[FONT=monospace][COLOR=#000000] 
[/COLOR][/FONT]I also get error on modprobe in Kubuntu 22.04. Not sure if in past it was in kernel &  either Boot-Repair or grub use that to confirm UEFI vs old BIOS?[FONT=monospace]

[/FONT]

---

### Post by defaultcitizen on 2024-03-26
I'm still not sure how to proceed with this manually.

```
[FONT=monospace][COLOR=#000000]sudo mount -t efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,n[/COLOR]
oexec,relatime)
bash: syntax error near unexpected token `('

[/FONT][FONT=monospace][COLOR=#000000]sudo mount -t efivarfs on /sys/firmware/efi/efivars type efivarfs[/COLOR]
mount: bad usage
Try 'mount --help' for more information.
[/FONT]
```

At this point I'm considering a temporary workaround.
I think I will set Windows 11 to be first the boot order to bypass GRUB and use the boot menu (pressing F8) on reboot to gain access to Kubuntu.
I've done something similar in the past, so I assume it's fine for now, especially with my light usage compared to Windows.

---


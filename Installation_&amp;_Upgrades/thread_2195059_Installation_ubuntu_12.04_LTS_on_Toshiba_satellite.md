---
title: "Installation ubuntu 12.04 LTS on Toshiba satellite L50-A /Windows 8.1"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by sgxnew54 on 2013-12-22
Hi folks,
I have installed ubuntu 12.04 LTS 64 bit on my pc with windows 8.1. I created two partitions root "/"  and Swap the installation has ben appareantly correct. when restarted the PC GRUB didn't loaded and PC started with Windows.
So I imagined the problem depended on UEFI and, having seen Ubuntu UEFI documentation, i have done the following 2 things : <**secureboot disabled> and <boot speed normal **(can be normal or fast)>, but  instead I  haven't found on my boot  **<Intel Smart Response Tech>, and <QuickBoot/FastBoot**>.

After that I restarted the PC but the grub didn't loaded, it goes with Windows always, also when I put on BIOS, BOOT first from CD/DVD . 
I tried to restart the PC using utility windows "use a device to start", I selected "EFI DVD/CD" and  inserted the CD-LIVE or USB-LIVE  and I have on screen the first map of Ubuntu (3 choices) , tried to select installer or use ubutnu but the next screen is always black, ubuntu doesn't start from CD/USB-LIVE.

At the end,  from windows I deleted the 2 partitions created before,  "/ "  and "Swap" , and repeated the above procedure to start from CD-LIVE, wihtout success: as above I have the first screen of ubuntu (3 choises) and after selecting anything from menu I have the same black screen, ubuntu doesn't start.

I don't understand why only the first time the CD-LIVE worked,that is very very very  strange !!!!

Please, have any idea and can you help me  ??

Thanks in advance.

Sandro

---

### Post by Bucky Ball on 2013-12-22
Yes, that is strange. This is a suggestion and no guarantees. When you boot and get to 'Try Ubuntu' 'Install Ubuntu', press F6 and you should get some pop-up options. Choose 'nomodset'. Proceed with 'Try Ubuntu'. How did it go? Any different?

---

### Post by oldfred on 2013-12-22
If it is preinstalled Windows 8, then it is UEFI and you get grub menu when booting installer in UEFI mode. Then you can only add boot parameters by manually editing grub boot stanza. You use e on menu for edit, scroll to linux line and replace quiet splash with nomodeset.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sgxnew54 on 2013-12-22
HI, I pressed F6 but I had the same result black screen using CD-LIVE or USB-LIVE, so I **_cannot install ubuntu anymore _**on my pc,  whi is this ??

do you have some idea  so I can  bypass this problem   ??


thanks again

---

### Post by sgxnew54 on 2013-12-22
[B]I have replaced quiet splash  whit nomodeset but I had the same black screen..
help me ....please, do you have another idea  ??
[/B]

---

### Post by oldfred on 2013-12-22
What video card/chip do you have. Some others need different boot parameters with very new systems.

Some other recent model Toshibas.

       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Bucky Ball on 2013-12-23
> **sgxnew54 said:**
> [B]I have replaced quiet splash  whit nomodeset but I had the same black screen..
help me ....please, do you have another idea  ??
[/B]

You don't replace 'quiet splash', you add 'nomodeset' to the end of that line after a space. Not that it will matter a lot and don't think that is going to work anyhow.

---

### Post by oldfred on 2013-12-23
@Buckey Ball
I have nVidia and have to use nomodeset. 
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I only like to remove quiet splash as then you see boot process. Sometimes it will show the boot error on the last screen although it always seems to stop on the battery line.

---

### Post by Bucky Ball on 2013-12-23
You are quite correct. Edited.

---

### Post by sgxnew54 on 2013-12-23
I also have nVidia geoforce anyway, but that isn't the problem of the black screen because when I put the original value again on the parameter secure boot = "enabled" the pc booted again from  CD-live or USB-live.

So I done a new installation with secure boot = "enabled", this time i tried ubuntu 13.10, and I created 2 partitions "\"  ext4 primary and "swap" primary (I didn't create EFI partitions because I have a EFI Windows partition) . at the end I restart the PC but GRUB doesn't work again !!

So as last try  I thing to do a _boot-repair_ using a CD-LIVE   and to try to restart pc and see what happens. after this wath can do , anaything else  ??

thanks

---

### Post by oldfred on 2013-12-23
At grub menu have you tried these instead of nomodeset. They seem to have worked on several other Toshiba's and some other newer laptops.

acpi_osi=Linux acpi_backlight=vendor

But you may have this issue. You still should be able to boot from UEFI menu. Unless you have one of the UEFI that only boots Windows.

 Unable to chainload Windows 8 with Secure Boot enabled  
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -

---

### Post by sgxnew54 on 2013-12-24
Hi folks, finally I solved the problem of the boot-loader on dual boot ubuntu/windos 8.1. As already said I tried with ubuntu 12.04 live-CD and set up the BIOS (v. 1.40) param to _**"secure-boot=enabled" **_(this was the original value) otherwise I coudn't boot from live-CD either live-USB. Tthis is strange is compared to ubuntu documentation on UEFI BIOS that recommend secure boot disabled . Anyway after having installed ubuntu from live-CD I tried to restart PC and I had only windows boot. So I reboot PC from live-CD **(always with secure-boot=enabled)** and by a terminal I installed and launched the _boot-repair_ , I answerd to the questions always <Yes>, during the repair phase a strange message appeared [COLOR=#ff0000]<Buggy-Kernel detected. Do you want to activate [Backup and rename Windows EFI files ] ?[/COLOR] > I said <yes> again , boot-repair go on and terminated the work with the message BOOT.successfully repaired. The info of boot-repai is on URL [COLOR=#0000cd]HTTP://paste.ubuntu.com/6630413/ [/COLOR].

Now always with **secure-boot=enabled **I tried to restart the PC and with my great surprise I saw the GRUB loaded (vers. 2.0) with the entry for ubuntu and windows, evryting works either ubuntu that windows.

thanks for all the support.
regards.
Sandro

---

### Post by oldfred on 2013-12-24
The buggy UEFI then renames grub's shim file to have the Windows efi name. Then UEFI when booting Windows will think it is booting Windows when it really boots grub. And then from grub you boot the backed up/renamed Windows file.
Best to keep boot repair handy. If Windows updates replace the Windows file it will become Windows only again and you have to rerun Boot-Repair.

---

### Post by sgxnew54 on 2013-12-25
Hi oldfred,
well I could try boot repair handly, but can you  show me how to do ?

sorry, i made a mistake don't keep into consideration this post 

thanks in advance

---

### Post by oldfred on 2013-12-25
You keep your Ubuntu installer flash drive or DVD and when booted you can always add Boot-Repair again like you did. Or you can download a full repair ISO that is just Ubuntu with Boot-Repair included. But I think that now is one version older.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Some also cannot boot from grub to Windows with secure boot on.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

    
Always best to have a repair CD or Flash drive for the current version of every operating system you have installed. So also make a Windows repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---


---
title: "Grub is not loaded in dual-boot configuration"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by 0xddr on 2012-12-10
I tried to install Ubuntu on my new laptop (Sony Vaio S13). It came with preinstalled Windows 8 and some partitions for recovery purposes which I want to preserve. 

What I've already done:
- shrink Windows partition
- install Ubuntu (and grub) from usb 

But when I restart machine nothing happens - Windows 8 loads as normal, without any sign from grub. 
I tried to use boot-repair (from usb), but it gives some errors:
[HTML]http://paste.ubuntu.com/1424056/[/HTML]

---

### Post by oldfred on 2012-12-11
Our friends at Sony have done something nasty or Ubuntu is not mounting it correctly, although many other installs have worked. We have seen similar issues of not installing with other Sony systems.

> cp: cannot create regular file `/boot/efi/EFI/ubuntu/shimx64.efi': Read-only file systemI did not know you could make the efi partition read only, but until that is changed you cannot correctly install grub's efi files. Grub2 does have the secure boot version that should work but read only on FAT32 is something different.

Normally the read only setting is controlled by how you mount the partition with Ubuntu for both FAT32 & NTFS.  

Have you turned secure boot off in UEFI/BIOS?

Also if you have a setting for quick boot or fast boot turn that off also.

Two other Sonys that worked:
       ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

This user manually copied boot files and renamed them. Post 3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
       Sony Vaio dual UEFI boot with manual copy of files to efi partition
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

---

### Post by 0xddr on 2012-12-14
I partially solved the problem. Installing Grub on EFI partition was essentially, then I followed instructions from [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/) . Everything works - I can boot Ubuntu and Windows8. The problem is, that after restarting Windows8, it reverts all changes in /EFI/Microsoft/Boot, which are necessary to be able to boot Ubuntu.

---

### Post by oldfred on 2012-12-14
Microsoft's contract with Windows 8 vendors specifies that you the user must be able to turn secure boot off. So is Sony not in compliance with Microsoft?

Is there a setting somewhere in Windows to stop the overwrite and/or unlock the efi partition.

Did you turn off fast boot as that has caused issues with many UEFI installs.

---

### Post by 0xddr on 2012-12-14
I turned off in Bios SecureBoot, but there is not an option like fast boot. Generally this Bios is poor with options. But I will check this again and try to find something in Windows. 

Generally this EFI partition works here strange. When I followed the instruction from previous post, sometimes cp/mv were refused because partition is read-only, but when I remounted it, it worked. 

After all - thanks for help.

---

### Post by Ck.asdf on 2012-12-17
I have a Sony Vaio S SVS151190X notebook with Windows 7 and UEFI booting.  I am trying to dual-boot with Ubuntu Studio 12.10 x64.

My first few attempts at dual booting ended identical to 0xddr's situation:
*Install completes with no complaints,
*Reboot, Windows starts with no trace of Linux or Grub.


I just went about it a little differently, and got different results:
*Use gparted to delete EFI partition created by Windows, then re-create it with same specs - FAT32, boot flag enabled.
*Install Ubuntu, setting sda1 (EFI partition) as the place to put the boot loader.
*Restart, boots Ubuntu with no trace of Windows or Grub.
*Run boot-repair, enable Advanced Options, Grub location tab, check "separate/boot/efi partition:" and select sda1.
Hit Apply, reboot.
*Grub menu appears, options: Ubuntu or Advanced Ubuntu options.

After further search, I came up with adding an entry to /etc/grub.d/40_custom as listed below:
```

menuentry "Windows 7" {
    set root='(hd0,gpt3)'
    chainloader /boot/efi/Microsoft/Boot/bootmgfw.efi
    }

```
After adding this and running update-grub, I restarted and Windows appears in the list, but then I get this message when I choose it:
> 
error: file '/boot/efi/Microsoft/Boot/bootmgfw.efi' not found.
Press any key to continue..._

The directory referenced above contains the file mentioned, so I'm not sure why it's telling me it is not found.  Everything is spelled correctly with correct case.

So, no Windows yet. Any thoughts? The URL created by boot-repair is:
[http://paste.ubuntu.com/1444648/](http://paste.ubuntu.com/1444648/)

Thanks!

---

### Post by oldfred on 2012-12-17
@Ck.asdf
When you deleted the efi partition did you back up all the Windows boot files in the efi partition?
If you had no Windows files, then grub does not show menu, but just boots.

Script does not show one key Windows file, the BCD. I believe it is also in the efi folder with the other efi files.
       ? location of BCD?
/boot/efi/EFI/Microsoft/Boot/BCD

From UEFI menu can you directly boot Windows? Only if that works will the chain load entry from grub2's menu  work.

Boot-Repair would create similar chain load entries to the Windows efi boot files in 25_custom as grub2's os-prober creates BIOS type entries. 

Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

---

### Post by YannBuntu on 2012-12-17
> **0xddr said:**
> [HTML]http://paste.ubuntu.com/1424056/[/HTML]

Interesting case.

Indeed the ESP is not completely read-only, because Boot-Repair has been able to create /EFI/Boot/bootx64.efi.bkp , /EFI/Microsoft/Boot/bootmgfw.efi.bkp  , and /EFI/Microsoft/Boot/bootx64.efi.grb

So that means the ESP prevents the creation/modification of files except inside /efi/Boot and /EFI/Microsoft.
That's really ugly from Sony/Microsoft.

Bug report and workaround: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

---

### Post by Ck.asdf on 2012-12-18
@oldfred
For the purposes of last night's testing, I did not back up the Windows boot files in the EFI (sda1) partition.  However, that brings me to further explanation of my setup.

My Vaio came preloaded with Windows 7, a 20GB restore partition, and a bunch of extra software.  I took that hard drive out, stuck another one in, and installed Windows 7 fresh.  In the install, it actually alerted me that the drive was formatted incorrectly for EFI, and made the necessary adjustments, creating sda1 (EFI boot), sda2 (msftres), and sda3 (Windows).

I went ahead and plugged in the stock drive and Sony partitioned it as such:
Part - "LABEL" size flags
sdc1 - "SONYSYS" 260MiB hidden
sdc2 - "Recovery" 18.90GiB hidden, diag
sdc3 - [no label] 260MiB boot
sdc4 - [no label] 128MiB msftres
sdc5 - [no label] 445GiB  <-- Windows

The two interesting partitions here are sdc1 and sdc3.  After mounting each of them, these are their file structures:

sdc1 (SONYSYS, hidden flag)
```

/EFI/
    boot/
        bootx64.efi
        en-US/
            bootx64.efi.mui

    microsoft/
        boot/
            bcd
            bootmgfw.efi
            en-US/
                bootmgfw.efi.mui
                fonts/  ## (Several *.ttf files)

```

sdc3 (no label, boot flag)
```

/EFI/
    Boot/
        bootx64.efi

    Microsoft/
        Boot/
BCD           bootmgfw.efi  da-DK/        es-ES/        hu-HU/        memtest.efi   pt-BR/        tr-TR/
BCD.LOG       bootmgr.efi   de-DE/        fi-FI/        it-IT/        nb-NO/        pt-PT/        zh-CN/
BCD.LOG1      BOOTSTAT.DAT  el-GR/        Fonts/        ja-JP/        nl-NL/        ru-RU/        zh-HK/
BCD.LOG2      cs-CZ/        en-US/        fr-FR/        ko-KR/        pl-PL/        sv-SE/        zh-TW/

```

Hopefully the way I structured the paths above makes sense.


So you're right, there is something called BCD.  So this further research brings more questions:
*Which of the two partitions should I copy data from? I'm thinking sdc3.
*What do I need to copy from the original drive?
*Where should I put it?
*How should I configure grub?


You asked whether I can boot to Windows from the UEFI menu.  This menu you reference, do you speak of the UEFI version of grub, or are you talking about a menu within the BIOS?  If the second option, I think my friend's new computer has an EFI menu, but as far as I know, my laptop does not.  I've tried repeatedly hitting F11, as well as F12 at boot-up, but nothing happens.

Thanks for all the help!

---

### Post by oldfred on 2012-12-18
There has to be a way to get to UEFI menu. But it varies by Vendor. An I do not know yours.

Some with UEFI have said if you do not turn quick boot off the only way to get to UEFI menu is thru Windows but I do not know. Not even sure what quick boot is, but it seems like it skips some UEFI startup to boot faster. 

Some have also posted that the key combination has to be pressed quickly as there is not much time from power on to system already booting or past UEFI choice. Others have posted that the key combination is more complicated or some combination of keys. I am not sure with Sony what the possibilitys are.

You may need Windows repair flash.
       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
With BIOS you could recreate a BCD with the Windows repair tools. One user manually copied BCD from repair flash and manually edited it with BcdEdit. BCD uses something like UUIDs to know which partition to boot, so if yours is not from the same install it would have to be edited. Not sure if with UEFI you can directly boot into a Windows repair console.

Some of the UEFI systems seem to have another partition with efi files. For repairs then the UEFI/BIOS must be able to change the boot flag or gpt efi partition designation to ef00 to be the boot partition with UEFI. Then you can run the recovery or vendor repairs. 

With your system you seem to have the extra partition with efi files and another with the recovery image??

Boot-Repair will reconfigure grub to boot in efi mode if not installed correctly, and add a correct chain load entry to Windows. But you have to go into UEFI menu and choose ubuntu as boot choice. It remembers last choice an uses that until you change it. From UEFI you should get at least Windows & ubuntu. But some others have shown a large list of boot options like every bootable device in both legacy or UEFI modes and recovery or repair options.

---

### Post by Ck.asdf on 2012-12-18
Okay, I remember now that each partition has a unique UUID, and borrowing info from another partition may have the wrong UUID info.

It would not be terribly difficult for me to reinstall Windows, so that I could get the Windows version of the EFI partition back in place, and then work on modifying that, as it seems a bit easier than repairing the boot.  There's no personal data on the hard drive yet, so I'm not worried about losing anything.

So what I will do is make a backup of the current (Ubuntu-only) EFI partition, then reinstall Windows in such a way that Ubuntu will still be installed, but not bootable.  Windows will create its EFI partition and install itself to the spot I give it, then I can boot to Ubuntu live to work on the partition.  If something goes wrong, no worries, just re-install Ubuntu, but first make a backup of the Windows EFI partition, then proceed from there.

So if my first part works okay (install Windows, Ubuntu installed but unbootable), how would I proceed once I boot into the live disk?  What would I need to do in order to merge Windows and Ubuntu on sda1?

Thanks for your patience and working to find resolution! Hopefully if this resolves my issue, it will resolve the issue for 0xddr as well. :)

---

### Post by oldfred on 2012-12-18
All systems use the same efi partition with separate folders for each system. One user had multiple systems installed and his BootInfo showed many sub directories in the efi partition. If Ubuntu's efi files get overwritten you may just be able to copy back. 

Or Boot-Repair may be able to help reinstall grub-efi which would add the correct grub entries & efi files. I know it converts BIOS with grub-pc to UEFI with grub-efi automatically or you chroot into your install and do the same thing or total reinstall of grub. 

Another thread had a user reinstall Windows but it reinstalled in MBR mode. How you boot the Windows installer is how it will install. And when the Windows installer converted the gpt drive to MBR, it left the backup gpt partition table at the end of the drive & all the Linux utilities were confused if MBR or gpt.

---

### Post by 0xddr on 2012-12-18
@YannBuntu
I'll backup my data and prepare rescue disks and then I'll try your workaround. 

@oldfred
In my bios there is no option like fast boot. On Windows, in Vaio Care, I turned off "Fast Wake" or something like that, but it didn't help. 

I still don't know how to prevent Windows8 from overriding my changes on efi. It's even more annoying than issue with read-only efi.

---

### Post by Ck.asdf on 2012-12-24
Hello, and sorry for the delay.  I wanted to let you know that I have some great news - I've got Windows 7 & Ubuntu dual boot working!

I formatted the Windows partition as well as the EFI partition, then ran the Windows installer, and had it install into the pre-determined partition.  I then booted to Ubuntu live, installed boot-repair, ran it, and I can now successfully boot into either operating system.

---

### Post by oldfred on 2012-12-24
Glad you got it working.

Did Windows 7 install in UEFI mode or BIOS mode? And then Ubuntu should be in same mode.

I like to document how system is installed. I have the bootinfoscript which I run as part of every rsync backup. But you might just want to run the BootInfo (which also runs the bootinfoscript) from Boot-Repair just to document your system.

---


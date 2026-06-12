---
title: "grub2 fails to load 12.10 kernel in UEFI boot environment"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by hgroover on 2012-12-01
I have a new Asus Q500A laptop with 6gb ram, 750gb hard drive and Windows 8 Home preinstalled. CPU is Intel Core i5-3210M

It has the AMI Aptio UEFI bios which allows booting from the regular Ubuntu 12.10 cd as well as the 12.10 secure remix (which I'm using, more on that below).

I was able to shrink the Windows partition to 258gb and install Ubuntu 12.10 to a 20gb root/boot partition plus a 400gb /usr partition.

I can boot the live cd and mount the installed Ubuntu partitions as well as the first partition, which is a FAT32 UEFI boot partition.

Once I ran boot repair from the Ubuntu 12.10 secure remix, I was able to boot to grub and (after some hiccups) make it my default boot. This is the link for the boot repair output: [http://paste.ubuntu.com/1377659/](http://paste.ubuntu.com/1377659/)

The grub menu shows the Windows UEFI boot loader and it works as expected.

Trying to load Ubuntu 12.10 from grub results in no disk or screen activity. Using the advanced options added to grub and the recovery option shows the messages "Loading initrd" then no screen mode change and no disk activity. Dropping to the grub command prompt and manually putting in kernel options with noefi and various other options suggested in this thread: [http://ubuntuforums.org/showthread.php?p=12373674](http://ubuntuforums.org/showthread.php?p=12373674) I get the same results.

I've reinstalled a couple of times and get the same results. The live CD works fine. I am able to run a VMware lubuntu image under Windows 8.

My next step would be to build a kernel and initrd with more early debug info and put them on there (which I can do, just haven't had time yet).

I've also looked at options in the BIOS which seem that they might have an effect on this but nothing seemed obvious, and in any case they had no effect on this problem.

I've also tried using the earlyprintk kernel option (which I'm used to using in embedded work) but I get nothing out of that.

Turning on set debug=all in the grub2 command environment gives me a couple of pages of malloc() messages then causes erratic behavior.

I haven't been able to find any other options for debugging early in the grub load process but it looks to me more like a problem in the early stages of kernel init and may require some remapping of memory, possibly related to the UEFI environment.

---

### Post by dino99 on 2012-12-01
browse the uefi section into the grub link below to be sure that your installation is made as it might.

---

### Post by oldfred on 2012-12-01
Some have had issues with large / (root) partitions. Either a separate /boot or a smaller / (root) and separte /home may work. Sometimes the boot files have to be closer to the start of the drive, but I do not think I have seen that with UEFI boots. Still think it may be a BIOS settings on those systems.

Did you turn off fast boot or quick boot setting in UEFI. That seems to be a conflict in many systems.

different system but Asus may be otherwise similar?
       Windows 8 & Ubuntu [  ASUS K55A 
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

            Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)


Older, as now compiling not required with grub2 2.00
       
 efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)

       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Some UEFI systems have the shell, some may not. Not sure of details, but seems to allow some checking of details.
       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Update
You mentioned aptio UEFI/BIOS. This user has a Dell but when he posted screens in post#26 it showed aptio. Are yours the same screens? He gets grub menu but cannot boot either. Still not resolved.
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by hgroover on 2012-12-01
Quick answers:

@dino99: Pretty sure I went through that but I will check. Thanks.

@oldfred: Aptio is either a brand or a module licensed by AMI. I think Dell uses AMI as well. Aptio seems to be relatively new and specific to UEFI.

Note that the manufacture date on my laptop is Sep 2012.

Yes, I tried with fast boot off (in the BIOS setup) as well as with the default. There is also an Intel antitheft feature which I tried turning off with no change. There is also a virtualization accelerator setting which I also tried both ways. I didn't really expect CPU feature bit toggles to have much effect - the platform init code is probably testing all those properly.

Re: this thread: [http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
yes, I am seeing exactly what he describes - screen blank with the same aubergine color, no apparent mode change, no disk activity. The only observation I'll add to this is that if I select recovery mode, I can press ENTER twice and see a bit more disk activity, then ENTER twice more and a bit more disk activity (for perhaps 500-800ms each time). Then no response. Ctrl-Alt-Del mostly works for me, sometimes power button needed to reset.

He does seem to have a vfat partition for all the EFI loaders. So it seems quite possible this is the same issue.

I'll go through the other links a bit later but wanted to reply quickly on the things I already know. Thanks!

---

### Post by hgroover on 2012-12-01
Yes, I've gone through the grub configuration and it all looks reasonable.
I had missed the serial console option when I looked through grub2 docs before, I'll set that up and see if I can get more info. That's helpful, thanks.

I'm just wondering if there's some odd problem with grub needing to set up special memory mapping to load the kernel in the EFI context. Didn't see anything in your grub2 link related specifically to EFI: [https://help.ubuntu.com/community/Grub2#Booting_from_a_serial_console](https://help.ubuntu.com/community/Grub2#Booting_from_a_serial_console)

I did find on one of the archlinux pages a suggestion to try with(out)add_efi_memmap

[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
I tried both with and without and it had no effect.

> **dino99 said:**
> browse the uefi section into the grub link below to be sure that your installation is made as it might.

---

### Post by oldfred on 2012-12-01
Do not know details of grub. But Boot-Repair uninstalls grub-pc and installs grub-efi. Not sure if it is just grub or if when that runs it also runs a dpkg to reconfigure something else like it does with video drivers.

Best not to power down if at all possible. Remember the elephants.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

    
Have you gone thru nomodeset or other boot options? What video chip do you have?
Does removing quiet splash or recovery mode show any of the boot process? It normally should show all the drivers being loaded.
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
If started does alt f1 get you to a terminal?

Older issue with several boot options.
       [SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by YannBuntu on 2012-12-01
Hello

> **hgroover said:**
> boot repair output: [http://paste.ubuntu.com/1377659/](http://paste.ubuntu.com/1377659/)

Please boot on your Ubuntu-Secure disk, connect internet, update the boot-repair and boot-sav packages:
```
sudo apt-get update; sudo apt-get install -y boot-repair boot-sav
```
then run Boot-Repair and indicate the new URL that will appear?

This will provide additional information about SecureBoot.

---

### Post by bpowers81 on 2012-12-04
hgroover, any luck? I'm going through the same issue. It feels like a kernel issue or a hhd issue.

---


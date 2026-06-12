---
title: "Grub won't work, can't run boot-repair, blank screen"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by Hansje on 2013-11-27
Hi,
I have an MSi GE70 laptop (Graphics: nvidia GeForce GT650M). At first I couldn't boot nor install, after adding 'nomodeset' in Grub I was able to start the installation, Try ubuntu just gave me a blank screen.
I installed a dualboot with ubuntu 13.10 and Windows 8.1, UEFI, secure boot off (UEFI with CSM).
After the installation was a success the computer boots straight into windows. I know this could happen and need to run boot-repair from the live-cd. Unfortunately I can't find a way to do this from CLI, since I get a blank screen in X I cannot use it's GUI.
I tried installing nvidia-current when booted with the live-cd, restarting lightdm (/etc/init.d/lightdm stop/start). No luck.
Trying to diagnose the problem this are the things I found:
/var/log/lightdm/x-0.log ends like this:
```
(EE)
Fatal server error:
(EE) no screens found(EE)
(EE)
Please consult the The X.org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help
(EE) Please also chech the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
```
Looking at /var/log/xorg.0.log I noticed:
```
[  1867.351] (II) VESA(0): initializing int10
[  1867.351] (EE) VESA(0): V_BIOS address 0x0 out of range
[  1867.351] (II) UnloadModule: "vesa"
[  1867.351] (II) UnloadSubModule: "int10"
[  1867.351] (II) Unloading "int10"
[  1867.351] (II) UnloadSubModule: "vbe"
[  1867.351] (II) Unloading "vbe"
[  1867.351] (EE) Screen(s) found, but none have a usable configuration.
[  1867.351] (EE)
Fatal server error
[  1867.351] (EE) no screens found(EE)
[  1867.351] (EE)
Please consult the The X.org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.
[  1867.351] (EE) Please also chech the log file at "/var/log/Xorg.0.log" for additional information.
[  1867.351] (EE)
[  1867.351] (EE) Server terminated with error (1). Closing log file.
```
So I am trying to run Boot-repair but I'm stuck because I can't get the GUI working with the live-CD. I'm added 'nomodeset', tried 'xforcevesa'.
Can anybody help me with eigher Boot-repair from CLI or graphics in live-CD?
For me it's weird that the installation is able to show a nice GUI where the liveCD doesn't find a screen...
If I am able to boot into installed Ubuntu, I probably will run into the same graphics problems, but maybe it's easier to fix them on an installed version?

Thanks!

---

### Post by technoshaman on 2013-11-27
I have exactly the same problem trying to install Ubuntustudio 13.10 with  HP ENVY 17-j011 notebook, also using Nvidia GeForce 740M. Have the same "No screens found" message. I then removed the Dual boot HDD with Windows 8, and installed Ubuntustudio 13.10 on a new drive. Same problem, only get a grub> prompt and "No screens found".

---

### Post by oldfred on 2013-11-27
With nVidia nomodeset works. With systems with both nVidia and Intel may be booting in one mode not the other. So are you booting with Intel or nVidia? And some auto switch, others have settings in UEFI/BIOS to set to one only. Intel for low power use and nVidia for performance.

Also are you booting in UEFI mode or BIOS mode. If purple screen that is BIOS, if grub menu that is UEFI.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
If Intel boot, try either of these instead of nomodeset.
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

      
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)

---

### Post by Hansje on 2013-11-28
Thx oldfred, that was a lot to read trough.

This is the situation I'm in now:
First I tried to fix the graphics while booting the liveCD, none of the options you listed worked for me. BUT: If I set boot method to 'Legacy' and add 'nomodeset' to boot the liveCD it works. I installed the system and tried to run 'boot-repair'. At the end of the procedure I got an error about a locked ESP partition. After some googling I found that a corrupted grubx64.efi file could cause this problem, I removed the 'boot' flag with Gparted, mounted the partition, deleted the file, unmounted and putted the 'boot' flag back, rerun boot-repair, OK now. Boot-repair tells me to switch back to UEFI for grub to work. Great! this way I will still be able to boot to Windows as well.

I changed back from 'Legacy' to 'UEFI', fired up and... windows straight away, scanning and repairing my disk, no grub. I booted back into the liveCD (Legacy, nomodeset) and rerun boot-repair, changed from Legacy to 'UEFI with CSM', grub starts! I am able to boot into Windows without losing GRUB, however, I cannot boot into Ubuntu, it is stuck at: 'Loading initial ramdisk'... Using recovery mode doesn't help, using nomodeset or one of the other options you gave me either. So at this point I'm still stuck, but I feel like we'll get there eventually. At this point I can't boot into Ubuntu to install nvidia/bumblebee.

I searched some more and found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237392) Is it possible that this is the problem? Or is there a problem with installing when booted with 'Legacy' and boot in 'UEFI with CSM'? UEFI has to do something with it I guess since I was unable to boot the liveCD without switching to Legacy...
I want to try installing the nvidia drivers and bumblebee, and if that doesn't work I want to replace the kernel with the one provided in the bug-report. But how? I can not boot into Ubuntu, is it possible to install these packages on disk using the LiveCD?

Thanks in advance!

---

### Post by oldfred on 2013-11-28
It looks like bug report is related to LVM, which has to mount lvm2 driver to work. You did not install with LVM nor encryption which uses LVM?

Post link to latest boot info report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Hansje on 2013-11-29
I forgot to write it down, so I booted with liveDisc (in Legacy mode) and used boot-repair to make a bootInfo Report. The link: [http://paste.ubuntu.com/6492991/]("http://paste.ubuntu.com/6492991/")
I installed with the standard setup, so I guess there's no LVM involved. Although the partitioning isn't straight forward. I have a RAID (striping) of 128 GB (64x2) of SSD's (with partitions: recovery, boot, windows OS and another one...) and a hdd of 1TB (recovery, windows Data, Ubuntu installation). I don't know whether this triggers LVM (as far as I understood it is never installed without specifically asking for it)?

---

### Post by oldfred on 2013-11-29
Boot-Repair (and oldfred) cannot tell LVM from RAID as both use /dev/mapper/... as mounts, so they may look similar at first. I do not know RAID nor LVM.

It looks like your efi partition is inside the RAID?, I thought the efi partition had to be a separate partition outside RAID, but have seen very few RAID with efi systems, so so not really know.
It does look like fstab has the UUID of the FAT32 RAID partition as the efi partition and all the boot stanzas correctly refer to that UUID.

It also looks like Boot-Repair ran its 'buggy' UEFI rename. That is only for UEFI that only boot the Windows efi file. The work around then is to name grub or shim to the Windows filename, then UEFI thinks it is booting Windows but really boots grub menu. And then from grub menu you boot Windows backed up entry.

       Boot-Repair renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

If you can boot from the ubuntu entry from UEFI, you do not need rename and can manually change names back or undo it with boot repair. Windows updates may restore a Windows version of bootmgfw.efi so best to backup the entire efi partition and have live installer handy.

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

The issue of loading intially RAM disk then is after UEFI boot with grub as you get grub menu. You may need other boot options ot install may not have been correct. 
You probably want to stay with UEFI boot mode not CSM. But a few systems only would install in CSM/BIOS mode and very few would only work in that mode. Boot-repair can convert a BIOS boot Ubuntu to UEFI boot by chrooting into system and uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

If not dual video and you are booting with nVidia you need nomodeset, but may also need other parameters. 
But if dual video you may need Intel parameters and others also. Also some new systems need some default UEFI/BIOS settings changed. Is this a new Haswell system? 

 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by Hansje on 2013-12-03
Well, it's this laptop: [http://www.msi.com/product/nb/GE70-0NC.html#?div=Specification](http://www.msi.com/product/nb/GE70-0NC.html#?div=Specification)
Dual video? don't think so (not entirely sure what you need to know), the link above states just one graphics card: GeForce GTX 765M. I was able to boot into the liveCD with just nomodeset, doesn't this mean that it should be ok to do the same in the installed system? I feel like the it's not the graphics holding me from booting (or am I missing something?).
Is this a Haswell system?, don't know for sure, windows tells me its a Core i7 4700MQ, according to Wikipedia this is a 'Haswell-MB': [http://en.wikipedia.org/wiki/List_of_Intel_Core_i7_microprocessors#Ivy_Bridge_microarchitecture](http://en.wikipedia.org/wiki/List_of_Intel_Core_i7_microprocessors#Ivy_Bridge_microarchitecture)
Looking at this wikipedia page I notices this Haswell-CPU has a GPU onboard, so it seems like I have dual graphics after all. But why did my liveCD boot and the installed system won't?

---

### Post by oldfred on 2013-12-03
Dual video can complicate the install. Some auto switch and others have settings in UEFI/BIOS that set which video mode you boot with.
nVidia and Intel need different boot parameters. So if you have Intel video then you may need different settings.

Everything I read says the new Haswell processors are much improved, lower power and built in video much better. Your built in Intel video is as good or better than the 4 year old nVidia 9600GT in my desktop. And then your nVidia will give even better performance but shorter battery life.

       Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

While different brands the Intel settings should be similar.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Hansje on 2013-12-03
Thanks again for the reply oldfred.
I tried all additional options to boot into liveCd or installed system using UEFI. None of them worked...
So there's the trick with disabling the NIC in BIOS, unfortunately there's no option in the bios to do so, nothing about graphics either...
I checked the BIOS version, it's the latest available.
Still stuck, but eventually it has to work, I just know it!
Thx again!

---

### Post by oldfred on 2013-12-03
If video is Intel when booting you need Intel boot parameters. 
Another Haswell system.
 (13.10) Intel graphics driver fails to manage HD 4600 on HP Split x2
[http://ubuntuforums.org/showthread.php?t=2191109](http://ubuntuforums.org/showthread.php?t=2191109)
Needed all the settings.

---

### Post by keifus-rahn on 2013-12-03
Have you tryed booting into bios by holding shift-F2 while pressing power and stay holding shift-F2 till boot screen appears. Thats what happend to me yesterday it took a few time but it finaly booted into bios  ( Some comps go by holding shift-F2 or shift-F12 )

---

### Post by Hansje on 2013-12-04
@ oldfred: I tried the solution in that post, also with the alternative video=VGA-1:1920x1080-24@60.
Still stuck at 'Loading initial ramdisk'...
I will try to start a thread on MSi forum on how to disable the NIC (just to try).
[https://forum-en.msi.com/index.php?topic=175393.0]("https://forum-en.msi.com/index.php?topic=175393.0")
@keifus-rahn: my laptop boots into bios with 'delete' or 'del' key. The options to disable NIC or choose video mode are just not there...

---

### Post by oldfred on 2013-12-04
Have you verified that the ISO you downloaded was correct?

       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Hansje on 2013-12-04
I did, it's correct. I even downloaded a second time, tried with both USB and DVD
Since I need it for work I can't wait longer, so I decided to run ubuntu in virtualbox.
I will keep trying to get it working, but my responses will be somewhat slower.
Thx oldfred!

---

### Post by oldfred on 2013-12-04
For the dual video part of your issues another user reported this worked well.

 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

### Post by Hansje on 2013-12-05
I don't think graphics are the problem, I tried all options I could find. I already read trough the link you provided in your last post. With 'nomodeset' I can boot in Legacy mode, with UEFI turned on I wasn't able to boot, not with LiveCd nor installed system, not with nvidia boot params nor intel boot params.
Most of the problems I red about are driver related, but they are able to boot and install eg bumblebee to fix it. But I'm stuck at 'Loading initial ramdisk...' (when trying to boot into recovery mode).

I refused a mac to work with because I don't like too expensive equipment (and aggressive marketing), but now I can't work at all. I tried booting into windows and install Ubuntu 13.10 in Virtualbox. It worked, but a higher resolution as 1024x768 wasn't possible (the Virtualbox Guest Additions could not find correct modules for the running kernel). It's the graphics that need to be perfect, so this won't work either. The next thing I'll try is installing 12.04 in Virtualbox.
I still hope someone (you?) can help me installing 13.10 in dualboot with Windows.
Thx oldfred, you deserve a medal for not giving up helping! Especially because I'm a complete stranger to you!

---

### Post by oldfred on 2013-12-05
If you have Intel 4600 graphics as well as nVidia, it is a new Intel Haswell chip. I have only seen 13.10 work with the new Haswell chips. When 12.04.4 comes out in Jan it will also have those updates but 12.04.3, the current version is not as new. And a lot of the changes were grub, kernel & UEFI related that Intel helped update to work with the newest chips.

Do you know or can set which video you boot with? Some auto switch so it is a bit more difficult to tell. Nomodeset works with nVidia, but the Intel settings are needed with the Intel chip if booting with it.

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

Even though new pc, have you check that UEFI/BIOS is most current version? Vendors also are making major changes.

---

### Post by Hansje on 2013-12-05
But I tried everything... there are two things I can't try because BIOS won't let me: disable the NIC, choose which graphics card to use. The only way to boot is with 'nomodeset' in Legacy mode, but I don't want this because Windows refuses to start in Legacy mode. When UEFI is switched on, there are no options left to try, neither for the nvidia dedicated card nor the integrated intel GPU. I also tried to combined all this options in various ways, I'm always stuck at 'Loading initial ramdisk...'

I installed Ubuntu 12.04 in Virtualbox now, was working great, after installing the Guest additions I got a black screen with blinking cursor. After following [this tutorial]("https://forums.virtualbox.org/viewtopic.php?f=3&t=55146") I can finaly start working (I'd still prefer a dualboot, bot OK, seems to be impossible).

I thought Ubuntu was a good way to go, but it seems that it can't keep up with the new hardware.

---

### Post by Hansje on 2014-04-30
Finally fixed, Grub was the problem. The only way I got it to work: load Grub on startup, let grub load refined, refined will load linux.
As I started to think this had nothing to do with graphics.

---


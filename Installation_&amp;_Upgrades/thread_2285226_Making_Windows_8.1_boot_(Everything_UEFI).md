---
title: "Making Windows 8.1 boot (Everything UEFI)"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by Rajendra_Adhikari on 2015-07-04
I had a functional Ubuntu 15.04 and then I installed windows 8.1 on a new partition. When the installation completed I lost ability to boot into ubuntu (I would auto boot windows). I then booted via a live ubuntu CD, removed the boot entry for windows using efibootmgr, and then ran boot-repair. It successfully restored my ability to boot into Ubuntu, however it failed to make entry for windows and enable me to boot into windows.

here is my situation:
[http://paste.ubuntu.com/11819341/](http://paste.ubuntu.com/11819341/)

My system-settings is set to boot exclusively on UEFI mode all the time.

Can somebody please provide some insight?

Thanks.

---

### Post by oldfred on 2015-07-04
At some point you installed grub to both the gpt drive's protective MBR & to the partition boot sector of sda3. With UEFI neither of those parts of drive are used, so they do not need to be erased.
But with UEFI you do not need the tiny bios_grub partition as that is only created for BIOS boot of Ubuntu.

While you have an ESP - efi system partition, your fstab now has it commented out.
Did you manually change that? You need to uncomment that.

It does say you booted Boot-Repair in UEFI mode, but it wants to reinstall grub in UEFI boot mode. Probably because your fstab has no efi mount.

This was what Boot-Repair suggested which I believe means uncomment one efi entry in fstab.
> EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.
Do you want to continue?


---

### Post by Rajendra_Adhikari on 2015-07-04
Hi,
When boot-repair said:
```
EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.
Do you want to continue?
```

I didn't know that that exactly meant (I was thinking EFI being detected is a good thing. I need EFI partition so that it can install boot files in that partition. I don't know why it was complaining.)
I preceded anyway (probably bad decision)
It then at one point asked me to select partitions to install grub 2.
I chose sda1 and sda3. (It did say it was good to select all if not sure)
I even chose the thumbdrive from which I was using the live ubuntu. It failed to install grub in it though. (Any idea why?)

Now, I don't understand what fstab is, and how I comment/uncomment things in it?

Thank you.

---

### Post by oldfred on 2015-07-04
Boot-Repair does go beserk on installing grub to too many places. Often better to use advanced mode and choose details. And with UEFI, you did not want BIOS version of grub installed.

You may need to use Boot-Repair to totally uninstall grub and reinstall when booted in UEFI mode.
There are two+ versions of grub. Grub-pc for BIOS and grub-efi-amd64 for UEFI. That may automatically change comment on efi partition in fstab.

If you need to manually edit it from live installer, you need to mount efi partition and then include that mount in path.

 sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/etc/fstab

Live installer may not have gksudo which should be used for gui apps (gksudo being discontinured?). Many suggest nano as terminal editor:
sudo nano /mnt/etc/fstab

---

### Post by NoWayWin8 on 2015-07-04
You should double-check the computer's UEFI firmware (formerly "BIOS") to be sure it is set correctly. Windows 8 was apparently installed in BIOS mode (aka "Legacy").

> =================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda3 into the MBR of sda.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems  fix-windows-boot
This would indicate the computer is not in full UEFI mode, or at least it wasn't when Windows 8 was installed, and that some legacy BIOS option is still active in the firmware.

First thing to do is make sure the firmware is up-to-date and settings are correct for native UEFI boot. I think your model has a BIOS setting called "OS Optimize" (or similar) which allows a choice between "Windows 8" and "Other OS" - make sure it is set to "Windows 8" (this is what toggles legacy compatibility support off). Windows 8 will have to be reinstalled (really both OS's).

---

### Post by Rajendra_Adhikari on 2015-07-04
I have always set the system settings to ('BIOS' settings) to UEFI only boot mode. I installed windows 8.1 by booting the thumb-dive in that mode, and then booted win-8.1 on the same mode. I don't see any chance of windows 8 being installed in BIOS mode.
What I doubt though is that boot-repair did try to create BIOS partition and install grub2 for bios-mode booting (for some reason).
I ran boot-repair in advanced mode and selected separate efi-partition (whatever that meant), but still no luck. I get a list of booting options: ubuntu, windows-boot-manager, and others, out-of which only the live USB booting, and booting the Ubuntu works. One other booting entry takes me to a grub command line.

[http://paste.ubuntu.com/11822056/](http://paste.ubuntu.com/11822056/)

---

### Post by oldfred on 2015-07-04
Your Windows is definitely installed in UEFI mode, as Windows only boots from gpt partitioned drives with UEFI.
And since fstab now shows the efi partition being mounted, I expect Ubuntu is bootable in UEFI mode.

When you say you get a listing of boot options, it that the UEFI menu or the grub menu?
You may want to add a Windows efi boot entry to UEFI boot menu.
       This should create a new entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

If you are getting grub menu with a Windows boot entry at bottom and still have issues then it may be video driver or some other driver related.

What model Lenovo & what video chip/card?


 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

---

### Post by Rajendra_Adhikari on 2015-07-04
You seem to have figured it out.
Its a grub menu. And here is the listing:

```

Ubuntu
Advanced Options for Ubuntu
EFI/BOOT/bkpbootx64.efi
EFI/Ubuntu/MokManager.efi
Windows Boot Manager (on /dev/sda1)
System setup

```

The ubuntu options works fine. 
The Advanced options for Ubuntu is also is fine.
Out of the 3rd and 4th entry, one takes me to a grub command line, the other takes me to some program with blue screen
The 5th entry, Windows Boot Manager, does nothing. The screen blinks and I am back at the same menu.
The 6th entry takes me to Firmware settings ('BIOS' settings)

Do you think I should still try to add an entry for windows using 
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" ?

When I do sudo efibootmgr -v, from my ubuntu, why don't I see windows boot manager, even though its available in the boot menu? 

rajee@rajee-ThinkPad-S1-Yoga:~$ sudo efibootmgr -v
[sudo] password for rajee: 
BootCurrent: 000C
Timeout: 2 seconds
BootOrder: 000C,0000,0001,0002,0003,0006,0007,0008,0009,000A,000B
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0007* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0008* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0009* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000A* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000B* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000C* ubuntu    HD(1,800,64000,e1f5267b-4bbf-4440-a347-40fd8b624757)File(\EFI\ubuntu\grubx64.efi)

My machine is the Lenovo Thinkpad Yoga. 

rajee@rajee-ThinkPad-S1-Yoga:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

I will try to see if any of the driver issue of other thinkpad models applies to me.

---

### Post by oldfred on 2015-07-04
UEFI is a boot manager. Or a menu of bootable options.

Grub is both a boot manager and a boot loader.

I did think that after several reboots UEFI adds entries it finds in the efi partition. So I would think it should add Windows. But you just may have to manually add it yourself. Then you can also see if you can directly boot Windows from UEFI or one time boot key like f10 or f12, when grub does not boot Windows.

You have the grub chain entry to Windows efi file in the efi partition. That usually works, but both Ubuntu & Windows have to be booting in UEFI mode, secure boot must be off and Windows must not be hibernated or fast startup must be off.

---

### Post by Rajendra_Adhikari on 2015-07-04
I did manually add the entry.
It didn't change the grub boot menu (which already was showing the entry for windows-boot manager). 
I could still NOT boot windows. 
I retried with temporary boot selector (F12) before the grub boot menu. This time, I did have entry for Windows-boot manager at the top in the UEFI firmware boot selector. However, no luck booting windows from there too.

[http://paste.ubuntu.com/11822616/](http://paste.ubuntu.com/11822616/)

Any idea on what next?

(I always have secured boot disabled, boot-order NOT locked, fast boot disabled, UEFI only boot enabled. Both my ubuntu and windows is installed in UEFI mode,and my hard-drive has GPT partition. )

---

### Post by oldfred on 2015-07-04
If you cannot boot Windows from UEFI directly, then that is a Windows issue. Can you press f8? Or from Windows installer go into repair console.
Grub only boots a working Windows and from grub menu you usually cannot press f8 quick enough to get into repair console. Either UEFI boot or from a repair disk or installer if it has repair console.

[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

---

### Post by Rajendra_Adhikari on 2015-07-04
I had working ubuntu 15.04. Then I had a working windows when I installed and booted windows 8 (but lost ability to boot Ubuntu). Then, when I ran boot-repair from live Ubuntu, I got back Ubuntu but lost Windows again. So apparently, I do have working windows but somehow can't get to it.

---

### Post by Rajendra_Adhikari on 2015-07-04
I just booted from Windows 8.1 installation USB, and then chose 'repair startup problem'. On restarted, I autobooted into my Windows 8. So, there infact is a working windows 8 present. I pressed F12 to choose boot medium while rebooting, and on the UEFI firmware boot menu, chose Ubuntu, but it didn't boot me to Ubuntu (just a black screen forever).
So, can anybody make something from this new information?

The next natural step would be to boot from live Ubuntu CD and then run boot-repair, but then I would get back Ubuntu and loose Windows again. Its going around in a loop.
I am on Win 8.1 right now.

Any suggestion please?

---

### Post by Rajendra_Adhikari on 2015-07-04
So, I booted from live Ubuntu USB and here is my situation:
[http://paste.ubuntu.com/11823980/](http://paste.ubuntu.com/11823980/)

---

### Post by oldfred on 2015-07-04
Sounds like boot issues are actually solved.
But black screen after grub is usually video driver, but occasionally another driver issue.

What video card/chip?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by jobsworth on 2015-07-05
i have never suceeded in creating a dual boot system with windows and linux on a drive with 2 partitions.
and as for wubi i see that it is no longer available. it was unreliable.
i have always had some of the problems described in this thread.
my solution is to have 2 hard drives one with windows and one with linux.
i even disconnect the other drive when installing.
then run wundows and disable the quick start option using the control panel and power options.
with 2 drives i then arrange in the bios to boot linux. then run update-grub which will find the windows disk.
the next time i boot grub will show everything.
and i can boot windows if i want to. windows is good for games.

---

### Post by Rajendra_Adhikari on 2015-07-05
Thanks.
What I don't understand is,  since I can boot windows fine (after I do start-up repair using Windows installation disk), how can drivers be blamed ?
If it is relevant: Lenovo thinkpad s1 yoga
[COLOR=#000000]00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

[/COLOR]

---

### Post by oldfred on 2015-07-05
Intel driver does not use nomodeset. And usually it works, but you need to be installing new versions of Ubuntu or add a ppa to get latest drivers.

Intel is actually pretty good about updating kernel, support software & video drivers that are in distributions. But timing is an issue as they release software, it has to be accepted into a new kernel, and then accepted into a new distribution. 

I installed 15.04 to a new Dell with Haswell i3 and internal graphics and it just worked.

 Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

Linux does not use Windows drivers.

---

### Post by Rajendra_Adhikari on 2015-07-05
I can boot both windows 8.1 and Ubuntu 15.04 fine (but only one, for any given boot-settings); problem only is making dual boot work. If I run boot-repair, only ubuntu works. If I use windows 8.1 installer startup-repair only windows 8.1 works. 
Now, how is it a driver problem? 
sorry, if I am asking the same thing again, I just don't get it yet.

---

### Post by oldfred on 2015-07-05
Did you re-install Ubuntu in BIOS/CSM boot mode?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode
You had grub both in gpt's protective MBR for BIOS and in efi partition for UEFI.
Is Summary report posted in #14 still the current one?

UEFI & BIOS are not really compatible, they are two totally different ways to boot a computer. One is legacy for those who want old way and one is the newer way. 
And then you can only switch boot modes from UEFI boot selection or one time boot key when starting system.

What brand/model system?
Some brands try to restrict booting to only Windows by description which is not per UEFI standard.
So we have to use work arounds to get ubuntu/grub to boot in UEFI mode.

Are the current work arounds are in the link in my signature, but it may depend on brand which is better.

---

### Post by jobsworth on 2015-07-05
is my english that bad? i am talking about hard drives not drivers.
and yes it should not matter having two partitions on one hard drive
only i have never succeeded in dual booting like this.

---

### Post by oldfred on 2015-07-05
Two drives is a good way to install if you have two drives.
Most laptops only have one drive, so you have to install to different partitions.

---

### Post by NoWayWin8 on 2015-07-06
The lack of a bootmgrfw.efi in the EFI partition is a telltale sign that Windows did not install in UEFI mode:
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/BOOT/bootx64.efi /EFI/BOOT/grubx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi
```
Unfortunately the installation won't work as it is currently. If you want Windows 8.1 you will have to enable secure boot, then reinstall. 

Any other OS (like Ubuntu) will install in UEFI mode, but unfortunately Win8/8.1 occasionally violates the UEFI standard (that MS helped design). Windows 8.1 defaults to a legacy install if secure boot is disabled. Ridiculous, I know.

[http://answers.microsoft.com/en-us/windows/forum/windows8_1-security/uefi-secure-boot-in-windows-81/65d74e19-9572-4a91-85aa-57fa783f0759](http://answers.microsoft.com/en-us/windows/forum/windows8_1-security/uefi-secure-boot-in-windows-81/65d74e19-9572-4a91-85aa-57fa783f0759)
> 
**You can enable / disable Secure Boot with UEFI Boot. Legacy Boot will _automatically_ get  enabled, Either if UEFI Boot Or if Secure Boot is disabled. This is  because Legacy Boot must become the default boot without UEFI Boot, and  Legacy Boot must act as an alternative to the UEFI Boot  without Secure Boot.**  **The ****choice  for UEFI Boot OR Legacy Boot must be set prior to Windows 8  installation, depending on the MBR/GPT Hard Drive partition table to be  used. **After installation they must not be changed. Changing them will not allow the system to boot.  The EFI Shell / Command Prompt can  also be used to configure the BCD and Boot Policy by running the  platform boot configuration commands in User Mode.  To ascertain the type of Platform  Firmware on a Windows 8 computer, open Run ( WinKey+ R ), type  "msinfo32" and click OK. This opens the **System Information** window. Select System Summary (on  the left panel) and check for the Items "BIOS Mode" and "Secure Boot  State". The BIOS Mode value can be *UEFI/Legacy, *and the Secure Boot State value can be *On/Off* when UEFI Mode and *Unsupported* when Legacy Mode.  
 **INSTALL Windows 8.1 on UEFI**  **UEFI BIOS boot settings is  specific to an OS and must prelude to the OS installation. For UEFI  Boot, it is essential that the Motherboard, Processor, HDD Partition  Table and the OS conform to 64-bit operation. **UEFI Boot will not be possible, if any of these component is  not 64-bit compliant. Further if a DVD media is used for OS  installation, the DVD drive must also be 64-bit capable.

---

### Post by oldfred on 2015-07-06
I do not think I have seen /EFI/Microsoft/Boot/bootmgr.efi?

It is either bootmgr in top level or root of Windows boot partition or install for BIOS boot or in efi partition it is bootmgfw.efi for UEFI boot.

Or did OP copy BIOS boot file into efi partition and add .efi? Or rename bootmgfw.efi?

---

### Post by NoWayWin8 on 2015-07-06
Oops, I mispeled it: should be bootmgfw.efi.

Weird, it wasn't in OP's first boot-repair output (the one I quoted from) but it is shown in the most recent one.

---

### Post by jobsworth on 2015-07-07
what about update-grub

---


---
title: "Win 10 + Ubuntu dual boot - no option after install"
date: 2017-11-17
forum: Installation &amp; Upgrades
---

### Post by me762 on 2017-11-17
Hi all,

Complete newbie here so bear with me. I tried to install ubuntu alongside windows 10 using USB boot stick and to all intents and purposes it was successful. However, I can't seem to actually get into it as an OS. 
No boot option appears on starting the computer and it's not present to select as part of the boot order in the BIOS. In Windows Disk Management, the partitions were created and if I try to 'delete volume' it tells me another OS is using them, so it appears to be there. I just can't seem to get into it!

I've tried multiple posts and guides but nothing is helping, I have Secure Boot disabled as well. Any help greatly appreciated.

So far I have tried: 
[LIST=1]
[*]Initially installed alongside Windows 10 from USB, same problem, can't get into it.
[*]Deleted the partitions, disabled secure boot and tried installing in legacy mode - got a "partition needs to be reserved for bios" error message and noped right out of that.
[*]Went back to UEFI and installed again, going through the manual partitioning in ubuntu this time and set a root (20GB, ext4, mount point = /), home(~1.4tb, ext4, mount point =/home) and swap (16GB, swap area)  partition and I'm back to where I started. It seems to be there, I just can't find a way to boot into ubuntu.
[/LIST]

---

### Post by oldfred on 2017-11-17
If Windows 10 is installed in UEFI, and all pre-installed Windows are now UEFI, you want Ubuntu in UEFI boot mode.

You should be able to just go into UEFI boot menu, often f10 or f12 and choose Ubuntu entry. 
Standard UEFI should have let installer set Ubuntu/grub as first default boot entry. And should allow you to change order of boot entries.
But some brands only allow by description "Windows Boot Manager" and do not allow other settings. But multiple work arounds.

What brand/mode system?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by me762 on 2017-11-17
Thanks oldfred. 
I can't seem to change the boot option anywhere, whilst it appears to be installed on the computer, it is not listed as an option in the boot menu via f12 - as requested the boot info is: [http://paste.ubuntu.com/25982210/](http://paste.ubuntu.com/25982210/)
I have no clue what it all means but if you could enlighten me and see if you can spot an issue I'd be grateful.

I have an acer aspire xc 780 desktop and came pre-installed with windows 10, currently in and ubuntu was installed in UEFI.

---

### Post by coffeefiend on 2017-11-17
May I ask what is the benefit to you of loading Ubuntu for dual boot as opposed to running a live version from a USB stick?

---

### Post by oldfred on 2017-11-17
Acer is one with a unique requirement of settings an UEFI password & enabling "trust" on the Ubuntu entry.
Some other vendors require a lot of work arounds. 

I think all of these are the same, but some explain better than others, so review a couple.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    
But I am not seeing a typical Ubuntu UEFI entry.
```
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0001,0002,0000
Boot0000  [COLOR=#ff0000]ubuntu[/COLOR]    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,30ea0e31-32b5-443d-bcfc-81644f05ddcc,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0002* UEFI: JetFlashTranscend 4GB 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(6,0)/HD(1,MBR,0x60,0x800,0x778000)..BO

```

Entries are typically more like this:
```
fred@Z170N:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0004,0003
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR]    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\UBUNTU\SHIMX64.EFI)

```

You may need to boot Ubuntu live installer in UEFI mode as you did and install Boot-Repair and run the full uninstall/reinstall of grub in advanced options.

Boot-Repair also reported this:
>  Windows is hibernated, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown 


       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by me762 on 2017-11-17
Thanks Fred,

Ok, so I turned off fast start-up first. Secondly, I re-installed as you suggested using boot repair and I have an Ubuntu UEFI entry like yours now ([http://paste.ubuntu.com/25983424/](http://paste.ubuntu.com/25983424/)). Then I tried to jump through acers hoops....
I set a supervisor password as per most of the linked threads but I do not get provided with a "Select an UEFI file as trusted for executing" option as the threads suggest. I also do not have the Insyde H2O bios, mine is called R01-A1 but I can't find any steps for this bios.

---

### Post by oldfred on 2017-11-17
I know some versions of Acer required updates to UEFI.Check with Acer's site and see if newer UEFI available for your model system.

Some old threads mention downgrading UEFI to older version, but then newer threads mentioned newest UEFI from Acer worked.
Another thread mentioned that you have to have UEFI Secure Boot on when making the UEFI trust settings. 
Generally we suggest having UEFI Secure Boot off. And if you have to install any proprietary drivers for video or WiFi you must have Secure Boot off.

---

### Post by me762 on 2017-11-18
Thanks for all your help oldfred, you sir, are a legend. I believe it is fixed so I'll post this here for your info and others:

My computer and bios (Acer Aspire XC-780 and R01.A1) does not have the " Select a UEFI as trusted for executing" option for this bios nor is it in any update for the bios. The folks over at Acer suggested adding it as an entry using EasyBCD ([https://community.acer.com/en/discussion/533615/dual-boot-win-10-and-linux/p1?new=1](https://community.acer.com/en/discussion/533615/dual-boot-win-10-and-linux/p1?new=1)). 
Unfortunately, EasyBCD doesn't have the required functionality available for UEFI as it did in the previous MBR incarnation.

So, taking suggestions from multiple places I have:
1. Disabled Secure Boot.
2. C[COLOR=#000000]hanged the default boot entry of the Windows bootloader within windows by [/COLOR][COLOR=#000000]typing the following command in an **admin** command prompt:

[/COLOR]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

In the bios I did enable the Launch CSM (legacy mode), but I have changed it back to disabled and it still works just fine.

My only issue now is, my grub loader is cluttered with options aside from the two I need: Ubuntu and Windows Boot Loader. How can I tidy it or at least reorder it so they are the top 2 entries?

---

### Post by oldfred on 2017-11-18
If you then boot into grub menu, do you then get Windows boot menu with grub again?

You can edit Ubuntu's grub menu, but should not just edit grub.cfg as it is rebuilt on every kernel update and sudo update-grub.

If you ran Boot-Repair it may have added entries in a new grub file 25_custom. If so you have edit that or turn off execute bit.

Typical menu had two kernels, recovery modes for each. Typically you may want those as if you have issues you can revert to the older kernel. And those entries are in the sub-menu.
os-prober searches for other operating systems, that adds Windows entry. Some prefer to create own entries in 40_custom and turn off os-prober.
Another entry is System Setup, which should get you into your Acer UEFI to make changes if needed.

       turn off executeable bit
sudo chmod a-x /etc/grub.d/25_custom

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 
     Ubuntu Community Documentation site
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---


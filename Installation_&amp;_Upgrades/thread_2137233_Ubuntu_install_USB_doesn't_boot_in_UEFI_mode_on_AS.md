---
title: "Ubuntu install USB doesn't boot in UEFI mode on ASUS K55N laptop"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by kylemsguy on 2013-04-20
Hello, 

I am trying to install Ubuntu 12.10 64-bit, on my ASUS K55N laptop that came with Windows 8 pre-installed. I wish to dual-boot Windows 8 and Ubuntu 12.10, but every time I try to boot the install medium (a USB drive), it freezes right after printing something along the lines of "binary trusted" if Secure Boot is enabled, or "Secure boot not enabled" when secure boot is disabled. I've tried two other distributions (Fedora 18 and Arch Linux), but it always freezes at the same place (right after some confirmation of the Secure Boot state). The only way that I've been able to boot anything other than Windows 8 in UEFI mode is if I boot it in BIOS-compatibility mode (with Launch CSM enabled). 

I've spent a long time googling for a solution to this problem, but I've only come up with people saying how this laptop refuses to boot anything other than Windows 8 in UEFI mode (for example, [http://mjg59.dreamwidth.org/22028.html?replyto=892940](http://mjg59.dreamwidth.org/22028.html?replyto=892940) or [https://lists.ubuntu.com/archives/foundations-bugs/2012-November/125271.html](https://lists.ubuntu.com/archives/foundations-bugs/2012-November/125271.html)). Personally, I've tried installing Arch Linux in BIOS-compatibility mode, and then installing an UEFI bootloader, but the boot would get stuck right after printing "Loading initial ramdisk ...," which would be about the same place in the boot sequence as with the Ubuntu install USB (that is, right after the GRUB boot screen).

The reason why I prefixed this thread with "[all variants]" is because I don't think this issue is limited to any one linux distro/flavour of Ubuntu.

If anyone has anything to say about this, or any solutions, that would be great.

Laptop specs:
ASUS K55N 
CPU: AMD A8-4500M
Graphics: Radeon 7460G (APU)
RAM: 8GB DDR3-1600
HDD: 750GB

Thanks.

---

### Post by oldfred on 2013-04-21
Boot-Repair will convert an Ubuntu install in gpt partition drive to UEFI install by uninstalling grub-pc and installing grub-efi. For a few systems that seems to be the only way to install. Some suggest only having Linux in BIOS mode but that is a real hassle as you have to go into UEFI/BIOS and change boot mode to match install.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

   Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)


 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

---

### Post by kylemsguy on 2013-04-27
I've tried installing Ubuntu in BIOS-mode, and then replacing grub-pc with grub-efi with boot-repair. I am able to boot Windows, but the ubuntu boot still freezes before loading the kernel and ramdisk.

---

### Post by oldfred on 2013-04-27
What video?
Are you booting Windows directly from UEFI, or from a grub menu?

If you get grub menu have you tried nomodeset or other boot parameters or both?
       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by kylemsguy on 2013-04-28
Booting Windows from the grub menu works. The video is the built-in radeon 7640G of the a8-4500m. I've tried nomodeset and pci=nomsi, but it doesn't work either.

---

### Post by oldfred on 2013-04-28
I do not know AMD as I have nVidia.
I thought there were some issues with the very new 7000 series. And I am not sure the links I posted above had good solutions.
Did live version boot ok?

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
sudo apt-get install fglrx
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

   [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)


 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

### Post by divine shine on 2013-05-11
Thanks for your reply oldfred. But I'm sorry to inform you that even that didn't work. Or probably I didn't know how to set it right... This is the code that I got when I pressed the 'e' key from the GRUB2 bootloader menu.
```
 setparams 'Install Ubuntu'
 set gfxpayload=keep
 linux /casper/vmlinuz.efi file=/cdrom/pressed/ubuntu.seed boot=casper only-ubiquity quiet splash --
 initrd /casper/initrd.lz 
```
and I replaced that with...
```
 setparams 'Install Ubuntu'
 set gfxpayload=keep
 linux /casper/vmlinuz.efi file=/cdrom/pressed/ubuntu.seed boot=casper only-ubiquity nomodeset
 initrd /casper/initrd.lz 
```
Is that how it is supposed to be done?? Nothing happened when I did this... I tried other combinations as deleting the ```
 set gfxpayload=keep 
``` line, etc but none worked.
Please help me. I'm desperately in need of installing Ubuntu. I Love Ubuntu and wanna use it permanently. But I don't wanna let go of my OEM Windows 8 either.

---

### Post by oldfred on 2013-05-11
Your nomodeset looks correct.

I think this is only grub, but you can change the gfx mode. But use your size.
 replace "set gfxmode=auto" by "set gfxmode=1366x768"
If you do not know sizes supported.
At grub menu change to command line

        
 From a grub command line to see available settings pressing <c> & escape to get back to meu
vbeinfo

But some systems need other boot parameters in addition to nomodeset.

 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

And some older settings, not sure they work with UEFI. Sometimes forcing generic gets it to boot.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

---

### Post by blind3d on 2013-05-11
I am having the same problem with the same laptop asus k55n,
 
I used boot-repair in legacy mode because the blank screen problem would happen trying to install ubuntu in UEFI mode, even with quiet splash disabled, the screen was not verbose and was blank.
 
After boot-repair : automatic, booting windows from grub works fine, but nomodeset does not have any effect on getting a blank screen when trying to boot ubuntu.
 
If I boot older version of ubuntu from grub, it shows loading Linux Generic...  , and then freezes after Loading initial ramdisk. 

I tried ls -l in grub <c> menu and it appears that the command list options are pointing to the correct boot partition (hd0, gpt4) , can't figure this out.

---

### Post by divine shine on 2013-05-11
In vain again. I tried putting in all the commands from the GRUB2 edit mode into the Command Line Interface, but in vain. There was some activity when I pressed <enter> after loading the kernel. But then again it went dead later.
This is the code I typed in
```
grub> setparams 'Install Ubuntu'
grub> set gfxpayload=keep
grub> set gfxmode=1366x768
grub> linux /casper/vmlinuz.efi file=/cdrom/pressed/ubuntu.seed boot=casper only-ubiquity nomodeset
grub> initrd /casper/initrd.lz
grub> boot

```
After I pressed the <Enter> key, the LED indicator on my USB PenDrive became idle and the grub refused to give me a shell (grub>). That's where I stopped. :(

---

### Post by divine shine on 2013-05-11
> **oldfred said:**
> 
•Older Intel video card: i915.modeset=1 or i915.modeset=0 newer: i915.i915_enable_rc6=1
•nVidia: nomodeset
•Generic: xforcevesa or nouveau.modeset=0

got me thinking... I have Intel HD Graphics as well. So that means it might be any of the 2 drivers conflicting with Linux or with each other.
What do I do now? I tried all these codes together < i915.i915_enable_rc6=1 nomodeset xforcevesa nouveau.modeset=0 vga=791 > separated by spaces. Still to be blocked out by the same blank black screen. :(

---

### Post by blind3d on 2013-05-11
According to another thread , I read that a guy had the same problem as this and just reinstalled the OS and ubuntu started loading fine after he reformatted...I didn't want to wipe my brand new factory install of win8, but I decided I wasted enough time and I'm trying it now. 

I found a pretty helpful guide here... and will post my results when I finish installing everything. 
[http://forums.mydigitallife.info/threads/29322-The-Official-Windows-8-Repository](http://forums.mydigitallife.info/threads/29322-The-Official-Windows-8-Repository)

---

### Post by oldfred on 2013-05-11
With Optimus, is it booting with Intel or nVidia. The very newest nVidia drive only runs nVidia, or no power savings. It may only work with the very newest kernel now in 13.10.
But you can install bumblebee. 
But I do not know how to boot initially.
Many with the very newest Intel video have to use the exact screen settings and some have to have other boot parameters.
       Force Intel Video mode as boot parameter in grub menu instead of nomodeset, but use the size that vbeinfo shows.
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by blind3d on 2013-05-11
@OP 


[http://forums.mydigitallife.info/threads/29322-The-Official-Windows-8-Repository](http://forums.mydigitallife.info/threads/29322-The-Official-Windows-8-Repository)

[SIZE=4]1[/SIZE]. install windows ISO to USB stick (in ubuntu with unetbootin [can be done in windows] )
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


[SIZE=4]2[/SIZE]. reinstall windows CFS(legacy bios mode) enabled / bios secure boot disabled

[SIZE=4]3[/SIZE]. format partitions at windows install screen manually to avoid windows from installing an extra partition 
[http://theitbros.com/how-to-avoid-reserved-or-hidden-partition-in-windows-8/](http://theitbros.com/how-to-avoid-reserved-or-hidden-partition-in-windows-8/)
(skip last part after diskpart commands about mounting iso) 


[SIZE=4]4[/SIZE]. install ubuntu (resize partitions with gparted at "something else" screen , open new terminal[ctrl+alt+t] sudo gparted, I resized my windows partition and made 2 others 1 for "/" and one for swap)

after install I didnt have grub options so i installed EasyBCD 
(added new boot option, grub2, named it ubuntu, and selected the partition)

reboot and selected ubuntu, grub loads after, select ubuntu in grub AND EVERYTHING WORKED!


notes: I did this all in the grace of asus's bios setting CSM ENABLED, which allows us to bypass UEFI all together ( a lot of manufactures dont include this), which is why the factory install has so many problems..


During the windows install never once did I need to enter a product key, and it auto activated as soon as i conntected to the net. I used to the 64 bit ISO ending in the md5 checksum of "beeec4"


also the only downfall to this is having to select ubuntu in windows bootloader first, then select ubuntu again in grub, not sure if theres a way around this , but i am happy now, after hours of trying to fix this , good luck, and always be careful when deleting OEM partitions, luckily asus rocks my socks and if id gotten another manufacturers laptop, it wouldnt have been this easy to reinstall win8 without key

---

### Post by divine shine on 2013-05-11
that didn't work either @oldfred. Nothing seems to fix my problem. :(
@blind3d : I don't wanna let go of my OEM Windows8. If that was the case, I'd never come back. I'd stay back for WWindows 7, cuz I seldom use Windows. I prefer to use Ubuntu more for everything.

---

### Post by oldfred on 2013-05-11
@devine shine
Can you boot in live mode? And what video is that using?
 LiveCD shows this:
ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 vga 

Intel HD4000
 [http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
have you tried either or both of these with the Intel or nVidia setting.
What video mode does it boot with? Intel or nVidia? That would help narrow down which settings to try.

edit
do you have the K55N? Others also have had issues booting in UEFI mode. It must not report it correctly with UEFI to system. If you have not updated UEFI/BIOS I would do that. Or you may be able to instal in BIOS mode, update video, then use Boot-Repair to convert to UEFI mode. Or you may only be able to boot Ubuntu in BIOS mode by going into UEFI and change to BIOS everything you boot Ubuntu and change to UEFI to boot Windows.

---

### Post by blind3d on 2013-05-12
@devine
I messed with it for hours, I really don't think there is a way to get it, there is something wrong with the factory install.

At first boot the laptop had 4 partitions, one for UEFI, windows 8 recovery environment, C:, and asus restore partition.

Trust me I didn't want to mess up my OEM either. The part that makes this tricky is that it's using a hybrid video card setup that is probably conflicting with booting and installing ubuntu install in UEFI mode, thus you have to install it in legacy mode, with safeboot off. 
This is bad, because when you run boot-repair, it then complains that legacy mode being detected, when you were supposed to be booted into UEFI mode all along, and nobody notices that, but that is where the problem is IMO.
You need to run boot-repair in UEFI mode in order for it to work properly, but you can't, because you cant even boot Ubuntu outside of legacy mode.

Download the ISO I mentioned  anywhere you can find it, as long as the checksum matches, it's clean. And follow the other steps and I guarantee you should have it working within  2 hours tops of burning the ISO to USB with unetbootin, and your windows8 oem will instantly be activated.

 I found this version on the ASUS website, from an ASUS member reccomending that specific version for k55n. The OEM key is built into the bios/uefi chip, so it automatically picks it up when you install this version of windows 8 from the ISO.

**Windows 8 RTM English, 64-bit (x64)**
Size: 3.33 GB SHA-1: *1CE53AD5F60419CF04A715CF3233F247E48BEEC4*


Note: It's the RTM edition for manufacturers. AKA ASUS OEM. I would get it while you can, and burn a few copies, before microsoft takes them down, they got cracked.
If you come to the descision to go through with this, private message me on here if you need help or have questions, I'll be on all day today.
(And I'm not condoning piracy, these are legit downloads on mSDN.)

---

### Post by divine shine on 2013-05-13
ok, oldfred, I finally got into the Ubuntu Live Session by disabling the Integrated NIC. But now the problem seem to have changed. Now Ubuntu doesn't seem to recognize my internal harddrive. The installer just skips the page where it is supposed to show the type of install that I might want to perform (like Install Ubuntu alongside Windows, Erase Windows and Install Ubuntu, etc), it doesn't even show whether I have another OS or not. It doesn't even tell me that I do not have another OS. Instead it directly takes me to the partitioning window where there is a table that is blank. There are no partitions to install Ubuntu on. Earlier when I logged into Ubuntu using the Legacy (CSM) mode, the installer atleast did show the partition of my PenDrive that I was using to boot into Ubuntu though it didn't seem to recognize my internal hard-drive. But this is like blank. Totally blank table. What do I do now?

---

### Post by oldfred on 2013-05-13
Moved Devine Shine to this threads. Since there may be some overlap it may be a bit confusing, but Devine Shine is a Dell and that is different than the Asus.
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

---


---
title: "System boots from USB first after boot repair"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by mohan3 on 2014-02-04
Hi,
 

 I installed Ubuntu 13.10 on my new laptop (Toshiba S55T-A5389) which had windows 8.1 pre-installed. I manually created the partition for linux and installed linux using linux USB installation disk.
 

 When I re-booted the system no boot option came up and the system booted into windows. Then I booted the system using linux USB and ran boot-repair and selected recommended repair. I selected “No” when prompted “Do you want to activate [Backup and rename Windows EFI files]?”. The URL for this boot-repair [http://paste.ubuntu.com/6870909/](http://paste.ubuntu.com/6870909/)
 

 The system again didn't display boot option and booted into windows.
   
 I again ran boot-repair and this time selected “Yes”when prompted “Do you want to activate [Backup and rename Windows EFI files]?”. The URL for this boot-repair [http://paste.ubuntu.com/6870949/](http://paste.ubuntu.com/6870949/)
 

 When I rebooted the system the initial screen which displays Laptop logo displayed error messages “Invalid image, Failed to read header, Failed to load image” as in the screenshot attached. These messages appear irrespective of secure Boot setting. When I took picture luckily I could capture some more error message as seen on the screenshot.
 

 After 2 seconds the system displays second screen where it says “Press F2 to enter setup. Press [F12] for boot menu”. If I press F2 or F12 nothing happens. After displaying this screen for 10 seconds, the system boots from linux USB if the USB is plugged in. (The BIOS setting has HDD as first boot option). If the linux USB is not plugged in, then a third screen which says “>> Checking Media Presence... >>No Media Present” is displayed. After displaying this screen for 15 seconds the system finally displays the GRUB boot menu. Then I am able to boot into Ubuntu or Windows from there.  All the above screens are displayed irrespective of BIOS secureBoot setting. Ubuntu bootup proceeds normally only if secureBoot setting is enabled (Both for booting from HDD and booting from USB). If I have the secureBoot disabled, Ubuntu boot hangs, even if I try secure boot option the system hangs after displaying “Loading initial ramdisk”. With secureBoot enabled I am able to boot normally.  

 

 I don't know why the system displays error messages as soon as started. Also the system always try to boot from USB first even though booting from HDD is the first boot option in BIOS. Only if the USB is not present system displays GRUB boot menu. Please help me in getting this resolved. 

Thanks.

Initial bootup screen
[ATTACH=CONFIG]250103[/ATTACH]

---

### Post by oldfred on 2014-02-05
Edit
 Could not open "\EFI\BOOT\fallback.efi" see #4 for a work around by renaming grub file.
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)



From line 921
Please disable SecureBoot in the BIOS.

It looks like you still have secure boot on. But also have Ubuntu installed with secure boot so it may boot.
Did you also turn off fast boot?

Also you should undo the rename. That is only for systems that only boot Windows.
Only if we find that system will not let Ubuntu boot at all, then we may need rename.

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Other Toshiba's, you may also need the video parameters
       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by mohan3 on 2014-02-05
Thanks Oldfred for providing me direction.

 Yes, I have the Fastboot disabled. If I disable secureBoot Ubuntu boot-up hangs once I select ubuntu from Grub menu. Ubuntu boots up fine only when secure boot is enabled.

 I am able to make some progress by making following changes.

 Copied grubx64.efi file to boot folder.
 >> cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Boot/
 This solved the problem of system booting from USB first always. This also get rid of the error message &#8220;Failed to open grubx64.efi&#8221;. Now the system displays initial screen (with load image failed error message) and then goes directly to grub menu.
 (Boot repair has copied shimx64.efi as bootx64.efi in /boot folder and it appears like shimx64 tries to load grubx64.efi from the same folder it is present)

After this I copied grubx64.efi file to boot folder as fallback.efi.
 >> cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Boot/fallback.efi
 With this, the error message &#8220;Could not open fallback.efi&#8221; is gone.
 
 Now, when I start the system, it displays &#8220;Invalid image, Failed to read header, Failed to load image&#8221; on initial screen  for two seconds and then takes me to the Grub menu. I am able to boot ubuntu or windows properly (with secure Boot enabled).  

I don't know how to get rid of the error messages &#8220;&#8220;Invalid image, Failed to read header, Failed to load image&#8221;. I guess these error messages are caused by shimx64.efi, but I am not sure.

---

### Post by oldfred on 2014-02-06
I do not know if those are grub errors or UEFI errors which may be something the vendor has configured.

It may be trying to load grub, give error message and then loads fallback?

Have you tried with secure boot off? But UEFI on. And perhaps Legacy/BIOS/CSM on, but still booting in UEFI mode?

---

### Post by mohan3 on 2014-02-07
The error message appears even if I turn off secureBoot. My firmware do not allow me to boot me in non UEFI modes.

The fallback I created is copy of grubx64.efi. So, I don't think the error messages are due to grub. 

I have shimx64 as the initial efi file (i.e. shimx64 is copied as bootx64 by boot repair). If I try to copy grubx64 as bootx64 and turn off secure boot then no error messages are displayed. I get grub menu but Ubuntu won't boot up with secure boot turned off. If I turn on secure boot then I get signature issue as expected and grub won't load. So, I guess the initial error messages has something to do with shimx64/UEFI.

---

### Post by oldfred on 2014-02-07
I thought the secure boot version of Ubuntu would also boot with secure boot off? But do not know for sure.

With Boot-Repair or manually you can install the standard kernels and use grub to boot not shim. I also thought they made shim the standard grub to be used with all UEFI installs.

---


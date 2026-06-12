---
title: "UEFI Installation - HP Envy X2 PC"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Konvit85 on 2013-04-18
Computer: HP Envy X2 PC
Product Number: c7n83av
Processor: Intel (R) Atom (TM) CPU z2760 @ 1.8GHz
Total Memory: 2GB
Bios Version: F.07
Bios Vendor: Insyde

I am trying to install any Distro of linux that will work. I would like to get linux on in order to get full use of the hardware. Win8 has a tendency to slow down a lot after a few hours of use sue to not closing programs but instead moving them to the background.

I have tried installing Ubuntu 12 and Fedora18 both of which claim EFI support. out of the two Ubunut was hte only one to even get close with showing a dual boot screen. however when i select Ubuntu to try and finish the installation (using a efi boot image from USB) it reverts to the windows boot manager and fails to load.
if i try to boot directly from the usb or cd neither are recognized in the advanced boot options.
I was only able to get the Ubuntu dual boot to show by installing the Help me boot option from the usb prior to rebooting.

I have been tryng everything i can think of over the last 3 days and am at a brick wall here.

Secure boot has been disabled and enabled on multiple attempts with no change.

I suppose my questions is this, has anyone been able to get a Distro to work on this model of laptop/tablet hybrid?  if so how, any ideas on how to get this to work would be greatly appreciated.

if you need anything from me just ask. I will be on here for a while.


-Konvit

---

### Post by oldfred on 2013-04-18
This user seemed to get it to work and fixed a wireless issue also in this thread.

 Installing Ubuntu on HP Envy-6 
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by Konvit85 on 2013-04-18
I attempted to install the x64 ubuntu 12 and am able to get to the load from EFI menue. when i select bootx64.efi it returns an error "the selected boot device failed.
when i select Grubx64.efi it returns an error" device not authorized. if i secure boot off then try grubx64.efi it also returns "selected boot device failed.
those are the only two options for efi boot listed on the dvd.

this tablet/laptop hybrid also does not have the option for legacy bios. so most of the steps from the evny pages do not work.

---

### Post by oldfred on 2013-04-18
It should boot the grubx64.efi with secure boot off. If you have not updated, you need the signed versions of grub2 with shim and signed kernel and then you should be able to boot in secure boot mode. I think then shim gets renamed to grubx64.efi.

Boot-Repair will also add the correct chain load entries from grub menu to Windows. And it renames Windows to be a backup and makes shim the Windows efi boot file.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by Konvit85 on 2013-04-18
I am making the boot repair disc now and will try to run that. my problem is that my desktop is running windows and the only way i have to run linux is through VMware. so making boot iso or efi boot devices is rather hard since everyone keeps giving the linux commands on how to do it.  I will let you know after i run the boot repair tool if that helps. if Win8 will even let me run it.

---

### Post by Konvit85 on 2013-04-18
stilla no go. the system will not boot from the cd even though it shows it is reading it at startup. nothing will load and after a few moments it reverts back to windows 8

---

### Post by oldfred on 2013-04-18
I do not know vmware and am not sure if it works with UEFI or is it really just another BIOS type system. But UEFI writes system data to hard drive differently than BIOS, so it needs to be UEFI capable.

---

### Post by Konvit85 on 2013-04-18
well i was finally able to get Ubuntu 13 to load. and install. however once it rebooted it gave an error in the the following file:  \ubuntu\winboot\wubildr.mbr
status: 0xc000007b

so now i need to attempt to run a boot repair tool from windows.

---

### Post by oldfred on 2013-04-18
Wubi does not work with gpt partitioned drives (All Windows 8 pre-installed with secure boot UEFI)  and has to be installed from inside Windows for MBR based systems.

---

### Post by sudodus on 2013-04-19
> **Konvit85 said:**
> well i was finally able to get Ubuntu 13 to load. and install. however once it rebooted it gave an error in the the following file:  \ubuntu\winboot\wubildr.mbr
status: 0xc000007b

so now i need to attempt to run a boot repair tool from windows.

Since you were able to load and install Ubuntu 13, I guess 13.04 (Raring beta) 64-bit version, you have the option to run linux and use the linux tools, when you boot from the Ubuntu 13.04 boot CD/DVD/USB drive. I don't know if Boot-Repair is available for 13.04, because it is still in the beta stage, but it is worth trying, if 12.10 won't boot in your computer. You need the 64-bit version.

---

### Post by pnoq on 2013-06-21
> **Konvit85 said:**
> well i was finally able to get Ubuntu 13 to load. and install. however once it rebooted it gave an error in the the following file:  \ubuntu\winboot\wubildr.mbr
status: 0xc000007b

so now i need to attempt to run a boot repair tool from windows.

Hey Konvit85,

I'm also trying to install Ubuntu on my HP Envy X2 but I can't even load and install it.
Please, can you tell how you did that?

Regards
pnoq

---

### Post by DrR2 on 2013-06-23
HP Envy X2 Owner

Numerous failed attempts to install Ubuntu 13.04 (and Lubuntu and Mint)
Waiting patiently for
Link to best instructions?
Thanks

---

### Post by oldfred on 2013-06-23
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Also see link in my signature for lots of general info.

---

### Post by darthrivius on 2013-10-15
Hello, i have the same problem as author of this topic, i have envy x2, author run ubuntu well but he didnt write how he did that, anybody can help? i have usb pendrive with ubuntu x64 efi, if i turn on envy its start booting windows 8, when i tried to boot from efi i have error with device failed when i have security boot disabled, when i have enabled i have error with authorize. someone here told to make grub2 with shim signed but i dont know how to do that

---

### Post by oldfred on 2013-10-15
If you boot UEFI installer with secure boot on, then it installs in secure boot mode. How you boot installer - UEFI with secure boot, UEFI (without secure boot), or CSM/BIOS/legacy is how it installs.
You can boot installer with secure boot  and then install Boot-Repair. It will run the commands to install the signed kernel & grub to enable booting with secure boot on. Then you do not have to reinstall, or you can just reinstall.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Original post was with wubi, which does not work with gpt partitioning which is used with UEFI.
You also may have issues with video modes and need nomodeset or other settings for Intel systems. See link in my signature for more info.

---

### Post by darthrivius on 2013-10-15
ok i tell you what ive done and tried.

hp envy x2 is 32bit, so first i tried boot from ubuntu 32bit 12.04, 13.04, 13.10, secure ubuntu. then i realize then i need efi so i tried use ubuntu x64 the same kind what before.
i use two options

1. I have secure boot DISABLED, im putting ubuntu on usb stick, and plug in but windows 8(i have boot first set from usb) boot instead ubuntu, so i run uefi and from menu i choose boot efi file, i select grubx64.efi and i see error "the selected boot device failed", and the same error when i tried select BOOTx64.EFI.

2.I have secure boot ENABLED, im plug in my usb stick with ubuntu, windows 8 boot instead ubuntu, the same like before i choose uefi, then select boot from efi i select the same files and i see[COLOR=#000000] "device not authorized"

now i tried run boot repair disk and is the same. 

so what can i do now? [/COLOR]

---

### Post by oldfred on 2013-10-15
If it is a secure boot system with UEFI, it is not 32 bit. 
All UEFI systems are 64 bit and currently no Windows nor Ubuntu has 32 bit versions that work with UEFI. There actually are major driver issues if attempting to use 32bit with UEFI, so no one has implemented it.
You need to download and use a 64 bit version of Ubuntu.

---

### Post by darthrivius on 2013-10-16
yeah i noticed that so i try use ubuntu x64 but it didnt even boot, as i wrote above your post

---

### Post by oldfred on 2013-10-16
Not Authorized is Secure boot is still on.
Both UEFI and CSM will boot with secure boot off.
But flash drive has to be correctly configured with unetbootin or other installer that both extracts ISO and then makes flash drive bootable.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by darthrivius on 2013-10-16
ok made bootable usb with unetbootin, i try it on my normal laptop and it boot normal. then i tried it on my hp envy x2 and nothing, even when i tried it from efi menu and choose efi file i got device failed error 
any advice?

---

### Post by oldfred on 2013-10-16
You need to install in UEFI mode, but does it boot in CSM/BIOS mode? From UEFI menu you should get two boot options if secure boot is off.
If secure boot is on, Ubuntu still should boot in UEFI mode as it has Microsoft signing key. Only signed bootable systems will boot if secure boot is on.

Have you updated UEFI/BIOS from vendor. They also have issues with UEFI and are doing major updates.

---

### Post by darthrivius on 2013-10-17
there is no legacy bios, bios mode/csm . only uefi i have secure boot disabled i updated my bios from vendor to firmware f.10 its newest, but i sill cant boot ubuntu or any other distro, even to grub :X
from efi menu i have two options : "os boot manager", "choose efi file to boot" , when i choose efi file, grubx64.efi i have error with failed boot as i wrote few post above.
i guess there is no hope to run ubuntu on my envy :{

---

### Post by darthrivius on 2013-10-17
okey, i made some progress, maybe its wird but it is 32bit uefi, i make usb stick with refind bootloader which support 32bit efi, and its work but how should i run ubuntu now? i need ubuntu 32bit to run in efi which it doesnt support, but maybe i can make my own live cd with ubuntu 32bit efi? or its not possible?

---

### Post by oldfred on 2013-10-17
You probably are in BIOS mode. Some have to install the 64 bit in BIOS mode and use Boot-Repair to convert to UEFI mode.

I do not think UEFI even works in 32 bit mode.
 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

---


---
title: "Confused about bootloader locations offered during installation"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by Marrea on 2014-08-01
Having set up a number of computers in the past to dual-boot Windows and Linux, I recently decided to buy an HP laptop (model 15-N299SA) pre-installed with Windows 8.1, specifically for the purpose of learning how to do the same with an UEFI system.  With hardly any knowledge of UEFI as yet I have managed to set up a Windows 8.1/Ubuntu 14.04 dual-boot, although not quite in the way I would have liked and am therefore seeking guidance on the nuances of the Ubuntu bootloader location options as nothing I have read so far seems to go into any detail on this point.

My partitions (according to gparted) are as follows:

/dev/sda
free space
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sda6
/dev/sda7
/dev/sda5
free space

sda1 is the Windows Recovery partition, sda2 is the EFI partition, sda4 is the Windows (C) partition and sda5 is the HP Recovery partition.  sda6 is the Ubuntu root partition and sda7 is the Ubuntu swap partition.  I think sda3, which gparted marks as “unknown”, may be the Microsoft Reserved Partition (MSR) although I am just guessing that.  I created the Linux root and swap partitions from unallocated space I had created between the Windows (C) partition and the HP Recovery partition beforehand in Windows Disk Management.

The Ubuntu installer showed the default bootloader location as /dev/sda.  I changed this to /dev/sda6 (Linux root), hoping that this would enable me to use the Windows bootloader (via EasyBCD) to boot both Windows and Ubuntu.  This is what I have always done in the past with my Windows 7/Linux dual boots.

When I rebooted after installation had completed, I was surprised to find the laptop booted straight back into Ubuntu - not Windows, as I had expected.  Nearly every article I have read about dual-booting Windows and Linux on an UEFI system states that the computer will boot straight back into Windows and then gives details about how to fix this so that grub can take control of the booting.  Well, by putting grub on Ubuntu’s root partition I seem to have succeeded in making grub the default (although this was not my intention) without any further steps!

I have read that the EFI system partition (ESP) contains the boot loader programs for all operating systems installed on the device. Therefore I am assuming that grub must be on the ESP, and not on Ubuntu’s root partition.  Is this correct?  So even though I selected /dev/sda6 during installation, Ubuntu ignored this and put grub on sda2?  If I had left the default bootloader location as /dev/sda, would this have resulted in grub being put on the ESP partition?

I am finding all this very hard to get my head round and would be extremely grateful if someone could explain to me what the consequences are of selecting various different bootloader locations during installation.

---

### Post by sudodus on 2014-08-01
The active bootloader is in the head of the drive, **/dev/sda** for the first drive (without a partition number). It may link to a bootloader in a partition, but it is not recommended. You can even write the bootloader to a partition, because you do not want to touch the current bootloader, that points from the head of the drive to some other partition with another distro. See this link

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Things are more complicated with UEFI, and a simple work-around or clean-up is to use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") afterwards to make things work. The following link describes the situation with many tips and links.

[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")

---

### Post by oldfred on 2014-08-01
BIOS based computers only boot from the MBR unless you have another boot loader in the MBR and then can (but not really recommended) have that boot loader chain load to another boot loader in the PBR or partition boot sector. Each drive has only one MBR, so only one system controls boot.
Grub does not fit into PBR and converts to blocklists or hard coded addresses. If any part of grub moves on drive by update or even fsck then it will not work has to be reinstalled to PBR.
Windows boot loader only boots other Windows so you have to use third party tools like EasyBCD which is really using grub4dos to do chain load.

With UEFI you do not need EasyBCD as all systems put efi boot files into separate folders in efi partition and you can choose from UEFI menu or one time boot key like f12 to choose which system to boot. Grub also will chain load back to the efi partition to boot Windows. The installer knows with UEFI you only need or want efi boot files in efi partition, so it does not install to partitions.

But new UEFI systems also have CSM or BIOS Mode. If you turn on CSM/Legacy/BIOS mode then system will only boot Ubuntu and grub cannot boot Windows in UEFI mode. UEFI & BIOS are not really compatible so grub can only boot systems installed in same boot mode. To dual boot with systems in different modes you can only choose different system from UEFI menu and may have to turn on UEFI or turn on CSM mode. Some auto switch or recognize how installed and you can use one time boot key to boot.

Boot-Repair often is not now needed to fix installs as grub finally installs os-prober correctly for UEFI installs. But it has a good report tool that lists lots of details of your install. It also can convert a BIOS install to UEFI by changing grub version and make other repairs. It cannot do much for Windows and you need a Windows repair CD or flash drive to fix most Windows issues.

Post link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

IF dual booting with Windows only install Ubuntu with Something Else. The auto options are not clear and usually totally overwrite entire hard drive erasing Windows. With Something Else you totally control partitions, so that works. 
Also then you need really good backups of Windows, efi partition, recovery partition and configuration. Boot-Repair report is a good way to understand partitions and configuration.

---

### Post by Marrea on 2014-08-02
Thank you **sudodus** and **oldfred** for your input and the various links.  I am most grateful.  There is a lot of reading for me to do, I think!

Strangely, up until today my laptop was booting straight into Ubuntu.  But when I switched it on this morning, it booted into Windows. I have turned it off three or four times during the day and on each restart it has continued to boot into Windows.  No problem really, as this is what I had been trying to achieve originally, and I can still get into Ubuntu easily enough with the one time boot option.  I am puzzled though why the default boot has apparently changed.  I have certainly not done anything myself to change it.

I have managed to install Boot-Repair, which took a bit of research on my part as I discovered there is no version for Trusty as yet.  This was purely for the purpose of obtaining a Boot-Repair report, the URL for which is [http://paste.ubuntu.com/7933676](http://paste.ubuntu.com/7933676).   It doesn't mean much to me at the moment but I thought perhaps if you had a look through it you might be able to advise if everything looks OK,

---

### Post by ubfan1 on 2014-08-02
Looks like you have a working secure boot setup.  If you find you cannot acutally boot Windows from the grub menu (it should be an entry in the menu), you probably can make that work by turning off secure boot.  The boot order seems to frequently get changed, usually by Windows but maybe by just the firmware also, so your solution of using the efi menu to choose ubuntu is a good one.

---

### Post by oldfred on 2014-08-02
In your report it shows that UEFI is set to boot Windows first. I think Windows 8 resets itself to first after any maintenance and Windows 8.1 always resets itself to first.

Line 482 shows the output of this which you can also run from Ubuntu terminal:

sudo efibootmgr -v

---

### Post by Marrea on 2014-08-03
**ubfan1** and **oldfred**

Many thanks for your comments.  

I do indeed have secure boot enabled.  All I had to do to get Ubuntu to install originally was to turn off fast startup.  I didn’t need to disable secure boot and/or enable legacy mode.

In addition to Windows having now apparently set itself as the default operating system I can also boot into it from the grub menu, and I can boot Ubuntu using the one time boot method, which on my HP laptop is accessed by pressing F9 from the Startup Menu.  So I have all scenarios covered.

I have marked this thread as solved as I am happy with the way the laptop is currently set up.  It is now down to me to study as much documentation as I can find about this subject so I have a much better idea of how it all works. 

Thank you again for your help.

---

### Post by oldfred on 2014-08-03
Many with HP and Sony systems do a work around. It seems that you may be able to set hard drive as first in boot order and Windows may not overwrite that.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

Many like the copy of grub or shim into /efi/boot and rename it to bootx64.efi. Then boot hard drive.
      
 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )


 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by Marrea on 2014-08-03
> **oldfred said:**
> It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu.

Yes, you are right.  There is no option in my UEFI Boot Order to boot Ubuntu.  My UEFI lists the following:

OS boot Manager
Internal CD/DVD ROM Drive
USB Diskette on Key/USB Hard Disk
USB CD/DVD ROM Drive
1 Network Adapter

However, I am quite happy using the method you mention above, ie F9 and then selecting Ubuntu.  That works quite quickly and suits me.  Being so new to UEFI, I am naturally hesitant about tinkering with settings at the present time in case I mess things up completely!

---


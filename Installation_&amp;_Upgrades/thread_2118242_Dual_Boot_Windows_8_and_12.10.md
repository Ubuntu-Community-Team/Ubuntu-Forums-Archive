---
title: "Dual Boot Windows 8 and 12.10"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by fosser2 on 2013-02-20
Hey guys,

I am new to these forums and would really appreciate the help. What I am attempting to do is dual boot Windows 8 (x64) and Ubuntu 12.10 (x64) BOTH with uefi support. I would also like to be able to use the Windows 8 graphical boot manager to be able to select either Windows or Ubuntu. I have gotten both os's booting using Grub2 so I know that is an option but that is not the way I want it done. I do not have secure boot enabled and when I install Ubuntu the following screen does show up.
[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

According to this [page]("https://help.ubuntu.com/community/UEFI") this means it will be installing in UEFI.

While installing a "fresh" copy of Ubuntu the first thing that is a bit weird to me is the fact that the Ubuntu installer does not detect Windows 8 at all. Possibly this is due to the fact that Windows 8 is installed in UEFI, I'm not sure. This is what I see upon starting the Ubuntu installation.

(first attachment)

Currently I have uninstalled Ubuntu and allocated free space on my HDD. The following picture represents my partition layout currently. From what I've read Ubuntu and Windows can share the EFI partition that Windows created. Out of that unallocated space I need to create a 4GB swap (primary) and the rest ~150GB ext4 (primary). I am unsure where the bootloader is supposed to be mapped. I have tried both putting it on "/dev/sda ATA ST320LT007-9ZV14" and I have attempted putting it on "/dev/sda6" (sda5 being the swap partition).

(second attachment)

Thank you guys in advance for the help. I'm sure there are more people out there wondering how to go about this.

---

### Post by oldfred on 2013-02-20
Please attach screen shots with the paperclip icon. Some of your screen shots are large.

Is this an UltraBook? That uses RAID and the desktop installer does not have RAID drivers. So then it has issues seeing drives. Also if Windows 8 is hibernated (and it also is unless you turn it off). Do not attempt to install if Windows is not seen, some have and totally erased Windows. 

Have you backed up efi partition and the entire Windows partition?

What model PC is this?

Have you turned off secure boot to install and turned off fast boot?

You install the grub efi boot loader to the efi partition if installing in UEFI mode. Old BIOS mode always installs to MBR. I think with UEFI it defaults to the efi partition.

I suggest a smaller / (root) of 25GB and the rest as /home or better still some of the space as a shared data partition formatted as NTFS. Windows and particularly Windows 8 does not like too much activity in the system partition. 

How you boot Installer is how it it installs. So if you boot flash/DVD  from UEFI in UEFI mode it will install in UEFI mode.

Some systems will not install in UEFI mode, some will not install in secure boot mode. Some will not boot anything else other than Windows efi file.

Boot-Repair does several work arounds for some of the issues. It can rename the Windows efi file and put the shim which has the Windows UEFI key as the Windows boot file. Then most will boot that, give a grub menu and grub then can chain load back to the renamed Windows file.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
Grub also has a gub where it does not create correct chain load entries to Windows.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---


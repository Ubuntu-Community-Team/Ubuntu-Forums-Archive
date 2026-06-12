---
title: "Trouble dual booting Xubuntu 12.04.3 and Windows 8"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by DiscoDave95 on 2013-10-15
I was able to install and partition Xubuntu correctly. However when i reboot my computer, i goes right into windows 8 and not grub. If i go to the boot order however and select the notebooks harddrive, then it will boot into grub. How can I fix this so I can have the option for both windows 8 and xubuntu on the same screen? 

I am using Xubuntu 12.04.3 and Windows 8 on a 64bit HP Pavillion (15e072nr)

Any help would be much appreciated :)

---

### Post by ubfan1 on 2013-10-15
Install efibootmgr and you should be able to change the boot order to put Ubuntu (grub) first.  Then you can select Ubuntu or Windows (provided your computer will boot windows from grub (bug 1091464).

---

### Post by DiscoDave95 on 2013-10-15
To be more specific I am using Grub 1.99-21ubuntu3.10; I have also attempted and failed to configure a dual boot with EasyBCD.

I had Xubuntu added as so..

[IMG]http://img443.imageshack.us/img443/3712/2zjb.png[/IMG]

[IMG]http://img812.imageshack.us/img812/4240/h7lz.png[/IMG]


However when i select Xubuntu in the Windows Boot Manager on startup, I'm presented with this error:

File: \NST\AutoNeoGrub2.mbr

Status: 0xc000007b
and then in the info it says the file could be corrupted  or missing.

I am only able to get into Xubuntu by hitting esc on startup, then pressing f9 (Boot Device Options). This presents me with three options: OS Boot Manager, Boot from EFI FIle, or Notebook Hard Drive. If i were to select the last option, Notebook Hard Drive, it will load grub successfully. The grub looks normal and has xubuntu and windows 8 listed, selecting the xubunu option works fine however windows 8 does not. 

When selecting Windows 8 from grub I get this:

[IMG]http://i44.tinypic.com/o9er2g.jpg[/IMG]


More specifications about my laptop can be found here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03771835&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03771835&cc=us&dlc=en&lc=en)

If there is any more information I should give regarding my laptop, hardware or software, or whatever, please let me know :)

I appreciate anyone that can offer any helping words of wisdom

---

### Post by DiscoDave95 on 2013-10-15
> **ubfan1 said:**
> Install efibootmgr and you should be able to change the boot order to put Ubuntu (grub) first.  Then you can select Ubuntu or Windows (provided your computer will boot windows from grub (bug 1091464).

Too be honest I just installed efibootmgr and googled just for a few minutes about it and its way over my head. I'm not quite sure where to start and how to work this. Shouldn't there be some way that I could have the 'Xubuntu' option in the Windows Boot Manager point to grub, kinda like how Wubi would do it?

---

### Post by oldfred on 2013-10-15
With the new UEFI systems, you can install in UEFI mode with secure boot, UEFI mode (without secure boot) or in BIOS/CSM/legacy boot mode.
It seems like Windows is in UEFI mode and Ubuntu in BIOS mode. You can not easily dual boot as UEFI and BIOS are not compatible. How you start to boot must be the same.

Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI) or if booted in secure boot mode it can also install the secure boot signed kernel & grub versions.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by DiscoDave95 on 2013-10-15
Thank you so much for the responses and help, I apologize in advanced if i seem a tad 'nooby'


Here is the boot info: [http://paste.ubuntu.com/6241804/](http://paste.ubuntu.com/6241804/)

---

### Post by oldfred on 2013-10-15
You have grub in BIOS boot mode with bios_grub partition and grub boot loader installed in protective MBR. If you go into UEFI/BIOS and turn off UEFI or turn on CSM/Legacy/BIOS it should boot Ubuntu. But then to boot Windows you have to go back into UEFI/BIOS and turn on UEFI to boot Windows. Not the easiest way to dual boot.

Boot-Repair suggests uninstalling grub-pc and installing grub-efi. Then you will be able to boot Ubuntu in UEFI mode and it should add an entry to boot Windows from grub menu in UEFI mode. Grub2's os-prober still has a bug and creates incorrect boot entries, but the one's Boot-Repair adds will work.

> EFI detected. Please check the options.
=================== Advice displayed in case of recommended repair
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?
=

---

### Post by DiscoDave95 on 2013-10-15
> **oldfred said:**
> You have grub in BIOS boot mode with bios_grub partition and grub boot loader installed in protective MBR. If you go into UEFI/BIOS and turn off UEFI or turn on CSM/Legacy/BIOS it should boot Ubuntu. But then to boot Windows you have to go back into UEFI/BIOS and turn on UEFI to boot Windows. Not the easiest way to dual boot.

Boot-Repair suggests uninstalling grub-pc and installing grub-efi. Then you will be able to boot Ubuntu in UEFI mode and it should add an entry to boot Windows from grub menu in UEFI mode. Grub2's os-prober still has a bug and creates incorrect boot entries, but the one's Boot-Repair adds will work.

Is this is as easy as going to snyaptic unchecking grub-pc and installing grub-efi? 

edit: I did already have legacy enabled in my bios

---

### Post by oldfred on 2013-10-15
I think that is exactly what Boot-Repair does. But it also adds correct Windows efi boot stanza to 25_custom. Not sure if the switch of grub-pc to grub-efi automatically updates fstab to include efi partition or not.
Of course once you change you have to change UEFI to boot in UEFI mode not BIOS mode.

---

### Post by DiscoDave95 on 2013-10-15
> **oldfred said:**
> I think that is exactly what Boot-Repair does. But it also adds correct Windows efi boot stanza to 25_custom. Not sure if the switch of grub-pc to grub-efi automatically updates fstab to include efi partition or not.
Of course once you change you have to change UEFI to boot in UEFI mode not BIOS mode.

So you are saying my best bet is to run the boot-repair from the live-usb I made to generate that boot-info?

Thank you btw :)

---

### Post by oldfred on 2013-10-15
You can do everything manually if you want.

---

### Post by DiscoDave95 on 2013-10-15
Oh dear...

I ran the repair-boot on the live-usb. Then I turned off legacy in the bios, and now the computer says disk failed to authenticate image, i hit okay and the laptop turns off.

---

### Post by DiscoDave95 on 2013-10-15
Oh wow nvm, i got it working perfectly now, thank you :)

---

### Post by martinr on 2013-11-09
A new install worked more quickly for me.

Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR or vice versa.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

What did your HD structure turn out to be?

---


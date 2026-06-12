---
title: "Alongside Windows - Doesn't detect Windows 8"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by Dominus123 on 2013-04-11
I was about to install Ubuntu on an EFI laptop. I have dual boot Windows 7 and 8...although 8 I installed later and 7 came pre-installed.

Anyway Ubuntu only detects Win 7 in the alongside install option...am I right to suspect that I will not be able to boot into Win 8 after install? Or will Grub allow me to boot Windows 8 in Windows 7 boot-loader, even though it will not have a separate entry for Win 8?

I ask this because on non-EFI machines when I have had dual windows booting, Ubuntu has detected '2' operating systems.

Also will I need to create an EFI partition, or is there no need for it when installing along with windows?

P.S. I think Ubuntu should work on the Wubi windows installer to make it successful on EFI machines, it is a nicer way for Windows users to install Ubuntu.

---

### Post by oldfred on 2013-04-11
Are your Windows installs in BIOS or UEFI mode. Ubuntu need to be installed in the same mode. Or else it becomes very difficult to dual boot.

If UEFI all systems use the same efi partition. But grub will only find one Windows entry to chain load into.
With BIOS you normally only get one Windows entry as Windows moves its boot files from second install to first install unless you make second install active (boot flag) partition.

Post this from liveCD/DVD/Flash installer's terminal:
       sudo parted /dev/sda unit s print

---

### Post by Dominus123 on 2013-04-11
Hi, thanks for the reply and information.

My windows installs are in UEFI mode. I assume using a 64-bit Ubuntu DVD automatically installs it in UEFI mode as the BIOS shows the disc as "UEFI: TSSCORP CD/DVD etc.."

Windows uses the same UEFI partition, and Windows 8 bootloader becomes the default for booting into either OS.

I am a bit confused as to what mount I need to choose for my Ubuntu partition i.e '**/**' (which I have used in the past on non-EFI) ; ***/boot*** OR ***/boot/efi***. The Ubuntu site says if you choose to install along with Windows no need to do anything further, which doesn't seem right to me as I still need to format the partition I created for Ubuntu as well as choose its mounting system and choose where the GRUB bootloader will go...not exactly a walkthrough. (Hence why I recommend they make an EFI working wubi windows installer).

Finally, is it better to install GRUB on the same partition I have created for Ubuntu or this will not work on UEFI booting systems?

---

### Post by oldfred on 2013-04-12
With UEFI the grub boot loader is installed to the efi partition. With UEFI it should default to the efi partition, but I think the install may not have been updated over BIOS and offer selection?? You can only have one efi partition per hard drive.

The efi partition is the replacement for the MBR and just has a part of grub or other boot loaders. But because it is larger the bits of grub you never saw that were core.img in the sectors after the MBR are also in the efi partition. It is like having many MBRs as every install creates a folder for its boot files.

You can create a /boot partition but I normally do not suggest it for most desktop installs. I do prefer smaller / (root) of 25GB and separate data or /home partition(s).

---

### Post by Dominus123 on 2013-04-12
Thanks again, I must admit that I don't understand how this efi partition works. BIOS shows a Windows boot Manager (WBM), so after installing Ubuntu, Ubuntu will usurp WBM and become the default boot option in BIOS. By creating this efi partition for Ubuntu does that mean I will lose WBM and if something goes wrong with Ubuntu or I lose access to my windows OS, than probably I have to run Windows startup repair to enable WBM?

I see no issues with creating an efi partition for Ubuntu as long as nothing happens to WBM i.e it is not deleted from BIOS. That way if I cant access Windows via GRUB, and I have trouble fixing it than I should be able to simply change BIOS back to WBM and Windows will return of course meaning I wont be able to use Ubuntu.

---

### Post by Dominus123 on 2013-04-12
Clearly it is not as simple on UEFI as I would like but all I want to do is this: 

- System able to boot win 8 / 7 and ubuntu
- Don't care which boot loader handles it but I want windows 8 to be the default
- I have to many things installed in Windows to do any formatting and "Start again" just to get Ubuntu working
- I have four partitons on my HD : Windows 7, Windows 8, Data Partition and a 20gb partiton I want to install ubuntu on, probably using 6gb of this as swap space (BTW, I have 12gb RAM so is swap space even necessary?)

---

### Post by oldfred on 2013-04-12
One advantage of UEFI is that installing grub does not overwrite the Windows boot loader. From UEFI menu you can choose to boot any install in the efi folder.

One disadvantage of the new secure boot systems is that some vendors have modified UEFI code to only boot the Windows efi file which is not per UEFI "standard". Then we have to have work arounds renaming Windows files to be grub files. If you do not have secure boot you will not have that issue.

Where with BIOS/MBR grub chainloaded to the part of Windows boot in the partition boot sector(PBR), with UEFI it chainloads back to the Windows efi file in the efi partition. More like having Windows on separate drive and chainloading to the MBR of the Windows drive.

Grub will give you a menu to boot both Ubuntu & Windows. Windows is not designed to multi-boot. You can set Windows as default in grub or manually go into UEFI menu and choose. You also should have a one time boot key, and besides hardware devices it should show the efi entries. 

But there is a bug and you have to update chain load entries in grub. Boot-Repair will do it automatically or use examples in bug report.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

You should also back up efi partition. But UEFI remembers entries and would have to be refreshed if you restored older efi entries.

Windows also has its BCD that controls Windows boot entries in the efi partition. You can problably edit it to make Windows 8 the default. You may be able to create an entire duplicate of the Windows efi folder with slight folder name change,  and edit one to be Windows 7 and the other Windows 8 in BCD.

---


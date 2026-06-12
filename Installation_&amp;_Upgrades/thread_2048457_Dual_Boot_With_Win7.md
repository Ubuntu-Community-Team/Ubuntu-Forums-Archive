---
title: "Dual Boot With Win7"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by JKyleOKC on 2012-08-26
I'm having a problem setting up a dual boot of Xubuntu 12.04.1 and Win7 on my new HP P2-1120 machine. I shrunk the Win7 installation to get 228 GB of free space, and since the system uses UEFI to boot via GPT, there's no limit on primary partitions. Xubuntu seems to have installed properly (as seen from the Live CD), although the "how-to" that I followed had me create a separate /boot partition and change the bootloader location to the resulting /dev/sda5. I then used the Win7 utility EasyBCD to modify the Win7 boot menu -- and everything I tried there gives me an error of 0xC0000098 indicating that the bootloader file created by EasyBCD has problems.

I've asked for help through the EasyBCD forums, but here I'm looking for the exact path that I should force into the BCD data to launch the bootloader. Since this box uses UEFI I'm a bit afraid to install grub2 to the MBR, which is what I would do were it the old BIOS bootstrapping with which I'm quite familiar... Help, anyone?

---

### Post by 0011235813 on 2012-08-26
> **JKyleOKC said:**
> I'm having a problem setting up a dual boot of Xubuntu 12.04.1 and Win7 on my new HP P2-1120 machine. I shrunk the Win7 installation to get 228 GB of free space, and since the system uses UEFI to boot via GPT, there's no limit on primary partitions. Xubuntu seems to have installed properly (as seen from the Live CD), although the "how-to" that I followed had me create a separate /boot partition and change the bootloader location to the resulting /dev/sda5. I then used the Win7 utility EasyBCD to modify the Win7 boot menu -- and everything I tried there gives me an error of 0xC0000098 indicating that the bootloader file created by EasyBCD has problems.

I've asked for help through the EasyBCD forums, but here I'm looking for the exact path that I should force into the BCD data to launch the bootloader. Since this box uses UEFI I'm a bit afraid to install grub2 to the MBR, which is what I would do were it the old BIOS bootstrapping with which I'm quite familiar... Help, anyone?
Why are you using BCD? Surely there must be better partition editors around. If you installed Xubuntu first, then you're probably not going to be able to get it to dual-boot regardless. To be honest with you, this sounds like an EasyBCD problem and not a ubuntu/xubuntu problem.

---

### Post by oldfred on 2012-08-26
I do not know if they have updated EasyBCD for UEFI. It did not work before.

Did you install both Windows & Ubuntu in UEFI mode. How you boot installer is how it installs. Both should be UEFI and then both the Windows efi and Ubuntu grub-efi files are in the efi partition and do not conflict. Grub2's os-prober has a bug and creates a BIOS boot chainload entry to Windows which does not work. But Yann has updated Boot_repair to create the correct entry.

Post link to BootInfo from Boot-Repair to see how Ubuntu is installed.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.Must be 64bit version to have UEFI 

Some links to others with UEFI:
GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by JKyleOKC on 2012-08-26
BCD is the Win7 replacement for "boot.ini" rather than a partition editor.

The problem, I've been told, is that EasyBCD is not yet compatible with the UEFI boot process.

Thus what I need is the way to force a "chainload" of Grub into the BCD data; Win7 has a command-line editor that can do this once I know the command (or code) to use.

Can someone tell me whether Grub2 is fully compatible with UEFI booting as used by Win7-64-bit? If so, I can simply re-install Xubuntu in the same space but using the conventional boot defaults and let the system handle it.

The only reason I want to keep Win7 at all is to have it available when i need to assist my data recovery clients; I don't rely on any Microsoft o/s for day-to-day operations, and Win7 doesn't impress me highly so far...

---

### Post by JKyleOKC on 2012-08-26
> **oldfred said:**
> I do not know if they have updated EasyBCD for UEFI. It did not work before.

Did you install both Windows & Ubuntu in UEFI mode?
I really do not know. Windows was factory installed and definitely seems to be in UEFI mode. For Xubuntu I simply followed the Live CD's wizards, using the manual partitioning to create partitions for /boot, /, swap, and /home (in that sequence) from the 228 GB of free space I had available, with 500 MB for /boot, 20 GB for /, 4 GB for swap, and the rest for /home. I never saw any mention of UEFI during the process. I also set the bootloader location to /dev/sda5 on that screen before continuing with the rest of the installation.

Since there's currently no way that I can boot into the Xubuntu system on the disk, how can I use "boot repair" to fix things? I can run the Live CD, but can it do what needs doing to the GPT-formatted hard disk?

Re-installing Xubuntu will be no problem since I've not been able to do any customizing of it yet, but I'm quite leery of doing things that can make the new box un-bootable. I'm beginning to think that perhaps doing a total replacement of Win7 might be the best fix; this box is replacing an 8-year-old system whose motherboard bit the dust, and it was Xubuntu Lucid only...

---

### Post by oldfred on 2012-08-26
I do not have UEFI, but a lot of the threads show users who installed the BIOS mode version with Windows in UEFI mode. Once they install UEFI version and fix the chain load entry it works. Best to have partitions in advance.

I think it may be possible to convert but reinstall is probably easier. I see grub installed to sda1 which is the efi partition and an efi entry in fstab. And it uses grub-efi not the BIOS version of grub2 - grub-pc.

Install gdisk or post parted:
sudo apt-get install gdisk
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

If first partition is efi and drive is gpt then Windows has to boot from UEFI.

---

### Post by JKyleOKC on 2012-08-26
> **oldfred said:**
> Once they install UEFI version and fix the chain load entry it works.

If first partition is efi and drive is gpt then Windows has to boot from UEFI.I've tried to send you my bootinfo data from [http://ubuntu.paste.com/1168839](http://ubuntu.paste.com/1168839) but it seems to go a bit crazy there. Will try again shortly...

I did get boot-repair installed in the Live CD session to create it.

It looks to me as if taking the recommended repair just might solve my problem -- and if it does, this thread might be worth making into a sticky for others, because it certainly looks as if UEFI is likely to be the coming thing!

Try [http://paste.ubuntu.com/1168839/](http://paste.ubuntu.com/1168839/) for the report!!!

---

### Post by oldfred on 2012-08-26
It looks like you may have installed the BIOS version as you have this entry also:
> 
EFI part (detected by BIS but not in fstab) in same disk

I would have sworn that BIS used to show Windows files in its report. But it does not now.

I do not know if Boot-Repair will convert your install from grub-pc to grub-efi. It will add a correct chain entry like this:

> menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


You would need this in fstab, but with your UUID:
efi partition
# /boot/efi was on /dev/sda1 during installation
UUID=[COLOR=Red]EA74-F7BE[/COLOR]  /boot/efi       vfat    defaults        0       1



UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

Yann posted this in one of the other threads.
> - **If you want to try grub-efi**, it is first necessary to have a  GPT disk with an ESP (EFI partition= FAT32, >200Mo,  start_of_the_disk, boot flag), and to setup the BIOS in EFI mode. Then  you need to install grub-efi (an easy way for this is to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")  with the "Separate /efi" option). To finish, some old EFI-BIOS need to  create an entry that boots the grub*.efi file in the EFI partition.



---

### Post by JKyleOKC on 2012-08-26
> **oldfred said:**
> I do not know if Boot-Repair will convert your install from grub-pc to grub-efi.This part of the report seems to indicate that it might: ```
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1
 the grub*.efi file in sda1 file!

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages) and reinstall the
 grub-efi of sda6, using the following options:        sda5/boot, sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s

```However I'm somewhat at a loss as to how to make the BIOS boot on sda1 (which is the EFI partition) the grub*.efi file, unless that's what the "sda1/boot/efi" option would accomplish.

It doesn't sound as if it would be too risky to try the "recommended repair" setting, in any event, once I've created the Win7 recovery DVDs to be able to get back to factory settings if things go wrong... Would you agree that this seems to be a reasonable plan?

My other options seem to be (1) install a second, blank, drive for Xubuntu, or (2) wipe Win7, move the recovery partition if need be, and make Xubuntu the only system on the disk. Both have disadvantages although I do have an empty 1-TB drive that could be used...

---

### Post by oldfred on 2012-08-26
That is how UEFI works.

You may have to select in the UEFI menu the first time which system you want to boot. Boot-repair will add a Windows chain load.

I think the 'normal' assumption with multi-boot in UEFI is that you go into the UEFI menu each time you want to change boot. The efi partition is a shared boot partition with just a Windows efi boot or grub efi boot file. It replaces the MBR and can then have more than one entry where with MBR you only can have one.

---

### Post by JKyleOKC on 2012-08-26
> **oldfred said:**
> That is how UEFI works.

You may have to select in the UEFI menu the first time which system you want to boot. Boot-repair will add a Windows chain load.

I think the 'normal' assumption with multi-boot in UEFI is that you go into the UEFI menu each time you want to change boot. The efi partition is a shared boot partition with just a Windows efi boot or grub efi boot file. It replaces the MBR and can then have more than one entry where with MBR you only can have one.It worked!

I still have a number of strange entries, but I can now boot into Xubuntu, and through the "bootx86" entry that boot-repair created, access the Win7 chain of startup menus. Since my major need is for the Linux side of things, and the machine will be running 24/7 in Linux once I finish configuring it, that's adequate for now and I can move forward.

The bootinfo report AFTER running boot-repair is at [http://paste.ubuntu.com/1169040](http://paste.ubuntu.com/1169040) for comparison. I'm marking the thread as solved but will continue to monitor it for any feedback that comes in...

I still had duplicate entries in the repository files that stayed there after running the suggested apt-get update, but since that was all in the RAM image from the Live CD it's no problem, just a curiosity. The bottom line is that boot-repair did work properly from the Live CD session, and made things work as desired finally.

Many thanks!!!

---

### Post by oldfred on 2012-08-27
Glad it worked. :)

Just a couple of questions. 

Did you install in BIOS mode and Boot-Repair made all the fixes? I see you do now have an entry in fstab, did you add that or Boot-Repair?

Others have reported that 2 of the 3 chain entries to Windows work (Bottom 3), one does not from Boot Repair's fixes. Grub2's os-prober finds a BIOS Windows boot stanza that does not work with UEFI ('loader on sda3' entry).

---

### Post by JKyleOKC on 2012-08-27
> **oldfred said:**
> Did you install in BIOS mode and Boot-Repair made all the fixes? I see you do now have an entry in fstab, did you add that or Boot-Repair?

Others have reported that 2 of the 3 chain entries to Windows work (Bottom 3), one does not from Boot Repair's fixes. Grub2's os-prober finds a BIOS Windows boot stanza that does not work with UEFI ('loader on sda3' entry).I didn't re-install; all of the fixes were made by Boot-Repair. There's a complete log of its actions at the end of the "after" bootinfo report I linked to above. 

The "loader on sda3" was, I believe, created while I was attempting to use EasyBCD to solve the problem. I tried every "Linux" option I could think of, and of course one of them created a legacy-grub script in the C:\NST\ directory of Win7 and added it to the BCD list where the os-prober found it. That directory has three scripts; I'll eventually get rid of the whole thing since EasyBCD won't yet work on that machine.

I'll use Grub-Customizer eventually to clean up the Grub menu, but that's a lower priority than getting VirtualBox configured to my needs and the VM from the failed box copied over to the new one. This project also involves going from 10.04 LTS to 12.04.1 LTS, and taking vbox from version 3.2 to 4.1.20, so there's about a week's worth of tweaking in store before it's finished.

Again, many thanks for your advice. Without it I would still be beating my head against a brick wall.\\:D/

---

### Post by oldfred on 2012-08-27
Thanks for update & good to know. Yann keeps updating Boot-Repair and it is good at many things.

---

### Post by motmat on 2012-08-29
hello,
sry If i am in a wrong thread but this pup us the first whne i look for "error invalid EFI file path" which i have after adding ubuntu 12.04 to to windows 7 on asus ux32vd.

Im glad it has simple solution - just switch boot order option in bios (when ubuntu is first u can launch ubuntu, but not windows and when boot option 1 is windows bootmanager, then vice versa)

not comfortable to switch BIOS all the time, but fast and simple ... 

if u anyone know simple permanent solution, please let us know it

---

### Post by oldfred on 2012-08-29
One of the options in Boot-Repair is to add a correct chain load entry in the grub menu to a Windows efi boot.

The grub menu currently has a standard BIOS boot entry which is wrong.
Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

You can add your issue to the bug. But you have to create a new sign on in launchpad. They work on a priority basis, so the more complaints (or severity) the sooner it gets fixed.

I think Boot-Repair actually puts in 3 versions as Yann was not sure which worked and it is reported that two of the three work. So after using Boot-repair you will have wrong entry from grub and three entries from Boot-Repair of which 2 work. You then can houseclean out the incorrect chain load entries if you like.

---

### Post by YannBuntu on 2012-08-30
Glad it worked :)
The original problem is that Ubuntu was installed in non-EFI mode.
As there is a separate /boot partition, I guess that JKyleOKC used manual installer.

**@JKyleOKC:** please could you confirm which option you chose in [this screen]("http://pix.toile-libre.org/upload/original/1312973605.png")?

**@all:** for information: [http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

---

### Post by JKyleOKC on 2012-08-30
Yes, I chose the "Something else" option when installing. Specifically, I used the Win7 disk manager to shrink the "OS" partition the maximum amount it would permit. This created 228 GB of free space on the "500 GB" drive. I then used the 12.04.1 Live CD to install in that free space, creating four new partitions including separate /boot and /home.

I believe that the non-functional loader found by Boot-Repair was created by my effort to recover via EasyBCD, before its developer advised me that it does not yet work with UEFI systems. Grub Customizer, however, took it off my Grub menu nicely.

Thank you very much for a great program in Boot-Repair!!!

EDIT: After reading your explanation I feel I needed to report a bit more in detail. Before I ran Boot-Repair but after EasyBCD's failure, at booting I would get a 30-second timeout of an HP splash with offer to hit Esc for a boot menu (which was not an o/s chooser, but rather a menu of HP's tools including full recovery) that would then offer the old Boot.ini-style of o/s chooser for another 30 seconds but only the Win7 choice would work; the other choices (I wound up with 3 as I flailed through the EasyBCD options) all reported corrupt loaders and returned to the o/s chooser.

After Boot-Repair, I still get the HP splash menu that lets me choose from the HP tools initially, but it times out in 10 seconds and gives me the familiar Grub menu with 12.04.1 at the top and chosen as the default. The two working Win7 choices (only one of which I still display) both take me to the Win7 o/s chooser, which still has three non-functional entries for Linux. This is no problem for me because I'm only keeping Win7 to have it available if ever needed to support a customer.

The developer of EasyBCD assures me that he is working to make it compatible with UEFI systems, so it might be a solution in the future. For now, though, it's to be avoided in a situation such as mine...

---

### Post by YannBuntu on 2012-08-30
Thanks for your feedback

> **JKyleOKC said:**
> I chose the "Something else" option when installing.

ok. Next time you do it, don't forget to mount your EFI partition (sda1) on /boot/efi .

> **JKyleOKC said:**
> I believe that the non-functional loader found by Boot-Repair was created by my effort to recover via EasyBCD

It was indeed created by os-prober (see [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383) )

> **JKyleOKC said:**
> After Boot-Repair, I still get the HP splash menu that lets me choose from the HP tools initially, but it times out in 10 seconds and gives me the familiar Grub menu

You may be able to reduce these 10s via the BIOS setup.

---


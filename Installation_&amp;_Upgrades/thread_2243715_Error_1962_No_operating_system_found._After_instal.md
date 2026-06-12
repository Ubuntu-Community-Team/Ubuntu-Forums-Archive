---
title: "Error 1962: No operating system found. After installing new HDD"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by Kathleen_Alexander on 2014-09-10
Hi,

I recently replaced the hard drive in my desktop (Lenovo K430) with a new hybrid drive (Seagate 4 TB Solid State Hybrid Drive SATA 6 GB),  and I have now spent the better part of a week trying to install and run Ubuntu 14.04 on it. However, in spite of numerous permutations of partitioning schemes, setup parameters, boot repair options, and suggestions on existing forum threads, I continue to get the message when trying to boot the system: 
**Error 1962: No operating system found.**

I have tried a number of different partitioning schemes, but the current partitioning scheme looks like this (as can be seen in the boot-repair url linked below):
/dev/sda1 ext4 953MB /boot
/dev/sda2 bios-grub 1MB
/dev/sda3 linux-swap 7.45 GB
/dev/sda4 ext4 3.6 TB /

My current boot/setup settings are: 
**ATA drives setup: **
SATA Mode [AHCI Mode]
[B]Security:
[/B]Administrator Password [Not Installed]
Power-On Password [Not Installed]
**Startup:**
Quick Boot [Disabled]
Boot Up Num-Lock Status [On]
Keyboardless Operation [Enabled]
Rapid Boot [Disabled]
UEFI Boot Mode [Legacy]

This is the resulting url from Boot Repair:
[http://paste.ubuntu.com/8312381/](http://paste.ubuntu.com/8312381/)

Other relevant information:I am currently working with a 32-bit install, but I was getting the same error message with the 64-bit architecture (at this point, I don't care which one winds up on the machine so long as I can get it to boot to an OS). I have no intention of dual-booting this machine. This machine had working Ubuntu 14.04 on it until I replaced the hard drive last week. 

I am happy to provide any additional information that might be useful and am grateful for any suggestions/feedback.
Thanks so much!

---

### Post by yancek on 2014-09-10
Googling the error in the title of this thread comes up with quite a number of hits, most of which are regarding Lenovo.  Your bootinfo output shows Grub installed on the master boot record as well as separate boot partition (sda1) and a BIOS boot partition (sda2).  Would not expect that to be necessary.  From what I have read (see the bottom of the page below) you can not have a partition larger than 2TB with an MBR setup.  You would probably be better off using GPT/EFI.  I don't use either so can't make any specific suggestions.  Shrink the Ubuntu root would be the only thing I could see, use the installation medium you used to install which has GParted on it.  

[http://www.maketecheasier.com/differences-between-mbr-and-gpt/](http://www.maketecheasier.com/differences-between-mbr-and-gpt/)

---

### Post by Mark Phelps on 2014-09-10
>  you can not have a partition larger than 2GB with an MBR setup. 

You mean ... 2TB (not 2GB) right?

---

### Post by yancek on 2014-09-10
> You mean ... 2TB (not 2GB) right? 		

Yes, thanks for pointing that out.

---

### Post by grahammechanical on 2014-09-10
Does the BIOS/UEFI recognise this hard disk? I think that the "no operating system found" message is coming from the BIOS/UEFI. When Grub has difficulty finding the Linux kernel it usually drops to a Grub Rescue prompt.

I do not understand what sda2 bios-grub is doing. If it is supposed to be a EFI partition then I think it should be at the start of the disk. I am not sure but I think so. But you are booting in legacy mode so that an EFI partition should not be necessary. But it could be causing confusion.

Another thing. If you do install in EFI mode do not use a 32 bit version of Ubuntu. And if Ubuntu is the only OS,  and it seems so, why don't you tell the Installer to use the entire disk?

You have a boot partition and a root ( / ) partition but you do not have a separate /home partition or a partition for data. Your partitioning scheme means that once you get Ubuntu installed, if you ever need to re-install you put your data at risk. In my opinion a separate /home partition is more useful than a separate /boot partition.

What I find strange is that Grub usually looks for the Linux kernel in /boot and it looks for grub.cfg in /boot/grub. On your system set root = 'hdo,gpt1' which is the first partition on the first hard disk. Which would be sda1 but in sda1 grub.cfg is in /grub/ and not /boot/grub/. Do you have a boot folder on sda1 that contains Linux kernel files?

There should be a 5 file set for each Linux kernel as well as 3 for memtest. You should see files that start with abi-; config-; initrd.img-; System.map- and vmlinuz-

Regards.

---

### Post by Kathleen_Alexander on 2014-09-12
Thank you very much for your responses. At this point, I am still getting the same error (**Error 1962: No operating system found**).[B]
[/B]Based on your suggestions, this is what I have tried. Note that all of these attempts are with 64-bit 14.04.
[B]The GPT/EFI route:
[/B]In order to get a live disk to boot on my machine in UEFI mode, it was necessary to use a DVD rather than a USB (the USB just goes to a black screen when I try to run it in UEFI mode). I have tried the following, all of which had the same ultimate result:
1. Automatic partitioning (erase disk and install option) and installing ubunutu from the DVD in UEFI mode. The resulting partition table looked like this:
     /dev/sda1 fat32 efi boot partition
     /dev/sda2 ext4 mounted on /
     /dev/sda3 linux-swap
2. Manual partitioning the disk (note that use of any additional partitions such as /home resulted in an out of disk error)
     /dev/sda1 fat32 efi boot partition
     /dev/sda2 ext4 mounted on /
     /dev/sda3 linux-swap
3. Using boot-repair on both of the above installations after they would not boot
4. chroot-ing to the installed system as described [here]("https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD") and running the following commands as recommended [here]("https://wiki.archlinux.org/index.php/GRUB_EFI_Examples"):
     # grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub --recheck --debug
     # mkdir /boot/efi/EFI/Boot
     # touch /boot/efi/EFI/Boot/bootx64.efi
5. The above bootx64.efi file was empty, so I also tried getting a version of it with wget and putting it in that location
6. Installing from the live DVD in legacy mode and then booting back to the live disk in UEFI mode and converting the installed system to UEFI as discussed [here]("https://help.ubuntu.com/community/UEFI")

**The Legacy Route:**
1. Automatic partitioning (erase disk and install option) and installing ubunutu from the DVD in Legacy mode, and then resizing the root partition to be less than 2 TB after the installation 
2. Automatic partitioning (erase disk and install option) and installing ubunutu from the USB in Legacy mode, and then resizing the root partition to be less than 2 TB
3. Maual partitioning the disk so that all partitions were less than 2 TB, the resulting partition table being (all primary partitions):
     /dev/sda1 bios_grub boot partition 1 MB
     /dev/sda2 ext4 mounted on / 1.9 TB
     /dev/sda3 linux-swap 8 GB
     /dev/sda4 ext4 no mount point specified, 1.8 TB
4. Running boot-repair on each of these 

The current permutation of all of this that I am at is back to one of my first attempts in UEFI mode:
Installed ubuntu from dvd in UEFI mode. Used automatically generated partition table that looks like this:
     /dev/sda1 fat32 512 MB 
     /dev/sda2 ext4 3.63 TB
     /dev/sda3 linux-swap 7.97 GB

[This]("http://paste.ubuntu.com/8328368/") is the current url I get from boot-repair, which is currently telling me that an error occurred during the repair.

Additional information: when I boot to the live DVD, the boot-order is set to check the HDD first, and the following error message appears before it goes and finds the DVD (I don't see this error when I have removed the DVD and it is only looking on the HDD):
**Error could not open EFI\Boot\fallback.efi**

Also- the 5 linux kernel files and 3 memetest files are present on the /boot folder on the 4TB drive I can navigate to from the live DVD, but I think this might be /dev/sda2, and I am not sure how to check whether there is anything like this on /dev/sda1

Any further recommendations or suggestions would be greatly appreciated.
Thanks Again!

---

### Post by Kathleen_Alexander on 2014-09-15
If I am ready to give up and just get a different replacement HDD, any suggestions in terms of avoiding this or similar issues? 

Aside from making sure that it is 2 TB or less, should I stay away from the Solid State Hybrid Drive devices and just go with something more like the Seagate Barracuda that was originally installed? I would like to avoid doing this again if possible, so any advice would be greatly appreciated.

Thanks again.

---

### Post by oldfred on 2014-09-15
There is a reported bug:
 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Solution seems to be just copy grubx64.efi to fallback.efi in /efi/boot folder in efi partition.

You do have to have 64 bit version for UEFI. And there really is not any reason for 32 bit version with new systems. There are only a very few special apps that may require 32 bit and then it may be better to install that 32 bit in another partition or virtual memory install.

With very large hard drives it is better to have a smaller / (root) and use rest of drive as /home or data partitions. 

Boot-Repair picks up some minor issues as errors but this says grub installed correctly as error code 0 is no error.
 Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

---

### Post by Kathleen_Alexander on 2014-09-15
Thanks so much for your response; I tried this suggestion and am still getting the same 'Operating system not found' error when I try to boot the machine and the live disk is not present. When the disk is present, I am still seeing the same 'Could not open EFI\BOOT\fallback.efi' message.

As such, it is possible that my method for moving files and folders within the efi partition is not correct (sorry for being so ignorant about all of this).

This is specifically what I did:
1. Boot computer with live DVD in UEFI mode 

2. Open terminal and type these commands as instructed [here]("https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD"):
[COLOR=#000000][FONT=monospace]# sudo mkdir -p /mnt/sabayon/boot
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# [/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo [/FONT][/COLOR][COLOR=#000000][FONT=monospace]mount /dev/sda2 /mnt/sabayon
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# [/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo [/FONT][/COLOR][COLOR=#000000][FONT=monospace]mount /dev/sda1 /mnt/sabayon/boot
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# [/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo [/FONT][/COLOR][COLOR=#000000][FONT=monospace]mount -t proc none /mnt/sabayon/proc
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# [/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo [/FONT][/COLOR][COLOR=#000000][FONT=monospace]mount -o bind /dev /mnt/sabayon/dev
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# [/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo [/FONT][/COLOR][COLOR=#000000][FONT=monospace]mount -o bind /run /mnt/sabayon/run

3. Then type this command:
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]# sudo chroot /mnt/sabayon /bin/bash

4. Then I looked for the files you mentioned. The /boot/EFI/BOOT directory did not exist, but /boot/EFI/ubuntu did

5. So I created /boot/EFI/BOOT and did:
cp /boot/EFI/ubuntu/grubx64.efi /boot/EFI/BOOT/fallback.efi

6. Then I exited and tried to reboot and got the errors mentioned above

Was that the correct method for this? I assume it wasn't since I am still getting the errors that this is supposed to fix...
Thanks![/FONT][/COLOR]

---

### Post by oldfred on 2014-09-15
That may not be correct. The efi partition is not a /boot partition. That would be another partition, but not normally required with most desktops. Your /boot then is a folder inside your / (root).

With grubx64.efi you do have to have secure boot off. Is it off?

Spec sheet for that drive says it is compatible with Linux. Even XP which does not normally work with gpt partitioned drives.
Some hybrid drives have had special Windows drivers and compatibility issues.

Most UEFI also can boot from bootx64.efi in the efi/boot folder.

       From live installer mount the efi partition on hard drive:
mount /dev/sda1 /mnt
mkdir /mnt/EFI/BOOT
cp /mnt/EFI/ubuntu/* /mnt/EFI/BOOT
cp /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi
cp /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/fallback.efi

---

### Post by Kathleen_Alexander on 2014-09-15
Thanks so much for the response. It is very useful to know that this is not a drive compatibility issue. 

I believe that secure boot is off, but I am not completely sure. In the Security tab of my setup menu, the only options I have are:
Administrator Password [Not Installed]
Power-On Password [Not Installed]
There was nothing else in the setup menu related to security settings, so I take that to mean that secure boot is off, but please correct me if I have not been looking in the correct place to change this setting.

I tried the commands you mentioned above (I didn't do any of the chroot commands before the ones you mentioned, was I supposed to?) and the results I am getting are the same (still 'could not open EFI\BOOT\fallback.efi' when disk is present and 'no operating system found' when disk is not present).

Edit: In case it helps, this is the current url from boot-repair: [http://paste.ubuntu.com/8352950/](http://paste.ubuntu.com/8352950/)

---

### Post by oldfred on 2014-09-15
You show you have the fallback and it looks to me in correct place.

You also have installed grub to MBR and to the partition boot sector of the efi partition. 
If that was NTFS it would corrupt partition, but I do not know about FAT32? Generally you should never install grub (BIOS version) to a partition. And the one in the MBR will never be used with UEFI, but does not otherwise matter. If you attempt to boot in BIOS mode it may try to load the grub in the MBR, but grub would fail.

I do not know how you got a menu.lst into the efi partition. That is from grub legacy and does not work with UEFI.

Your grub.cfg shows no kernels installed. Did when you install use the efi as /boot?
Also with a nVidia card you will need nomodeset in grub to boot until you install proprietary driver. And with one install grub menu will not normally appear, so you have to use escape from UEFI/BIOS until menu appears. But until you get past initial error, you cannot do any of that.

I really suggest a new install. You will probably have to recreate the /efi/boot/fallback.efi again after install. I would not reuse existing efi partition but delete & recreate it, so it removes the grub in the partition boot sector.

I suggest with this large of a drive a smaller / (root) partition of 25GB or so. Since you have so much space it could be a bit larger but not really required.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

Just found this:
A user complaining about error 1962 and why he cannot install Windows 8.
[https://forums.lenovo.com/t5/IdeaCentre-Desktops-Home-Servers/b540p-error-1962-no-operating-system-found/td-p/1068069](https://forums.lenovo.com/t5/IdeaCentre-Desktops-Home-Servers/b540p-error-1962-no-operating-system-found/td-p/1068069)

Another thread says it may be the SATA cable error? Does you BIOS show drive correctly in UEIF/BIOS?

---

### Post by Kathleen_Alexander on 2014-09-15
Thanks so much for this advice- I will make sure to partition in advance for this install as you suggest, but I wanted to clarify a few things, if you don't mind.

I mentioned earlier that I actually have been unable to complete the installation when I include any additional partitions like /home and /data. I get an 'out of disk' error during the installation when attempting partitioning schemes of this nature, and the solution I saw most people recommended was to remove the other partitions and have only a root partition. Will this fundamentally cause any problems? Also, this shouldn't have anything to do with the other issues I am having, right?

Lastly, I have been using GParted to partition the drive. I was under the impression that when the computer is running in UEFI mode during the partitioning, it will partition into a gpt partition table whereas, if the computer is running in Legacy mode at the time of the partitioning, it will partition into an MBR partition table. So I have not been taking any action to ensure that the partitioning creates a gpt system beyond ensuring that the system is in UEFI mode. Should I be using a different tool or taking other action to ensure the right kind of partition table is generated?

---

### Post by oldfred on 2014-09-15
I have been using gpt with BIOS boot on my part 2006 & part 2009 system without issue. I suggest gpt whether UEFI or BIOS for any drive will will not have Windows or can boot both systems with UEFI.
Windows only boots from gpt with UEFI, but all Windows since XP read gpt without issue.
Ubuntu boots from gpt with UEFI or BIOS as long as correct supporting partitions, efi or bios_grub are on drive.

       . I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

If only installing Ubuntu only use gpt. I also have seen a few installs where drive was blank and somewhere over 1.5TB and Ubuntu changed to use gpt as default. And any drive over 2TiB must use gpt to be able to use entire drive.

There used to be a grub bug on very large / (root) partitions (over 500GB). Supposedly that was fixed several versions ago, but you have an extremely large /. Most of the issues were with old BIOS systems that only boot from the first 137GB, or from USB drives with large root partition. I boot from the end of my 640GB drive in BIOS without issue. I also have not seen boot issues with boot files further into drive with UEFI systems.

But if you have a smaller / of 25 GB right after the efi partition then you definitely should not have any issues. One advantage of a smaller / is that drive does not have to search over a large / partition to find grub & kernel to boot. The Linux formats generally randomly write files to anywhere in partition.

But we need to get past error 1962 as that seems to be a UEFI/BIOS or hardware issue.

---

### Post by Kathleen_Alexander on 2014-09-16
Thanks so much for your continued support and patience on this.

I was able to partition the hard drive and complete the installation with this partitioning scheme, which is definitely a step forward. 
I then recreated the /efi/boot/fallback.efi files as you suggested. However, I continue to get the same errors as before (error 1962 without live DVD, and could not find fallback.efi when the live DVD is present).

This is the current output from boot-repair: [http://paste.ubuntu.com/8358238/](http://paste.ubuntu.com/8358238/)

I don't know if this is relevant, but when I run boot-repair, the tool has me run a number of terminal commands throughout the process. Specifically, it has me run:
sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda2" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda2" apt-get purge -y --force-yes grub* shim-signed linux-signed*
sudo chroot "/mnt/boot-sav/sda2" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

In the Boot Repair advanced options, I specify that there is a separate /boot/efi partition at sda1 and that OS to boot by default is sda2 (Ubuntu 14.04. 1 LTS), so I'm not sure why all these commands it tells me to do for the grub-efi installation are on sda2

Any other suggestions at this point?

---

### Post by oldfred on 2014-09-16
It has to chroot (CHange ROOT) to work from inside your install. And if just reinstalled or forced a reinstall of the signed versions of the Kernel & shim (grub) for secure boot.

Do you have secure boot on?

Perhaps your system is one that only boots Windows? I thought Lenovo just worked but some may have issues.

Just as we created a /efi/boot for fallback, we can create a /efi/Windows/Boot and copy grub or shim into that folder and rename it to bootmfgw.efi.

     From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi 

Then see if system will boot a Microsoft entry from UEFI or one time boot key. Sony & HP modify UEFI to only boot the UEFI entry with Windows. We may have to also rename the entry in UEFI to Windows.

Some that do not have Windows just rename shim directly:

 
 sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

Or we can rename the new "Windows file" which really is grub or shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\Microsoft\Boot\bootmfgw.efi "

And another alternative which requires installing another boot manager is rEFInd.
       [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Kathleen_Alexander on 2014-09-16
That fixed it!
I added the Microsoft/Boot directory on the sda1 boot partition, and then did each of:
[COLOR=#000000]cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi 
[/COLOR][COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[/COLOR][COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\Microsoft\Boot\bootmfgw.efi "[/COLOR]

And now it boots to Ubuntu 14.04 with no error messages.
Thank you so much for all your help!

---

### Post by oldfred on 2014-09-16
Glad you got it working. Yours must be one that needs the Windows name. :(

I think only one of the renames to Windows Boot Manager took in UEFI, but it does not really matter.
But you will not be ever able to install Windows :)  without major reconfiguration.

---

### Post by roy25 on 2014-10-26
> **Kathleen_Alexander said:**
> That fixed it!
I added the Microsoft/Boot directory on the sda1 boot partition, and then did each of:
[COLOR=#000000]cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi 
[/COLOR][COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[/COLOR][COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\Microsoft\Boot\bootmfgw.efi "[/COLOR]

And now it boots to Ubuntu 14.04 with no error messages.
Thank you so much for all your help!


Hi,

I'm running into the same problem with my Lenovo and have tried many different things to make this boot.  I've tried to do the steps mentioned in this thread but not sure how to get this to work.

Is there a step by step process you took that helped make this boot correctly?

Thanks in advanced!

---

### Post by oldfred on 2014-10-27
@roy25
Are you also dual booting with Windows or just Ubuntu?
Is Ubuntu in UEFI boot mode?
What model Lenovo?

Did you rename bootx64.efi in /efi/Boot? Copy grubx64.efi into that folder and rename it to bootx64.efi?
And then see if you can boot a hard drive entry in UEFI or one time boot key.

---

### Post by roy25 on 2014-10-27
Hi,

Thanks for the quick reply!

I'm not dual booting with Windows.  Just Ubuntu.

How do I know if Ubuntu is in UEFI boot mode?  I have my bios set to use 'UEFI First' for boot priority.

My Lenovo model is ideacentre B540.

I did not rename bootx64.efi in /efi/boot.  Do I open the files within my usb key?

Sorry, I'm very new to Linux and I want to learn.  It's the reason I'm trying to install Ubuntu to my computer.

Thanks in advanced for your help!

---

### Post by oldfred on 2014-10-27
If you only have Ubuntu you can recreate or rename the Windows efi boot file bootmgfw.efi but make it really be grubx64.efi. Then system thinks it is booting Windows and really boots grub.

Several vendors have internally modified UEFI to only boot the Windows boot entry. That is not per UEFI standard but is how it is, so we have to do work arounds.

Most of the various work arounds:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

But if not using Windows you can just create the bootmgfw.efi file. The only thing would be if grub does a major update you would need to copy grubx64.efi again.
I would think if you installed in BIOS/CSM boot mode and you have UEFI/BIOS set to boot in BIOS mode it should just work. But UEFI requires you to be in UEFI mode and then the system may expect only Windows.

This was one way:

 Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)
    From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by roy25 on 2014-10-27
Hi oldfred,

I've done the steps that you've mentioned above and I'm still getting the same error.  Did I miss a step by any chance or maybe I do not have the bios set up correctly.

Was I supposed to run boot repair?  If so, does it matter if I do it before or after doing the steps mentioned above?

Again, thanks for your help and patience on this!

---

### Post by oldfred on 2014-10-28
Run the summary report in Boot-Repair just so we can see configuration. Post link to report.

       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Your efi partition should have these folders:

 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

And in each you have grubx64.efi and have secure boot off in UEFI.
Then in Boot you rename grubx64.efi to bootx64.efi and in Microsoft/Boot rename grubx64.efi to bootmgfw.efi.

Looks like I may have typo in many of my instructions. should be bootmgfw.efi not bootmfgw.efi.

---

### Post by roy25 on 2014-10-28
Hi oldfred,

I renamed the file and it boots!  Thanks again for your help!

---


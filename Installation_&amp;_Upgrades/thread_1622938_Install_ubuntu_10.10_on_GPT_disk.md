---
title: "Install ubuntu 10.10 on GPT disk"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by bolus on 2010-11-16
I'm trying to install ubuntu on a 2TB disk, which uses guid partition tables. I can find a lot of information about how/why it works differently, but I cannot find a guide how to correctly install the bootloader on the disk. What I understand is that I need to make an extra boot partition, but I don't know how. I tried putting /boot on a different partition but that doesn't work.
 
Does anyone have a step by step guide how to install ubuntu 10.10 on a >= 2TB disk?

---

### Post by linux-hack on 2010-11-16
You can use Gparted to make a partition of lets say 200Mb for the boot and install the brub on that partition with the command grub-install /dev/partition-name

but if you want to install ubuntu on that drive, it does that for you. What are the exact steps that you did to install it ??

---

### Post by bolus on 2010-11-16
Well I tried a normal install, that doesn't work. It installs, but afterwards doesn't boot. Then I made a partition 10mb and gave it mount point /boot. That doesn't work either. 
 
Then I made a partition with gparted 10mb and entered the command below, and then did the install process. Half-way the install it says it can't install grub there.
 
$ sudo parted /dev/sda set sda1 bios_grub on
 
I found the info here: [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

---

### Post by dino99 on 2010-11-16
[http://ubuntuforums.org/showthread.php?t=1452235](http://ubuntuforums.org/showthread.php?t=1452235)

---

### Post by bolus on 2010-11-16
Thanks, interesting topic, but I don't see a solution there.

---

### Post by oldfred on 2010-11-16
Are you using efi or BIOS?

It is not a separate /boot that you need, but a bios_grub partition. Also some BIOS need a boot flag even though gpt does not include boot flags.

Add boot flag (even though not required with gpt) - see post by srs5694
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)

If you have gpt you need another small (8-32mb) partition for grub. Are you using efi or BIOS compatible mode?
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. Make it 128 kiB as recommended in the following link. Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32. You can set bios_grub flag in gparted or with command line:
sudo parted /dev/sda set <partition_number> bios_grub on


Just to learn about gpt, I converted one smaller drive to gpt. I created my partitions in advance and add the bios-grub partition first. It installed without any issues and booted just fine. But I still have BIOS.

---

### Post by bolus on 2010-11-16
Hi Oldfred, thanks for your reply, I found a lot of usefull information. Indeed, it's an Intel D945GSEJT motherboard, which has the problems I found in your links.
 
To answer your questions, I don't know what EFI is, I googled it, and it's like an improved BIOS? As far as I know my mobo has a BIOS. So I also don't know if I am using EFI or BIOS compatibility mode...sorry :confused:
 
I think I tried your suggestion allready, it didn't work. I'll descrbe it step by step:
 
1. Boot from usb using unetbootin ubuntu 10.10 desktop
2. started gparted gui.
3. made partitions:
sda1 10mb fat (do I need to make it ext2?)
sda2 74gb ext4 /
sda3 2gb swap
sda4 ntfs data
4. ran command sudo parted /dev/sda set 1 bios_grub on
5. reboot
6. install ubuntu on sda2
7. installation went fine, after reboot mobo says: no boot device found. When I boot and enter f10 (boot menu) and choose: disk 2tb samsung ... it boots fine.

Thanks for your help, I really apreciate it.

---

### Post by oldfred on 2010-11-16
It seems that the intel boards require a boot flag whether needed or not. Windows needs a boot flag, grub does not.

Link in my earlier post.

Add boot flag (even though not required with gpt) - see post by srs5694
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)

If that does not work then post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by srs5694 on 2010-11-17
The BIOS Boot Partition can be very small (as small as 30-some *kilo*bytes), but given modern partition alignment practices, it's likely to be 1 MiB. It should contain *no* filesystem. (Creating it with a filesystem won't do any harm, but it'll be wiped out, since GRUB uses it to store some raw code without a filesystem.) In a libparted-based tool, such as GParted, it should have a bios_boot flag. In [GPT fdisk (gdisk),](http://www.rdosbooks.com/gdisk) give it a type code of EF02.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP). This is entirely different; it should be a 100-200 MiB FAT32 partition that's flagged as an ESP. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.

To be safe, create both of these partitions, in addition to your regular Linux partitions. *Do not* configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

To install, you have two options, both of which begin with preparing the disk as just described:


[list]
[*]Install in BIOS mode and reboot. With luck it'll work; but some Intel BIOSes have known GPT issues. [See here](http://www.rodsbooks.com/gdisk/bios.html) for more details and information on the solution, which is to set the MBR boot/active flag on the EFI GPT (type-0xEE) partition in the MBR. (GPT includes an MBR with a single type-0xEE partition to protect it against GPT-unaware utilities.)
[*]Switch on EFI mode in your BIOS. (Many modern Intel BIOSes can actually switch between BIOS and EFI mode.) You can then install Ubuntu, but you may need to jump through some extra hoops, since Ubuntu doesn't support EFI very well just yet. Specifically, you'll need to uninstall the grub-pc package and install grub-efi in its place. You may also need to install rEFIt.
[/list]


I should also point out that it's not necessary to use GPT on a 2 GB disk; this disk size is actually below the 2 GiB value that's the limit for MBR. Although GPT does have advantages even on smaller disks, and although you'll have to use it eventually, if your motherboard is giving you too many problems, you can stick with MBR for the time being. To do so, though, you should be sure to *completely* wipe the GPT data. GParted can do this if you tell it to create a new disklabel of type "ms-dos" (its name for MBR), but this is destructive. (I figure that's fine at the moment, since this is a new installation.)

---


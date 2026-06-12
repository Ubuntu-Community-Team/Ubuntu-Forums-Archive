---
title: "No boot device after fresh 16.04.3 install"
date: 2017-09-12
forum: Installation &amp; Upgrades
---

### Post by GovDude on 2017-09-12
I haven't done a fresh install of Ubuntu in about 7 years, and it shows! Maybe someone can tell me what I'm doing wrong...

I have a new HP Z640 workstation with two disks, a 1TB SSD and 3TB standard drive. I disabled everything I could find in the BIOS about secure boot and enabled everything I could find about legacy boot. I changed the boot order so that it boots USB, DVD, HDD, SSD. Popped in the the 16.04 install DVD and it booted just fine. Selected "Install Ubuntu" and off it went. I got a considerable way through the install but when it tries to install grub it fails. So I rebooted from the install DVD and selected "Try Ubuntu" instead of the install and after booting I opened up a terminal. Everything looks fine, according to my read of UEFI, GPT, and a lot of new crap that I'm not familiar with. My partitions look like:

[FONT=courier new]# parted -l

Model: ATA TOSHIBA DT01ACA3 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number   Start     End     Size     File system      Name     Flags
 1       1049kb    2095kb  1049kb                             bios_grub
 2       2097kb    2863GB  2863GB   ext4
 3       2963GB    3001GB  137GB    linux-swap(v1)

Model: Unknown (unknown)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

[/FONT][FONT=courier new]Number   Start     End     Size     File system      Name     Flags
[/FONT]
So I'm trying to install Ubuntu on the ATA and all I've done to the SSD is wipe Windows off of it and wipe the partitions. I believe I did something in the BIOS to erase it as well, some type of Windows Boot Manager partition I think? That was so many steps ago though so I don't recall exactly. Back to the open terminal from the "Try Ubuntu" boot...

Now I can invoke grub manually like:

[FONT=courier new]# mount /dev/sda2 /mnt
# grub-install /dev/sda --root=/mnt
Installing for i386-pc platform.
Installation finished. No error reported.
[/FONT]
And even go through the whole install process again after this, this time without any grub errors, and then I get the message about no boot device being found. The exact message looks like:

[FONT=courier new]BootDevice Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)
[/FONT]
And then the options to go into the BIOS. Again, the BIOS looks fine to me. None of the UEFI options are active, and I have the Toshiba listed in the boot devices, but it's a no-go? 

Hopefully someone has some suggestions. Most of what I've been able to find on Google deals with UEFI booting, which I don't think is my issue.

TIA!
Gary

---

### Post by JKyleOKC on 2017-09-12
This may be a very wild guess, but I believe I read somewhere that to partition a 3-TB drive you have to use GPT rather than legacy BIOS, and that might be your problem since they have different booting protocols. For a GPT system, you have to use EFI, which requires a different setup of grub. Oldfred can tell you more about this, though. My biggest drive is smaller than 2 TB, which is the boundary line, so I still use the MBR boot protocol on it -- and it's been several years since I fought my way through a UEFI install on another, smaller, drive! Perhaps this will give you a lead for your research even though I'm not able to be more helpful.

---

### Post by oldfred on 2017-09-12
You can boot from gpt with BIOS, but must have a bios_grub partition, which you have.
Generally better to use UEFI/gpt than the 35 year old BIOS/MBR. (You put that Ford Pinto engine in your new Mustang). And MBR is so old that it cannot support more than 2TiB as even GB was unheard of when MBR was designed. 

HP is not UEFI dual boot friendly. But many work arounds to make it work. Probably last on list is to use BIOS boot, but some do that.

But your error seems to be that you are trying to boot in UEFI or UEFI Secure boot mode with a BIOS boot install. You should in your UEFI have a boot option for Legacy/BIOS/MBR or directly to hard drive. Often have to separately turn that on or allow that boot.

This will not show UEFI settings nor is good about the new high speed SSD NVMe devices. 
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by GovDude on 2017-09-13
Thank you! I was under the impression that UEFI and Secure Boot were synonymous and I did NOT want to deal with secure booting. Also, of course, I'm familiar with the legacy system, or was, so I thought I'd be more successful using it. However, after you guys pointed out that the 3TB drive in my system and legacy booting probably weren't good ideas I went in and reenabled UEFI but kept secure booting disabled and voila, Ubuntu installed and booted with zero problems. Many thanks!

---

### Post by mörgæs on 2017-09-13
Good, please mark the thread solved.

---


---
title: "Installation needs Reserved BIOS Partition; but no Grub; boots only into Windows"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2012-11-06
I have installed Ubuntu many times on Windows systems (for dual-booting), and today I have come across something new that I do not understand.


[LIST]
[*]The machine has Windows 7 64-bit. I am installing Ubuntu 12.04.1 64-bit.
[/LIST]

[LIST]
[*]I created the partitions (swap, root and home) beforehand.
[/LIST]

[LIST]
[*]On choosing the partitions in "Something Else", the Ubuntu installer complained that I did not have a partition of at least 1Mb for a *Reserved BIOS Boot Partition*.
[/LIST]

[LIST]
[*]I duly shrunk one partition and created a new partition of 16Mb (I couldn't make it any smaller). In GParted, the "flag" shows as [FONT=Lucida Console]bios_grub[/FONT]; in Disk Utility, it shows as *BIOS Boot Partition*. I have never come across such a thing before.
[/LIST]

[LIST]
[*]Trying again to install Ubuntu, I told the installer to use that partition as its BIOS boot partition.
[/LIST]

The installation appeared to go perfectly.

However, post-installation, when I rebooted, the computer went straight into Windows. It did not present a Grub screen to choose Ubuntu.

Any help as to what I should do? I am happy to delete the partitions and reinstall, if necessary.

---

### Post by oldfred on 2012-11-06
With the new gpt partitioning instead of MBR(msdos) partitioning you need either a bios_grub partition for BIOS booting or an efi partition for UEFI booting.

gpt is required for drives over 2TB, suggested for SSDs, and required for UEFI booting. Ubuntu will work with gpt partitioned drive with either BIOS or UEFI.

I use gpt with BIOS and have had to add the 1MB bios_grub partition with no format on every gpt drive. I even used gpt on a 16GB flash drive for a full install to see if it worked. It did. 

Windows will only boot from gpt partitioned drives with UEFI. So if your system is the new UEFI system, you should not be creating bios_grub, but already have an efi partition as either the first or second partition on the drive.

With both Ubuntu (64 bit only) & Windows   and new UEFI systems the install media has both UEFI and BIOS installers. How you boot install media is how it will install. If you already have Windows in UEFI mode you must install Ubuntu in UEFI mode or else it gets confusing.

If you installed Ubuntu in BIOS mode on an UEFI system, Boot-Repair can convert Ubuntu/grub from BIOS to UEFI boot if installed on a gpt drive. It uninstalls grub-pc, installs grub-efi and adds an entry to fstab.

Best to post BootInfo:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Paddy Landau on 2012-11-07
Oldfred, thank you for your comprehensive reply.

You did not post a link to the boot info, but I think I understand that I have two ways forward.

[LIST=1]
[*]Run Boot-Repair to fix the boot system.
[*]Reinstall Ubuntu using UEFI.
[/LIST]
In both cases, I can also delete the small partition that I created—I have done that.

As the second option is the cleanest (to my mind), I am reinstalling as I write.

(When booting the computer, it gave me the choice of "my USB" or "UEFI my USB". I chose the second.)

I shall let you know what happens.

---

### Post by Paddy Landau on 2012-11-07
Oh dear&#8230; I need help!

Here is what happened.

Ubuntu installed fine. When I reboot, I get the familiar Grub with the following six options.
```
Ubuntu, with Linux 3.2.0-29-generic
Ubuntu, with Linux 3.2.0-29-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda3)
Windows Recovery Environment (loader) (on /dev/sda4)
```If I choose the first option (Ubuntu), Ubuntu boots perfectly. Yay!

But if I choose the penultimate option (Windows 7 on /dev/sda3), I get an error.
```
error: invalid EFI file path.

Press any key to continue...
```What can I do to get Windows back?

---

### Post by oldfred on 2012-11-07
The grub2 os-prober creates the standard BIOS/MBR chain load entry, not the newer efi entry. Boot-Repair can fix it. 

BootInfo is the report Boot_Repair creates which adds some extra info to the bootinfoscript.

Boot-repair also has an option to add the correct efi chain entries. 

Or you can manually add them yourself to 40_custom. But you have to use your [COLOR=Red]UUID, [COLOR=Black]if you use the first version. If you use the second version it relies just on the grub search function.The insmod are to make sure grub has added in the modules required, but with efi they must be automatic as the second version works without all the specific add ins. 

[/COLOR][/COLOR]Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root [COLOR=Red]4f84-ee2e[/COLOR]
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Paddy Landau on 2012-11-07
Thank you, oldfred. My problem is solved.

I decided to do it the easy way; I booted into a Live CD, installed Boot Repair, and let it fix the problem. It is pleasing to find a GUI utility that works so well.

There are several new entries in the Grub menu now. Is there an easy way to move the entries around, so that Ubuntu is at the top and Windows at the bottom? And, if possible, to move the other entries into a submenu?

---

### Post by oldfred on 2012-11-07
I have not used it, grub customizer. It has been updated for grub2 2.00. Do not know for sure if it works with your efi, but since it is just the grub menu I would think so.

New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

Is this the grub menu or the UEFI menu? Do not know about UEFI menu, but I thought you just see UEFI to boot one system and it remembered that. Then grub menu gives option to boot both systems.

---

### Post by Paddy Landau on 2012-11-08
> **oldfred said:**
> Is this the grub menu or the UEFI menu?
I wouldn't know how to tell the difference!

The entries now look like this:
```
Ubuntu, with Linux 3.2.0-32-generic
Ubuntu, with Linux 3.2.0-32-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows UEFI loader
Windows Boot UEFI bootx64.efi
MacOS UEFI *.scap
MacOS UEFI *.scap
Windows 7 (loader) (on /dev/sda3)
Windows Recovery Environment (loader) (on /dev/sda4)
```Note the unexpected addition of MacOS (twice); this is not a MacOS machine!

I guessed "Windows UEFI loader" to load Windows, and it turned out to be the right one.

This is so confusing — how is a non-technical "average" user supposed to decipher this?

However, oldfred, you have come up trumps yet again — the Grub Customizer works a treat, thank you!

---

### Post by oldfred on 2012-11-08
I think Boot-Repair may have added those settings, not sure why. We maybe should ask Yann if it is a bug. 

I think Grub Customizer is the easiest way to customize grub for most, but the inner workings are in the scripts.

Entries come from the scripts in /etc/grub.d. But one script 40_custom or maybe 25_custom are just files with added boot stanzas. I backup my 40_custom so I have it for my next install, but I have lots of entries. The main script for finding other systems is 30_os-prober. All scripts can be turned off but one or two are essential.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

------------------------
From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by Paddy Landau on 2012-11-08
Thanks for the links, oldfred. They are took complex for my purposes; I'll just stick with Boot-Repair and Grub-Customizer. They do the job very well.

Thanks again for pointing me to a great solution — Grub looks great with a background picture.

---

### Post by YannBuntu on 2012-11-08
Hello
The "MacOS UEFI *.scap" invalid entries were due to a bug of the 3.194~ppa50 to ppa52 versions of Boot-Repair. I will fix this today.

Thanks for reporting it!

---

### Post by Paddy Landau on 2012-11-09
> **YannBuntu said:**
> Hello
The "MacOS UEFI *.scap" invalid entries were due to a bug of the 3.194~ppa50 to ppa52 versions of Boot-Repair. I will fix this today.

Thanks for reporting it!
Thank you for attending to this.

---


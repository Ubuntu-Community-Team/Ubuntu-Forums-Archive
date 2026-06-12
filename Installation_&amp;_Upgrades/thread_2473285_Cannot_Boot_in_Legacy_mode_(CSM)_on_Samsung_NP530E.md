---
title: "Cannot Boot in Legacy mode (CSM) on Samsung NP530E5M (Boot-repair/grub)"
date: 2022-03-30
forum: Installation &amp; Upgrades
---

### Post by foobar34 on 2022-03-30
I'm using a 5 years old Samsung NP530E5M as my Ubuntu/Linux dev machine. As many other Samsung laptops, in order to support Samsung features like the ability to charge the battery only to 85%, I need to boot in Legacy/CSM mode and not UEFI mode

I have 2 disks in my system, one is a NVME disk (GPT) with a dual UEFI boot for Ubuntu 20.04 and Windows 10, and another SATA HDD with a Windows 10 installation. I realize that if I choose to boot from the NVME disk as legacy BIOS, I lose the ability to boot in Windows 10 from that disk, but it's ok in my case, I only need Linux

I followed the instructions here [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode), removed the UEFI partition, created the bios boot partition with gparted, ran boot-repair, with advanced options, selected to place grub into /nvme0n1 and rebooted into the BIOS options. I selected CSM boot, disabled fast boot and secure boot. But the BIOS doesn't see the NVME disk as bootable. I followed all the steps in boot repair religiously multiple times, and ensured I installed grub-pc, not grub-uefi

I checked that my laptop can boot into BIOS mode by renaming the EFI folder in the boot repair disk and booting from the USB stick as a legacy BIOS session (and verified that it's the case)

It looks as if I'm not properly marking the NVME GPT disk as BIOS bootable

Pastebin file is here [https://paste.ubuntu.com/p/WVbghrW5sz/](https://paste.ubuntu.com/p/WVbghrW5sz/)  any help is appreciated

---

### Post by zebra2 on 2022-03-30
I don't know what version of Ubuntu you are trying to install.  If your system can support 22.04 you can create a startup disk from the Ubuntu desktop ISO and when the installer opens choose "other" and use the disk partitioning to set up your disk. 
This seems to be the minimum requirements for partitions. 
 Part 1  8meg partition setup as Bios Boot, You won't have to  format this partition.
 Part 2 256Meg to 512meg /Boot/EFI Partition. You won't have to format this partition but it will automatically format to fat32.
 Part 3 35Gig as /root  I format this one to ext4 but your choice.  This seem large for root but it will contain your swap file and some snap data. 
 Part 4 as /Home in any format you want.  I use ext4 myself. Then continue your install and It should get you running.  
Windows 10 requires a NTFS partition but Partition 1 and 2 will be necessary no matter what. And Grub should take care of the rest. 
Part 1 and 2 should work for Legacy and EFI . I use Legacy right now but legacy is speedily moving into history.

---

### Post by foobar34 on 2022-03-31
Thanks for your suggestions, but it doesn't apply to me. And I stupidly didn't mention the Ubuntu version (but it's in the pastebin). I'm on 20.04 LTS

I know that the partition scheme works, because if I use UEFI in the same disk it works just fine. And my boot problem has nothing to do with Ubuntu itself, since it never even gets that far. And for what is worth, I tried multiple sizes of the bot partition, from the recommended 1Mb of the wiki, al the way to 128Mb, makes no difference

My laptop BIOS doesn't recognize the NVME disk as bootable at all. It doesn't even show in the list of options. I don't know if it's an incompatibility with the protective MBR in the GPT disk, but before taking more drastic action (like converting my GPT disk to MBR), I want to be sure that the NVME disk is properly marked as bootable (which I'm not sure how to)

---

### Post by tea for one on 2022-03-31
When you use Windows 10 in UEFI mode, do all the Samsung features (e.g. battery charge limit to 85%) function OK?

---

### Post by foobar34 on 2022-04-01
> **tea for one said:**
> When you use Windows 10 in UEFI mode, do all the Samsung features (e.g. battery charge limit to 85%) function OK?
Yes and no. You need to use specific Samsung utilities to change those, none is managed by the OS itself

There's no way I could find to use the Samsung specific extensions (samung-laptop.ko) in UEFI mode. Due to a series of severe issues with the way Samsung implemented UEFI, the Linux disables any Samsung extensions when in UEFI mode. The main reason was a bricking bug you will find when you search for Samsung UEFI. Here's the commit that disables the module when in UEFI mode [https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=e0094244e41c4d0c7ad69920681972fc45d8ce34](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=e0094244e41c4d0c7ad69920681972fc45d8ce34)

The only way to use those extensions is to boot in BIOS mode. Or possibly recompile the module myself, but I'd rather not do it both to avoid non-standard components and the risk of bricking the laptop

---

### Post by foobar34 on 2022-04-04
UPDATE in case anyone reads this at some point in the future.

I tried everything to have my laptop recognize a GPT disk as a boot disk in BIOS mode, but nothing worked

In the end, I converted the GPT disk to MBR without losing data, and used boot-repair to ensure Ubuntu could boot again in BIOS mode. I also had to repair the Windows 10 installation on the same disk. I now have set my BIOS as CSM and UEFI, and can select either the Ubuntu or Windows images to boot. Ubuntu boots in BIOS mode, Windows in UEFI mode. I have not found a way to have GRUB be able to boot Ubuntu in BIOS mode and Windows 10 in EUFI mode, but it's really not a problem for me to use the BIOS boot menu that once in a blue moon that I want to run Windows on that laptop

To convert GPT to MBR without losing data I did

Complete backup, just in case
from a disk repair boot disk, in terminal type

[COLOR=#232629][FONT=ui-monospace]sudo dd if=/dev/sda bs=512 count=2048 of=backupfile
sudo gdisk /dev/nvme0n1
r
g
w
y
exit

[/FONT][/COLOR]The r command enters recovery mode for gdisk, g converts, w writes the changes, and y confirms you really want to write the new data on the disk. Plenty of online guides on using gdisk to convert between GPT and MBR[COLOR=#232629][FONT=ui-monospace]


[/FONT][/COLOR]

---

### Post by oldfred on 2022-04-04
You can boot Ubuntu in BIOS mode from gpt partitioned drive.
Its just you need a unformatted 1MB partition with the bios_grub flag (if using gparted) for the BIOS version of grub to install correctly.

When first converting from old BIOS system to a newer UEFI system I often had gpt drives with both ESP & bios_grub partitions, so I could just reinstall grub to convert from old system to new system.

---

### Post by foobar34 on 2022-04-05
> **oldfred said:**
> You can boot Ubuntu in BIOS mode from gpt partitioned drive.
Its just you need a unformatted 1MB partition with the bios_grub flag (if using gparted) for the BIOS version of grub to install correctly.

When first converting from old BIOS system to a newer UEFI system I often had gpt drives with both ESP & bios_grub partitions, so I could just reinstall grub to convert from old system to new system.
Well, as I said, I'm sure that the scenario works in general, and it actually worked for the USB stick I was using. It didn't work on the NVME disk in my NP530E5M and its weird BIOS. I'm positive that I had the right disk partitions and this can also be seen in the pastebin I enclosed (you can see more there)

[FONT=courier new][COLOR=#666666]============================[/COLOR] Boot Info After [COLOR=#B8860B]Repair[/COLOR] [COLOR=#666666]============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/nvme0n1 and looks at sector 
    [COLOR=#666666]2048[/COLOR] of the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and 
    looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],gpt4[COLOR=#666666])[/COLOR]/boot/grub[/FONT].

The problem is that the Samsung BIOS did not see that disk as bootable. The disk itself was bootable, but the BIOS did not allow me to choose it as a bootable disk, so there was no way to get the process started. It looks as if that BIOS wants a GPT disk with UEFI or a MBR disk without EFI in order to be bootable, no matter what settings I chose in the compatibility drop box. For what is worth, there are quite a few other problems with that BIOS, including the risk of bricking the laptop when messign around with UEFI settings

---


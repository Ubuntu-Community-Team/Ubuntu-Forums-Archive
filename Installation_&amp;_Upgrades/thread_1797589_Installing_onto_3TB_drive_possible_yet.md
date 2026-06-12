---
title: "Installing onto 3TB drive possible yet?"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Fartingbob on 2011-07-05
Just wondering is any of the desktop versions of ubuntu allow you to install onto a 3TB drive. I have a uEFI motherboard so thats not a problem, but you still need OS support for anything more than 2.19TB. Will it make a difference if i partition the drive first to 2 seperate partitions of less than 2TB? Guesing ill need the 64bit version if it does work?

Im asking because im building a fileserver/htpc and ideally i will be using 2 or 3 3TB drives, so if i can avoid having to use a smaller drive just to keep the OS happy that will better as im going for low power and noise, and adding another drive in there doesnt play well with either of those things. I need the desktop version not server as i will be using this as a HTPC so it has to have pretty menus and easy usability.

---

### Post by in-dust-rial on 2011-07-05
try this one:
[http://dlorch.github.com/hammer-linux/](http://dlorch.github.com/hammer-linux/)

---

### Post by srs5694 on 2011-07-05
You shouldn't have any problems because of your disk size (but see below), and you shouldn't need any exotic filesystem, either.

The 2 TiB limit is an issue for the Master Boot Record (MBR) partitioning system, and also (I'm told, but have not yet investigated in detail) for some BIOS calls used in booting the OS. Since you've got a UEFI-based system, you aren't affected by the BIOS issues (which just limit the system's ability to boot from files located above the 2 TiB mark), and part of the UEFI spec is the (relatively) new GUID Partition Table (GPT) specification, so you can leave MBR in the dust, where it belongs.

The problem you may run into is that Ubuntu's UEFI support is still pretty weak. Most importantly, if you install any OS before you install Ubuntu, you must back up the EFI System Partition (ESP), which is a partition that EFI and UEFI systems use to store boot loaders and associated data, since Ubuntu improperly and infuriatingly *erases* the ESP when it installs itself! If you want to install Windows 7 after Ubuntu, you may need to back up the ESP after you install Ubuntu, create a fresh FAT32 filesystem on it, restore Ubuntu's boot files to it, and adjust your /etc/fstab reference to it appropriately. (Fortunately, there's no need to deal with hidden boot sector code; a straight file backup and restore will do the trick.) The reason is that Ubuntu creates a FAT16 ESP, but the Windows 7 installer insists on seeing a FAT32 ESP -- at least, that was true in my tests. I've seen claims from one other person that Windows 7 was fine with a FAT16 ESP, but if that's true I don't know what variable was in play, so it's best to assume Windows will insist on a FAT32 ESP. If you're affected by Ubuntu's improper handling of the ESP (erasing it and creating it as FAT16), please chime in [here](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669) to let the developers know how important this bug is.

It's also possible you'll run into boot loader problems. In my experience, Ubuntu's GRUB 2 implementation for EFI is pretty weak; it works sometimes, but other times it fails completely or only boots occasionally. I've had better luck compiling GRUB 2 myself, as described [here,](https://help.ubuntu.com/community/UEFIBooting) and I've had much better luck on UEFI-based PCs by using [ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom) rather than GRUB 2. Any way you slice it, you may need to fiddle with your boot loader to get things working. Post back here with details if you run into problems.

---

### Post by Fartingbob on 2011-07-05
> **srs5694 said:**
> You shouldn't have any problems because of your disk size (but see below), and you shouldn't need any exotic filesystem, either.

The 2 TiB limit is an issue for the Master Boot Record (MBR) partitioning system, and also (I'm told, but have not yet investigated in detail) for some BIOS calls used in booting the OS. Since you've got a UEFI-based system, you aren't affected by the BIOS issues (which just limit the system's ability to boot from files located above the 2 TiB mark), and part of the UEFI spec is the (relatively) new GUID Partition Table (GPT) specification, so you can leave MBR in the dust, where it belongs.

The problem you may run into is that Ubuntu's UEFI support is still pretty weak. Most importantly, if you install any OS before you install Ubuntu, you must back up the EFI System Partition (ESP), which is a partition that EFI and UEFI systems use to store boot loaders and associated data, since Ubuntu improperly and infuriatingly *erases* the ESP when it installs itself! If you want to install Windows 7 after Ubuntu, you may need to back up the ESP after you install Ubuntu, create a fresh FAT32 filesystem on it, restore Ubuntu's boot files to it, and adjust your /etc/fstab reference to it appropriately. (Fortunately, there's no need to deal with hidden boot sector code; a straight file backup and restore will do the trick.) The reason is that Ubuntu creates a FAT16 ESP, but the Windows 7 installer insists on seeing a FAT32 ESP -- at least, that was true in my tests. I've seen claims from one other person that Windows 7 was fine with a FAT16 ESP, but if that's true I don't know what variable was in play, so it's best to assume Windows will insist on a FAT32 ESP. If you're affected by Ubuntu's improper handling of the ESP (erasing it and creating it as FAT16), please chime in [here]("https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669") to let the developers know how important this bug is.

It's also possible you'll run into boot loader problems. In my experience, Ubuntu's GRUB 2 implementation for EFI is pretty weak; it works sometimes, but other times it fails completely or only boots occasionally. I've had better luck compiling GRUB 2 myself, as described [here,]("https://help.ubuntu.com/community/UEFIBooting") and I've had much better luck on UEFI-based PCs by using [ELILO]("http://elilo.sourceforge.net/cgi-bin/blosxom") rather than GRUB 2. Any way you slice it, you may need to fiddle with your boot loader to get things working. Post back here with details if you run into problems.

Thank you. I will probably be installing next week sometime, dont plan on dual booting, just straight up ubuntu (probably 10.04). Does this make things easier with the ESP you were talking about? Is there anything i can do (try a different flavour of linux etc) that is more reliable of UEFI systems or should i just be ok once everything is installed?

---

### Post by in-dust-rial on 2011-07-05
oh yes yes!
the critical mark is 4TB
- sorry.
my reflexes.

---

### Post by srs5694 on 2011-07-05
> **Fartingbob said:**
> Thank you. I will probably be installing next week sometime, dont plan on dual booting, just straight up ubuntu (probably 10.04). Does this make things easier with the ESP you were talking about? Is there anything i can do (try a different flavour of linux etc) that is more reliable of UEFI systems or should i just be ok once everything is installed?

A straight-up Ubuntu installation is certainly simpler, since you don't need to be concerned with Windows' needs regarding the ESP. I recommend just proceeding with the installation in UEFI mode. If you're lucky, everything will work fine. If not, you may run into boot loader problems that you'll then have to solve. If that happens, you can either try resolving the problems while still using GRUB 2 or you can switch to another boot loader, such as ELILO or the EFI-enabled version of GRUB Legacy that Fedora uses.

---

### Post by Luke M on 2011-07-06
For those who are experts on this subject, is it possible for an MBR partition and the new partition style to coexist on the same drive? So you would create a boot partition (limited to 2TB) and a non-bootable partition. The MBR would contain the boot partition only, and the new partition style would contain both.

---

### Post by srs5694 on 2011-07-06
> **Luke M said:**
> For those who are experts on this subject, is it possible for an MBR partition and the new partition style to coexist on the same drive? So you would create a boot partition (limited to 2TB) and a non-bootable partition. The MBR would contain the boot partition only, and the new partition style would contain both.

What you describe is called a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) but it's not clear to me if what you hope to accomplish is what it actually does. Hybrid MBRs are most often found on Apple Macintoshes as a way to help Windows and OS X coexist. When confronted with a hybrid MBR, Windows "sees" only the MBR partitions, whereas OS X "sees" only the GPT partitions. (Linux is like OS X in this respect.) This is helpful because it enables Windows to install on a Mac using the Mac's BIOS compatibility mode -- ordinarily, Windows won't install to a GPT disk using BIOS, so to get Windows booting on a Mac, Apple had to find a workaround, and a hybrid MBR was what they used. Make no mistake, hybrid MBRs are ugly and dangerous hacks.

On a Linux-only system, a hybrid MBR buys you absolutely nothing, since Linux "sees" the GPT side and ignores the MBR side. Worse, hybrid MBRs are flaky and dangerous; if the partitions get out of sync because you've used a tool that adjusts one side or the other but not both, the inconsistency can result in data corruption if one tool or OS starts writing data in inappropriate places. Some GPT tools (such as at least some versions of GParted) also routinely clear the MBR partition table, so if you may need to re-create them from time to time.

When dual-booting Linux and Windows on a BIOS-based computer, it's best to stick with MBR to avoid these problems. If you want to use an over-2TiB disk on such a computer, the best solution is to use *another* disk to boot Windows and use GPT on the big disk; Windows Vista and 7 will be happy with that, and Linux can even boot from the GPT disk, if that's desirable. If you really must have a Linux/Windows dual boot on an over-2TiB disk, then a hybrid MBR could help, since you could put the Windows partitions below the 2 TiB mark as MBR. Another option would be to [use UEFI DUET](http://www.rodsbooks.com/bios2uefi/) to make Windows boot as if on a UEFI system. It's also possible, by careful placement of partitions, to "stretch" the MBR limit to 4 TiB. This doesn't work with all OSes, though, and even with OSes that do seem OK with it, I can't guarantee that all partitioning tools will work well with it.

When dual-booting Linux and OS X on a Mac, IMHO it's best to forego the hybrid MBR, since the hybrid MBR does neither OS any good. Most Linux installation procedures for Macs, however, rely on installing Linux in BIOS mode and using a hybrid MBR. It's possible to do it otherwise, but there can be drawbacks related to video and other hardware accessibility on some models. The bottom line is that this topic is rather complex, but from the point of view of the partitioning task alone, the hybrid MBR gains you nothing but adds complexity and risk.

If you have a specific scenario in which you think a hybrid MBR (or some other type of odd partition layout) would help, please elaborate on what it is.

---

### Post by Luke M on 2011-07-06
> **srs5694 said:**
> If you have a specific scenario in which you think a hybrid MBR (or some other type of odd partition layout) would help, please elaborate on what it is.
 
Old operating systems, only one drive. Another question: when using a new OS but old BIOS, can you use a single >2TB partition or do you need to create two partitions so the boot files are guaranteed to be in the lower 2TB?

---

### Post by srs5694 on 2011-07-06
> **Luke M said:**
> Old operating systems, only one drive.

If you've got a sub-2TiB disk, then I'd recommend using a straight-up MBR configuration in that situation. If it's an over-2TiB disk, then a hybrid MBR GPT disk may be the only option if you must also dual boot on that disk. You might want to look into virtualization as an alternative, though. Many old OSes run quite well in VirtualBox, for instance -- often better than they would natively, since old OSes often lack driver support for modern hardware. Getting a second disk for the legacy OS(es) is also worth considering, although I realize this option isn't always practical.

> Another question: when using a new OS but old BIOS, can you use a single >2TB partition or do you need to create two partitions so the boot files are guaranteed to be in the lower 2TB?

I recommend the latter. [This page](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit) claims that it's impossible to boot from beyond the 2TiB limit with a BIOS. Although I haven't investigated the matter thoroughly, I have been unable to boot Linux from such partitions in a VirtualBox environment using GRUB 2.

Besides which, IMHO it's inadvisable to create a single >2TiB partition for both OS and user data. As a general rule, it's wise to separate system files from user files; doing so simplifies certain types of system upgrade and re-installation tasks. The problems with not doing this become greater the larger the disk, since there are situations in which you might need to back up all your data in order to re-install the OS if you put it all in one partition, and backing up over 2 TiB of data is a non-trivial undertaking.

---

### Post by YesWeCan on 2011-07-06
> **Luke M said:**
> For those who are experts on this subject, is it possible for an MBR partition and the new partition style to coexist on the same drive? So you would create a boot partition (limited to 2TB) and a non-bootable partition. The MBR would contain the boot partition only, and the new partition style would contain both.
Yes.

To be GPT compliant the partition table in the MBR would not be usable for booting, so the MBR code would need to be custom and would have to know to boot a specific partition boot code. This partition boot code could be Windows' or Grub's for instance. Since the PT is not used it does not limit the maximum sector address where the bootable partition can be, although the bios may have a limitation.

If you have Ubuntu in mind there is an additional issue. Grub's MBR code boots Grub's kernel file. Normally, the kernel fiel is installed to about 50 specific sectors just after the MBR where it is easy to find and won't move. It is possible, using 'grub-install --force', to instead put the boot code in a partition and leave the kernel code in Ubuntu's /boot/grub. But this is considered unreliable (grub-install will whine) because the boot code has to know the sector address of the kernel file and it is possible for the kernel file to be relocated or re-segmented by the file system.

If you are interested in booting Ubuntu on a GPT disk using standard Grub2 there is a way to work around the reliability issue. Send me a message.

---

### Post by srs5694 on 2011-07-06
> **YesWeCan said:**
> [quote=Luke M]For those who are experts on this subject, is it possible for an MBR partition and the new partition style to coexist on the same drive? So you would create a boot partition (limited to 2TB) and a non-bootable partition. The MBR would contain the boot partition only, and the new partition style would contain both.Yes.

To be GPT compliant the partition table in the MBR would not be usable for booting, so the MBR code would need to be custom and would have to know to boot a specific partition boot code. This partition boot code could be Windows' or Grub's for instance. Since the PT is not used it does not limit the maximum sector address where the bootable partition can be, although the bios may have a limitation.[/quote]

Although your reply is mostly accurate when it comes to an MBR-based *boot loader*, Luke M's question specified "an MBR partition," so I believe he's asking about the MBR partition table co-existing with a GUID Partition Table. These are two entirely distinct issues, although they can interact (for instance, there's the question of how a boot loader treats a hybrid MBR).

---

### Post by YesWeCan on 2011-07-06
That's very interesting, Rod, I'm sure. But my reply was to Luke who is in the best position to judge whether my entirely accurate reply is of any help to him.

---

### Post by psusi on 2011-07-06
> **Luke M said:**
> Old operating systems, only one drive. Another question: when using a new OS but old BIOS, can you use a single >2TB partition or do you need to create two partitions so the boot files are guaranteed to be in the lower 2TB?

The bios can not see beyond 2TB at all, so the boot loader needs to live below that point so the bios can load it.  With GRUB2, this can be done on a GPT partitioned disk by creating the bios_grub partition under the 2tb mark, which only needs to be 1mb in size.

---

### Post by Luke M on 2011-07-07
> **psusi said:**
> The bios can not see beyond 2TB at all, so the boot loader needs to live below that point so the bios can load it.  With GRUB2, this can be done on a GPT partitioned disk by creating the bios_grub partition under the 2tb mark, which only needs to be 1mb in size.
 
But isn't the BIOS also used to load the kernel? GRUB doesn't have disk device drivers built in (or does it?)

---

### Post by psusi on 2011-07-07
> **Luke M said:**
> But isn't the BIOS also used to load the kernel? GRUB doesn't have disk device drivers built in (or does it?)

Actually it does have a disk driver but I have never tried it.  Usually it does use the bios on bios based machines, in which case /boot also needs to be below 2tb.  I forgot about that.

---

### Post by YesWeCan on 2011-07-07
> **psusi said:**
> Actually it does have a disk driver but I have never tried it.  Usually it does use the bios on bios based machines, in which case /boot also needs to be below 2tb.  I forgot about that.
Yes. Also, the Grub boot code uses 4 bytes to represent the sector address of the kernel. I believe it is feasible to place the /boot or grub-bios partition as a logical partition beyond 2TB with the right daisy-chaining boot codes, but I haven't tested this.

---


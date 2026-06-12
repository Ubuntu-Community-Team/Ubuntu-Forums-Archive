---
title: "Can't boot - modify boot order via efibootmgr?"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by Amblyomma on 2012-08-13
My first computer build went amazingly smooth from a hardware stand point, but the OS installation is making up for it.

Here's the build:
AMD A6 3650 quad core APU
MSI A75A-G55 mobo with UEFI bios
Corsair 8GB RAM
Seagate barracuda green HDD (1.5TB)
LiteOn Blu ray combo drive

It's a budget build HTPC. I really wanted it to handle Netflix, so I initially installed XP on it and attempted to activate an old license, but no dice. So I figured it wouldn't kill us to continue to watch Netflix on the Xbox and installed 12.04 via USB. Had problems with the screen blacking out after the initial boot menu on the install, so I added nomodeset to the boot command. The install went smoothly from then on, but every time I try to reboot post install I get "Reboot and select proper boot device". The HDD was listed as the first boot option in the bios, but it isn't listed as a UEFI device (only my thumb drive and the shell are listed as UEFI options). 

I searched here and other places online, realized I probably needed to double check that the partition table was set up correctly and add the HDD as an entry on the UEFI boot manager. Reinstalled (multiple times) with the final partition table looking like this:

sda1, efi, fat32, 250Mb
sda2, ext4, [most of 1.5TB], mount point '/'
sda3, swap [Ubuntu defaults]
sda1 set as the boot partition in the dropdown menu

Next tried to add the HDD as a UEFI boot option via efibootmgr. I booted into the EFI shell and tried a variety of different commands, but the shell won't execute anything except "quit". efibootmgr -c just gets me an 'unrecognized command' error. 

Feeling really dumb and hating on UEFI right now. Missing the old bios (breaking out the tiny fiddle for myself).

---

### Post by drmrgd on 2012-08-13
Out of curiosity, after you re-partitioned and reinstalled (pointing Grub to the efi_boot partition if I understand you), did you try to just reboot and see if the system loads?  It looks like you have everything set up correctly, and assuming you installed Ubuntu in UEFI mode (just choose the boot the .iso as UEFI and not BIOS), it should set everything up for you as if it were still BIOS based.  I'm not sure that you need to manually place an entry with the efibootmgr anymore.

You might also try Boot Repair, as I'm told the latest version works really well with UEFI systems now:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Amblyomma on 2012-08-13
> **drmrgd said:**
> Out of curiosity, after you re-partitioned and reinstalled (pointing Grub to the efi_boot partition if I understand you), did you try to just reboot and see if the system loads? It looks like you have everything set up correctly, and assuming you installed Ubuntu in UEFI mode (just choose the boot the .iso as UEFI and not BIOS), it should set everything up for you as if it were still BIOS based. I'm not sure that you need to manually place an entry with the efibootmgr anymore.
 
You might also try Boot Repair, as I'm told the latest version works really well with UEFI systems now:
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
I tried a reboot after every reinstall. I always got the same error. And yes, I did point GRUB at the efi partition.
 
I did install in UEFI mode. By default the installer was setting up a 100MB efi partition. I upped the size on the advice of one of the threads I read.
 
If no one has any other suggestions, I'll try the boot repair tool tonight. I was leaning in that direction, but glad to have someone confirm there weren't any obvious problems. I think I choose to blame the problems on the initial XP install until someone proves otherwise :P

---

### Post by oldfred on 2012-08-13
With XP you have a lot of issues that will not work with UEFI. 

XP does not work with gpt partitioning & UEFI needs gpt partitions. You also need UEFI/BIOS set to AHCI and XP needs extra drivers for that. XP prefers to be the first partition but does not have to be, but the efi partition is supposed to be first.

I find with the very large drives that a smaller system partition also works better. There was (is?) a bug in grub2 that it does not boot correctly on very large / partitions. So a separate /home or data partition(s) work better anyway.

If you will not be using BIOS you do not need the bios_grub, but it is not large & gives the flexibility to install in BIOS mode. You have to boot the 64bit version in UEFI mode to get the UEFI installer.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
I know nothing about steam games but understand they are very large - 4 to 5GB.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by Amblyomma on 2012-08-13
> **drmrgd said:**
>  You might also try Boot Repair, as I'm told the latest version works really well with UEFI systems now:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Running this from the USB live stick now ... it's been sitting on the "Scanning systems. This may require several minutes ..." screen for going on 3 hours now. I know it's a 1.5TB drive, but geez. Is it stuck? That messed up?

Oldfred: I was trying to install over XP, not dual boot. Which was sad, if for no other reason than I put a fair amount of effort figuring out how to get around just the issues you mentioned.

I think I will end the boot repair scan and try doing a pre-partition with the setup you suggested.

Thanks! I'll post back as soon as I know something.

---

### Post by oldfred on 2012-08-13
While with a lot of partitions or installs like I have Boot-Repair can take a few minutes. But if it has been 3 hours some partition will not mount. 

Either it is damaged like a NTFS needing chkdsk or shutdown abnormally and if Linux needs e2fsck. That often is the issue. 

But that may also appear with gparted as it will not load damaged partition either.

---

### Post by Amblyomma on 2012-08-13
> **oldfred said:**
> While with a lot of partitions or installs like I have Boot-Repair can take a few minutes. But if it has been 3 hours some partition will not mount. 

Either it is damaged like a NTFS needing chkdsk or shutdown abnormally and if Linux needs e2fsck. That often is the issue. 

But that may also appear with gparted as it will not load damaged partition either.

When I went to end the process, it suddenly started running the GUI for Boot Repair. I just clicked on the standard repair button to start. The output can be found here: [http://paste.ubuntu.com/1145940/]("http://paste.ubuntu.com/1145940/")

Does this change anyone's advice? It appears to be a problem files not being where they're supposed to be (my highly technical assessment). Your patience is very much appreciated.

[edit] Despite the supposed repair, it still doesn't boot. The HDD isn't listed in the bios as a UEFI device.

---

### Post by oldfred on 2012-08-13
It looks like it should boot, but there was (is still?) a bug in grub2 that makes it not work with very large / (root) partitions. Installer always assumed smaller drives, but now with multi-gigabyte drives boot files may be scattered all over drive. Then it just does not work.

Much better to have a small / (root) partition and a separate larger /home or data partition(s). 

About half the users I suggested just using gparted to shrink the / partition to 50 or 100GB worked. Others I am not sure if it worked or not. With  old BIOS  systems with a 137GB boot limit, we had to have a separate /boot with just grub & kernel files in a separate very small partition near the beginning of the drive. That also works and I think that is what Boot Repair suggests. But if / is smaller and near beginning of drive that also works.

For the Total space you want for Ubuntu, if just UEFI, you do not need bios_grub as that is for BIOS booting with gpt drives, but it is not a lot of space either:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
I know nothing about steam games but understand they are very large - 4 to 5GB.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Amblyomma on 2012-08-16
Apparently the main problem was that I grub2 was choking on my HDD size. I used gparted to wipe and repartition the disc like you suggested (tried resizing first, but gparted choked on the disc size too), then did a reinstall to the new partitions.

To be on the safe side, I broke all of my "extra" space down into 3 partitions of roughly equal size, so there's no partition >500GB on the drive. Probably didn't make a difference, but I was getting extremely tired of reinstalling.

It still didn't boot on the first try (black screen with boot: at the top), but I ran the Boot Repair tool again (from the Ubuntu live USB) and reset the boot drive order in the bios and viola! A working installation :D

Many thanks to Oldfred.

---

### Post by YannBuntu on 2012-08-16
Hello

> **oldfred said:**
> It looks like it should boot, but there was (is still?) a bug in grub2 that makes it not work with very large / (root) partitions.

I have seen several similar cases. My guess is that it is a GRUB regression: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887)

But this is the first time i see it on a EFI install !

**@Amblyomma:** please could you indicate your new [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL?  (in order to compare with previous ones)

---

### Post by Amblyomma on 2012-08-16
[Boot Repair link]("http://paste.ubuntu.com/1148066")

I hope it's helpful.  :) I'm moving on to hunting down drivers ...

---

### Post by YannBuntu on 2012-08-16
Thanks!

Previously the /boot (contained in / ) partition ended at 1492GB (>100GB) from the start of the disk.
Now it ends at 52.7GB (<100GB).

In order to confirm that this is a bug regression, it would be nice if you could try installing 11.10 in dualboot at the end of the disk, and see if its (old version of) GRUB works or not.
(just in case, backup your sda1/efi/ubuntu/grubx64.efi file before)

---

### Post by Amblyomma on 2012-08-16
You all have been really helpful, but I've got some installation fatigue right now.

How much would it help the community/development to have this confirmed? I'd like to help if it would be, well, helpful, but currently _it's working_ and I'd like it to stay that way :)

But I can try it maybe over the weekend (starts looking for her copy of clonezilla).

---

### Post by oldfred on 2012-08-16
It looks like you ended up booting in BIOS mode, using the MBR and bios_grub partitions. Your entry of the efi partition in fstab is commented out. You also installed grub to the partition which should never be required, but will not hurt anything.

Both Yann & I have seen this type of error and cannot really track it down. We are not developers of Ubuntu although Yann is continuously improving his Boot-Repair tool.  I still think it may be related to certain BIOS and settings in BIOS, but may be the grub error or both. Can you confirm if you are in AHCI not IDE mode, and/or LBA? But different vendors label that info differently in UEFI/BIOS so it sometimes is not what I think it is.

I always like to have multiple installs just to test the next version or have a backup way to boot. But I have multiple installs on multiple hard drives and flash drives. I have multiple 25GB / (root) partitions on my larger 650GB drive.

If you do install use manual install & choose to not install grub or install to the same partition as you are installing into. Then when you reboot run sudo update-grub to find your new install. Any of the auto install options will overwrite you current boot loader, but that can easily be repaired.

---

### Post by YannBuntu on 2012-08-16
As you are new here, first discover and enjoy Ubuntu :)

EDIT: please could you install Boot-Repair into your installed Ubuntu, and tell me the [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL obtained from it? (not from a CD)

---

### Post by Amblyomma on 2012-08-19
I do know my Bios was set to ACHI mode (not on the first install, but on everything you have data from).

I'll run the boot repair from the hdd and report back for you, Yann. Dealing with some graphics driver problems right now that are making me want to scream (blasted AMD integrated nightmare).

---

### Post by Amblyomma on 2012-08-19
[http://paste.ubuntu.com/1155807/](http://paste.ubuntu.com/1155807/)

---

### Post by YannBuntu on 2012-08-20
thanks.
It confirms you are using the BIOS-boot partition now (you don't use EFI any more).

To summarize:
- You had problem when you used EFI + Ubuntu partition far from the start of the disk.
- Now your system works without EFI + Ubuntu partition close from the start of the disk.

The initial GRUB problem may be due to EFI or to the position of the Ubuntu partition. Investigating on it would be helpful for GRUB devs, but would require testing big changes that may break your system. First discover and enjoy Ubuntu, we'll do the tests when you are ready to break your system ;)

---


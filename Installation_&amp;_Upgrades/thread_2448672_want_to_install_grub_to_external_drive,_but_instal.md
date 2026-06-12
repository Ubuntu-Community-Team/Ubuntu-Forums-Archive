---
title: "want to install grub to external drive, but installer changes it to internal drive"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by unprovoked2000 on 2020-08-11
I am trying to install Ubuntu 20.04.1 LTS to a portable external drive.  The laptop I am using has two internal NVMe drives for Windows 10 and data, ando I want my Ubuntu installation to only be on the external drive.  However, I tried multiple times, and grub keeps getting installed to the NVMe drive instead!

From the bootable live USB, I select Try Ubuntu, and then partition my external drive (/dev/sdb):

[FONT=courier new]Device     Boot      Start        End    Sectors  Size Id Type
/dev/sdb1  *          2048     514047     512000  250M ef EFI (FAT-12/16/32)
/dev/sdb2           514048 1049090047 1048576000  500G 8e Linux LVM
/dev/sdb3       1049090048 1091033087   41943040   20G  7 HPFS/NTFS/exFAT

[/FONT]
/dev/sdb2 is an LVM partition (which I am trying to learn about) where I created logical volumes for swap, /, and /home.

Then within the Live Desktop, I select Install Ubuntu and the something else option.  By default, the installer chooses /dev/nvme0n1p1 from the internal Windows 10 NVMe drive.  I double click that and change the default use as EFI to use as nothing, so the type gets changed from efi to fat32.  Then I double click /dev/sdb and select use as efi.  I then select the lvm partitions for swap, /, and home.  I also make sure to change "Use device for boot loader installation" from /dev/nvme0 to /dev/sdb.  See the screenshots below:

[ATTACH=CONFIG]286678[/ATTACH][ATTACH=CONFIG]286679[/ATTACH]


Then I start the installation.  However, despite my choices above, it still ends up selecting /dev/nvme0n1p1 for grub, as shown by lsblk during the install:


[FONT=courier new]NAME               MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb                  8:16   0   1.8T  0 disk 
&#9500;&#9472;sdb1               8:17   0   250M  0 part                     [COLOR=#ff0000][WHY NOT HERE?][/COLOR]
&#9500;&#9472;sdb2               8:18   0   500G  0 part 
&#9474; &#9500;&#9472;volume1-lvswap 253:0    0    72G  0 lvm  [SWAP]
&#9474; &#9500;&#9472;volume1-lvroot 253:1    0    20G  0 lvm  /target
&#9474; &#9492;&#9472;volume1-lvhome 253:2    0   250G  0 lvm  /target/home
&#9492;&#9472;sdb3               8:19   0    20G  0 part 
nvme0n1            259:0    0   1.8T  0 disk 
&#9500;&#9472;nvme0n1p1        259:1    0   260M  0 part /target/boot/efi    [COLOR=#ff0000][WHY HERE??][/COLOR]
&#9500;&#9472;nvme0n1p2        259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3        259:3    0   1.8T  0 part 
&#9500;&#9472;nvme0n1p4        259:4    0     1G  0 part 
&#9492;&#9472;nvme0n1p5        259:5    0  12.7G  0 part 
[/FONT]
[ATTACH=CONFIG]286680[/ATTACH]

I have tried this three times, each time being super careful about the settings, and yet the result is the same.  Why is nvme0n1p1 selected as /target/boot/efi when I thought I told the installer to use /dev/sdb1?

Can you please help me with suggestions on how I can get the installer to use /dev/sdb1 (the portable external drive) instead of the internal NVMe drive for the grub stuff?

---

### Post by oldfred on 2020-08-11
This is what I do:
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Others have posted that removing boot/esp flags from internal drive and then specifying the external drive, that will work. It has not for me, but I boot ISO directly using grub2's loopmount, so not standard flash drive installer.
Others have posted physically or logically in UEFI disconnecting all internal drives, works.

Grub boots external drive from ubuntu entry in UEFI as if internal drive using /EFI/ubuntu.
But UEFI directly boots all external drives using /EFI/Boot/bootx64.efi. Grub now also creates that folder & file with an install.

Be sure to update fstab with UUID of ESP on external drive. Then updates will reinstall to correct place.

You can just reinstall grub to external drive. Be sure to use --removable

---

### Post by unprovoked2000 on 2020-08-11
Thanks so much, @oldfred! I am looking at your comments at [#23]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379/comments/23") and [#26]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379/comments/26").

So the key is to set up user and password, but do not press continue on that screen yet?  Then in a terminal, first run [COLOR=#333333][FONT=monospace]sudo umount /target/boot/efi [/FONT][/COLOR]followed by [COLOR=#333333][FONT=monospace]sudo umount /dev/sdb1 /target/boot/efi ([/FONT][/COLOR]where /dev/sdb1 is the partition I actually want to install grub to).  And then press continue on the installer screen?

I will give that a try tonight and report back, but if you have any corrections to what I should do regarding the summary above, please let me know.

I thought about physically unplugging the NVMe drives, but with many torx screws and a spudger required to open my laptop, I was hoping to avoid that.

My laptop BIOS is quite limited and doesn't allow disabling drives in the BIOS.  I also thought about hiding the NVMe drive from Linux, but I wasn't able to figure out the correct equivalent of [COLOR=#242729][FONT=Consolas]echo 1 > /sys/block/sdX/device/delete [/FONT][/COLOR]which works for sdX type drives, but not for NVMe drives.

---

### Post by oldfred on 2020-08-11
I immediately open terminal and run a mount command.
But using Something Else install option the mount of the ESP does not show immediately.
I always click to not use my swap which seems to work as I have an old swap partition on internal drives. But clicking in partitions to not use internal ESP and using external drive's ESP seems not not do anything.

So after I put in user name & password but before clicking next, I go back to terminal and check mount again. Then umount one ESP & mount the correct one.

But later I found it still used the UUID of first ESP in update or creation of fstab. So I later have to edit that with correct UUID.

---

### Post by pbear42 on 2020-08-11
> **unprovoked2000 said:**
> I also thought about hiding the NVMe drive from Linux, but I wasn't able to figure out ...
What's always worked for me (learned [here]("https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079")) is opening GParted before running the installer, removing the boot/esp flags from the internal drive's EFI partition, installing, then using GParted to restore the boot/esp flags.  The last step isn't actually necessary, as Windows can boot without the flags, but leave-it-as-you-found-it is such a foundational problem solving principle that I can't bring myself not to.  Besides, only takes a few seconds.  Or use oldfred's method, if that seems simpler to you.

Important.  Have you tried booting Windows without the USB drive attached?  I would expect it not to work.  The simplest fix is this.  Attach the USB drive and boot into Windows.  Open Power Shell or Command Prompt.  Run bcdboot C:\Windows.  This will reinstall the Windows boot loader from backup ([link]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di")).   Alternatively, if you're familiar with efibootmgr, you can simply delete the ubuntu entry from NVRAM.  Either method works.

By the way, this [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488") is now seven years old.  Four LTS releases since then, and still no fix.

---

### Post by unprovoked2000 on 2020-08-11
Thank for the followup replies!  For booting Windows without the USB drive attached, I would also expect it not to work.  I was going to follow a tutorial ([https://www.58bits.com/blog/2020/02/28/how-create-truly-portable-ubuntu-installation-external-usb-hdd-or-ssd](https://www.58bits.com/blog/2020/02/28/how-create-truly-portable-ubuntu-installation-external-usb-hdd-or-ssd)) to fix up Windows boot afterwards. Alternatively, since I have the Windows boot partition backed up (with Macrium Reflect), I can restore the Windows boot partition in case of any problems.  However, bcdboot is great to know about, and I will read about it!

For the installation retry, I was about to try oldfred's method, and I verified that once the set user and password screen appeared, lstblk already showed the /target/* mounts, so I am confident it would work.

However, out of curiosity, I figured out a possible (? don't know how dangerous it is) method to remove the NVMe drives from Linux.  I used lspci and figured out candidate addresses for my NVMe drives.  These were the best candidates:

[FONT=courier new]# lspci
[snip]
03:00.0 Non-Volatile memory controller: Silicon Motion, Inc. Device 2262 (rev 03)
04:00.0 Non-Volatile memory controller: Silicon Motion, Inc. Device 2262 (rev 03)[/FONT]

I then checked /sys/bus/pci/devices/0000\:03\:00.0/ and could see an nvme/nvme0 subdirectory.
Likewise for /sys/bus/pci/devices/0000\:04\:00.0/nvme/nvme1.

So I did (all from root, after first making sure nothing on the NVMe was mounted):

[FONT=courier new]# echo 1 >  /sys/bus/pci/devices/0000\:03\:00.0/remove
# echo 1 >  /sys/bus/pci/devices/0000\:04\:00.0/remove [/FONT]

There was one message in syslog for each which I didn't understand:

[FONT=courier new]kernel: nvme nvme0: failed to set APST feature (-19)
kernel: nvme nvme1: failed to set APST feature (-19)[/FONT]

but the nvme devices were gone from /dev and lsblk.

When I ran the Ubutnu installer afterwards, there was no confusion with grub installing to the wrong drive, since my external hard drive was the only one (other than the Live USB) visible to the kernel.

The system booted fine afterwards, and since it didn't even know about the Windows 10 drive, I think Windows 10 will boot fine without the external USB drive plugged in. (If that's is not the case, I will follow up).

The only thing I didn't do (because I am not confident yet) is to re-run grub-install with the --removable flag.  Is re-running [FONT=courier new]grub-install --removable[/FONT] necessary at this point?  My goal is basically to use this as a Windows 10 laptop for normal usage, but have the flexibility to plug in this external drive to have a portable Linux system.

Thanks again for all of useful info in the comments!

---

### Post by oldfred on 2020-08-11
You should not have to reinstall grub.
And if you have not edited fstab, it may reinstall to wrong drive.

If in UEFI you set external drive as first in boot order and also run sudo update-grub, you will be able to boot Ubuntu & also have Windows in grub menu. Only works if Windows fast start up is off.

And then if you remove external drive & Windows is second in boot order, it should auto boot as external drive not found.

---

### Post by unprovoked2000 on 2020-08-12
[QUOTE=oldfred;13978999]You should not have to reinstall grub.
And if you have not edited fstab, it may reinstall to wrong drive.
/QUOTE]

Thanks! I have not edited /etc/fstab, since the NVMe drives were invisible during install. Here are the relevant fstab lines:

[FONT=courier new]# /boot/efi was on /dev/sdb1 during installation
UUID=*<uuid of /dev/sdb1>*  /boot/efi       vfat    umask=0077      0       1[/FONT]

I have one more concern.  If I update the kernel, for example with sudo apt-get dist-upgrade, and a new kernel version gets installed, I think update-grub would run during the dist-upgrade. If the Windows 10 NVMe drives are not hidden during that process, will a kernel upgrade / update-grub end up messing with the NVMe boot partitions again?

I really need to learn more about grub and the boot process. My total lack of understanding of UEFI, Secure Boot, grub, etc makes me feel  intimidated by boot-related issues.

---

### Post by oldfred on 2020-08-12
The normal sudo grub-update is more a refresh of the grub menu. So it can see a new kernel.
I think only a major grub update or re-install would change files in the ESP. And that then is based on the mount of the efi partition. And if the UUID is for your correct ESP on external drive you should be ok.
There was a major grub update for Boot Hole with Secure Boot. But some with Secure Boot on had issues and another grub update came thru. I do not have Secure Boot on, and updates did not cause me any issues. But I now have newer files in /EFI/ubuntu.

Many users with errors on grub have with UEFI a wrong UUID or with BIOS there is a configuration file that grub uses to know where to do a full update. If that is wrong, update goes into wrong place, but boot then tries to boot using old version of grub and you end up with grub error.

I have some links to more info on grub in the link in my signature below. I maybe need to review to make sure still current & perhaps add a bit more.

---

### Post by unprovoked2000 on 2020-08-12
Thanks again for all of your help. I'll check out that link in your signature. Thread marked as solved (didn't know about Thread Tools until now)

---


---
title: "Why can't I boot into Ubuntu?"
date: 2017-05-28
forum: Installation &amp; Upgrades
---

### Post by YLTO on 2017-05-28
Today, I have an unusual case with this laptop lenovo v310-14-ISK. The problem is whenever I install through "Something else" path, I can't get the system boot into Ubuntu (which I'd been doing successfully several times in other PC/laptop), instead when I choose "Erase disk and install Xubuntu" path it work like charm. Still I have to go for "Something else" path because I need partition out my /home. 

Here's how I do the partition:

[IMG]http://i.imgur.com/vtBSucn.jpg[/IMG]


[IMG]http://i.imgur.com/wDjZF8A.jpg[/IMG]

Then when it finish and reboot, I got this view instead.

[IMG]http://i.imgur.com/eqCYRGg.jpg[/IMG]


Can you help me figure out what's wrong with the installation?

---

### Post by ubfan1 on 2017-05-28
I'd guess you formatted your EFI partition (sda1) to ext4, making it unusable for booting in UEFI mode.   UEFI mode is usually associated wth a GPT partitioning, not MSDOS, but that's because when running Windows on UEFI, the disk must be GPT -- Ubuntu doesn't care.  Put a FAT filesystem back onto sda1, (flag it boot), and the UEFI install should work.  For future ease in changing partitions, you might consider using GPT partitioning, then you would not need an extended partition to add any more.

---

### Post by oldfred on 2017-05-28
Does not the ubuntu entry in UEFI boot Ubuntu?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Some other posts on similar models.

  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
[QUOTE]Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather

---

### Post by YLTO on 2017-05-28
> **ubfan1 said:**
> I'd guess you formatted your EFI partition (sda1) to ext4, making it unusable for booting in UEFI mode.   UEFI mode is usually associated wth a GPT partitioning, not MSDOS, but that's because when running Windows on UEFI, the disk must be GPT -- Ubuntu doesn't care.  Put a FAT filesystem back onto sda1, (flag it boot), and the UEFI install should work.  For future ease in changing partitions, you might consider using GPT partitioning, then you would not need an extended partition to add any more.
[IMG]http://i.imgur.com/u4nF68B.jpg[/IMG]

Yes that's what I did but it didn't work.

I tried to boot via USB with Supergrub2 on and it could boot into the xubuntu.

---

### Post by oldfred on 2017-05-28
Please attach screen shots. Not everyone has high speed Internet.
Easy to do with Forum's advanced editor and paperclip icon.

Did you run Boot-Repair?

---

### Post by YLTO on 2017-05-29
> **oldfred said:**
> Please attach screen shots. Not everyone has high speed Internet.
Easy to do with Forum's advanced editor and paperclip icon.

Did you run Boot-Repair?

Sorry. Here's the attachment.
[ATTACH=CONFIG]275341[/ATTACH]

I've tried the boot-repair but the problem still persist.

---

### Post by yancek on 2017-05-29
> 
I've tried the boot-repair but the problem still persist. 		

Boot repair will give you a link you can post here so that others with more knowledge can take a look at it and hopefully make a suggestion.  That's what you were asked to do and until you do that, there isn't much the members can do but guess at your problem.

---

### Post by YLTO on 2017-05-30
> **yancek said:**
> Boot repair will give you a link you can post here so that others with more knowledge can take a look at it and hopefully make a suggestion.  That's what you were asked to do and until you do that, there isn't much the members can do but guess at your problem.

[http://paste.ubuntu.com/24711719/](http://paste.ubuntu.com/24711719/)

You mean this?

---

### Post by oldfred on 2017-05-30
You are showing corruption and just about every partition?
Boot-Repair tried to run a basic fsck but still errors.

You did have at least one install as UEFI has a ubuntu entry and that is the last part of the install.

Is drive set for AHCI, not RAID nor IDE. And not any Intel SRT or similar setting which looks like RAID to Linux?

What does Disks utility  show. In upper right corner icon is Smart Status which shows info on drive. All I know is good/bad, but it also can run test and report lots of data.

       Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]https://bbs.archlinux.org/viewtopic.php?id=164185

      [/URL]
 To see all the ext4 partitions, report showed sda3 & sda4.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partitions
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

    [URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]
[/URL]

---

### Post by YLTO on 2017-05-31
> **oldfred said:**
> you are showing corruption and just about every partition?
Boot-repair tried to run a basic fsck but still errors.

You did have at least one install as uefi has a ubuntu entry and that is the last part of the install.

Is drive set for ahci, not raid nor ide. And not any intel srt or similar setting which looks like raid to linux?



ahci

> **oldfred said:**
> 
what does disks utility  show. In upper right corner icon is smart status which shows info on drive. All i know is good/bad, but it also can run test and report lots of data.


Where, you mean when I boot into boot-repair? I don't see any icon in upper right corner.

[ATTACH=CONFIG]275372[/ATTACH]

> **oldfred said:**
> 
       must be unmounted
sudo dosfsck -t -a -w /dev/sda1
the -a seems to help in clearing dirty bit
[URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]https://bbs.archlinux.org/viewtopic.php?id=164185
[/URL]
Done. 
[ATTACH=CONFIG]275367[/ATTACH]


> **oldfred said:**
> 
 to see all the ext4 partitions, report showed sda3 & sda4.
Sudo parted -l

Done
[ATTACH=CONFIG]275369[/ATTACH]

> **oldfred said:**
> 

#from livedvd/flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partitions

live FD of what? live FD of boot-repair?



> **oldfred said:**
> 
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -c0 -p -f -v /dev/sdb1

Done

[ATTACH=CONFIG]275370[/ATTACH]

> **oldfred said:**
> 
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

    [URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]
[/URL]
Done
[ATTACH=CONFIG]275368[/ATTACH]

---

### Post by oldfred on 2017-05-31
You tried to run on example, you have to run on your partitions.
And if posting terminal output just copy & paste to forum. If very long use code tags or # in  forum advanced editor.

To see all the ext4 partitions, report showed sda3 & sda4.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary,  [COLOR=#b22222]change example shown[/COLOR] with partition sdb1 to your partitions

Disks or Disk utility is another application in live installer. (the flash drive you are using in live mode).
Older version screen shots attached, still essentially the same.

---

### Post by YLTO on 2017-06-01
> **oldfred said:**
> 
[COLOR=#000000]You tried to run on example, you have to run on your partitions.[/COLOR]
[COLOR=#000000]And if posting terminal output just copy & paste to forum. If very long use code tags or # in forum advanced editor.[/COLOR]

To see all the ext4 partitions, report showed sda3 & sda4.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary,  [COLOR=#b22222]change example shown[/COLOR] with partition sdb1 to your partitions

Disks or Disk utility is another application in live installer. (the flash drive you are using in live mode).
Older version screen shots attached, still essentially the same.

Sorry I post image because I use desktop to post while the troubled machine is my laptop

The live installer xubuntu has no disk utility so I try gparted instead. This one I got from gparted and "sudo gparted -l". 

[ATTACH=CONFIG]275392[/ATTACH]

---

### Post by ubfan1 on 2017-06-01
You have a GPT partitioned disk, an EFI partition but no bootloaders, so UEFI cannot boot.  You have grub in the MBR, but no small (1-2M) grub-bios flagged partition, so legacy cannot boot.  Decide in which mode you want to boot, and fix that problem. (install grub-efi or make another partition (easy with a GPT disk), and install grub-pc

---

### Post by oldfred on 2017-06-01
You need to be using live installer, or Ubuntu install flash drive in live mode on system that will not boot.
Then you can copy & paste from terminal using Firefox in live installer.
And you need live installer to run the repairs & Boot-Repair.

If Xubuntu live installer does not have an Ubuntu application, you still can easily install it from terminal.
But if different base gui may install a lot of dependencies. And it is not really installed, but just for the one session. On reboot it is lost.
sudo apt install gnome-disk-utility

---

### Post by YLTO on 2017-06-04
> **ubfan1 said:**
> You have a GPT partitioned disk, an EFI partition but no bootloaders, so UEFI cannot boot. 


On the installer I believe I have set the bootloader to install on dev/sda . It's weird, it didnt install the bootloader on efi, dont you think so?

> **ubfan1 said:**
> 
You have grub in the MBR, but no small (1-2M) grub-bios flagged partition, so legacy cannot boot. grub-pc

How do you know?

> **ubfan1 said:**
> 
Decide in which mode you want to boot, and fix that problem. (install grub-efi or make another partition (easy with a GPT disk), and install 

I have tried boot in UEFI mode, UEFI mode + legacy support but with no success. 

> **ubfan1 said:**
> 
 (install grub-efi or make another partition (easy with a GPT disk), and install 

How do I do it?

---

### Post by oldfred on 2017-06-04
How you boot install media UEFI or BIOS is then how it installs. If it wants the bios_grub to correctly install grub, that is the BIOS version.
If should give errors about a missing ESP - efi system partition (if missing) and installing in UEFI mode.

Your UEFI should give two boot options for Ubuntu flash drive, one UEFI:flash and other flash which is the BIOS. Where flash is name or label on flash drive.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ubfan1 on 2017-06-05
Mabe your Lenovo offers a boot choice like "UEFI before legacy" or "legacy before UEFI", and you need to select the UEFI first choice to boot the install media in UEFI mode, since it can boot in either mode.  A successful UEFI install should leave the Ubuntu bootloaders in the EFI partition's /EFI/ubuntu directory.  That partition gets mounted at /boot/efi in a normal UEFI install, so if you install and see /boot/efi/EFI/ubuntu/grubx64.efi ... etc. the UEFI install worked.  "How do I know"... Your boot repair report shows the MBR with grub and the disk partitions show a GPT partitioned disk with no grub-bios partition.  Odd that there's no complaint, since the grub-bios partition is where the core.img gets copied and normally picked up in getting grub running.  Maybe boot-repair found the source of it in /boot/grub/i386-pc, since the sector it reports is somewhere on the root partition.  I'm running an old Lenovo with two disks, one set up for  MBR/legacyboot and one for GPT/UEFI boot, and after selecting the disk to boot, it boot in the appropriate mode without having to change any machine settings.

---


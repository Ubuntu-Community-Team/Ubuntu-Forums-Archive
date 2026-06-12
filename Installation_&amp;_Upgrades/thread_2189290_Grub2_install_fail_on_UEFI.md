---
title: "Grub2 install fail on UEFI"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by blortuga on 2013-11-21
(No Windows Involved.  I am not Dual-booting.  Laptop originally shipped with Windows 7 installed in MBR mode).
I can successfully install 12.10 on MBR.

Hardware is a Dell Inspiron 7520, with Bios revision A09.
Bios menu software is Insydh20.
(Edit: I have Secure Boot DISABLED).

The "Boot" menu has a couple of options, one for <UEFI> or <Legacy> boot, and with <UEFI> selected, there is a "Legacy Option ROM" that can be enabled or disabled.

In UEFI mode, if there is a bootable DVD in the DVD drive, the system seems to hunt forever (well-over 30 seconds, often, never does make it to the boot-menu, when pressing F12), and will not boot.  If I select the "Legacy" item from the boot menu (DVD drive), it begins to boot, but hangs on "Checking Media [Failed]".

I have more success with USB stick "Live CD".  In UEFI mode, with the Legacy Option ROM enabled, I am presented with a Boot Menu of:
LEGACY BOOT:
Hard Drive
USB Storage Device
CD/DVD/CD-RW Drive
Network
UEFI BOOT:
EFI USB1 PATH1 (KingstonDataTraveler SE9).

(I built this boot disk with Unetbootin, laying down the .iso for 12.10 64 bit).

This lets me boot from either the USB Storage Device, or the EFI USB1 PATH1 device.  

If I boot to the EFI USB1 PATH1 device, and perform an install, it formats the drive as a gpt partition, and fails about 3/4 the way through, attempting to install grub to /target/.

If I boot via the Legacy USB Storage Device item, I can perform an install, and it formats the drive as an MBR partition, and finishes and succeeds.

I have read, here: ( [http://community.linuxmint.com/tutorial/view/858](http://community.linuxmint.com/tutorial/view/858) ),  that this is because of how the USB "persistenz" works?  (I don't think  I understand this).  

That user suggested to try to install via DVD.  But I can't get the DVD to be recognized in UEFI mode.

I have tried Boot-Repair, but it did not fix the problem.

I believe that GPARTED should be able to convert the installation (partition) from MBR to GPT.  Is this true?  I can't seem to find the menu selection that allows that in GPARTED.

---

### Post by oldfred on 2013-11-21
I think if you use gparted to convert it will totally reformat drive. I do use gparted to create gpt partitions on a new drive.
        I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.
    
You should be able to use gdisk which is in repository but not in default install or live installer.

       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)

If never installing Windows on a drive, I would use gpt anyway. Ubuntu can boot UEFI if an efi partition is first partiiton or boot BIOS if you have a tiny unformatted 1 or 2 MB bios_grub partition anywhere on drive.
Windows only boots from gpt drives with UEFI.
If you partition in advance, then use manual install, just choose the existing partitions for / and /home or others. Swap if already created will be found automatically.

I only have BIOS, hoped to get new UEFI system (said this now for about 2 years) and now format all new drives with gpt including both efi & bios_grub partitions. Then I can easily move drive to a UEFI system and install a UEFI bootable system if desired.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by blortuga on 2013-11-21
I think I solved this myself, after reading THIS thread: ([http://forums.linuxmint.com/viewtopic.php?f=46&t=143848](http://forums.linuxmint.com/viewtopic.php?f=46&t=143848))

I used dd if=imagefile.iso of=/dev/sdd <-sdd being my USB stick.

Using an image of 13.04, x64.

Booted in UEFI mode.

Used GParted to wipe the old install.
(GParted complained that it looked like a GPT disk that had been misformatted; well, it was formatted by my prior 12.10 installer - SO THERE!)
I used GParted to create the NEW partition, and using the "advanced" selection, specified "gpt" as the type. (otherwise, it would ALWAYS revert back to "msdos". - GParted should not used "advanced" to specify this UI control, but rather, should list it as "partition type" in a dialog when "New Partition..." is selected. Just my opinion.)

Installer completed, and was able to copy Grub.

So, I changed TWO variables in this experiment.

I switched from Unetbootin to dd *(ran dd in a cygwin terminal on my separate Windows 7 box).
I switched from 12.10 to 13.04.

So, either something in Unetbootin "breaks" the installer in a way that causes Grub installation to fail.
OR.
There is a problem with the 12.10 installer, which is fixed in 13.04.

So: my problem was "solved" - but I don't really think that this problem is solved.
If I were to speculate as to which issue was the real root-cause, I'm going to put my money on Unetbootin.

I am also going to BET that the reason why my burned Live CD's are not booting, is because they also are not properly copied to the DVD, (by Roxio), and the UEFI loader on my laptop can't find the EFI System Partition.

I suppose; as an experiment, I should try burning a DVD via dd, instead of Roxio.

But if this is true, I think that UEFI booting is probably sensitive (on some hardware) based on how the boot drive was created. I'm pretty sure my Roxio software is pre-UEFI.

(edit): The upshot of this is: I'm sure that developers at Canonical (or whoever is making installers for various Linux distros: I encountered the same problem with Mint, Debian, and Fedora) - probably build their live disks with dd. 

Most n00bz out there (like me) are probably going to be burning their ISO's with whatever old DVD mastering software they happen to have installed.   

Maybe not all hardware is going to puke all over itself like my laptop did.  Or maybe a lot of "n00bz" haven't tried on UEFI hardware yet.  I don't know.

One clear benefit of my new UEFI install vs. my old Legacy (BIOS) install, is that it definitely boots way faster.  (not just the bios-loading phase, but also the OS-loading phase).

---

### Post by oldfred on 2013-11-21
Cross posted just before yours.

Probably that you used the newer Ubuntu version. Each new version has major UEFI updates. Even more promised in 14.04 and 12.04.4.
Vendors also updating UEFI/BIOS as they also needed changes in many cases.

---


---
title: "Blinking cursor after new partition and install"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2017-01-05
Hi
Following these instructions exactly
1
[https://ubuntu-mate.community/t/gpar...dows-users/797]("https://ubuntu-mate.community/t/gparted-partition-guide-for-linux-and-windows-users/797")

2
[https://ubuntu-mate.community/t/inst...lse-method/651]("https://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651")

to partition  a 1TB SSD and install ubuntu-mate off a live USB.

My partition is different than the instructions and is as follows(also
see attached)

1 esp 550MiB
2 root 40 GB
3 home 640 GB
4 swap 128GB

At the blinking cursor I can either alt-F4 to bo to UEFI or esc and I
continue to boot to my 2nd SSD with a Windows 10 install.

If I try holding the shift key on reboot I instead see capital GRUB with
a blinking cursor on a black screen.

Hitting return takes me to my 2nd SSD with a Win 10 install.

The only change I have made to my UEFI is to disable FastBoot.

Next I tried Boot Repair from a live USB, and attempted to reinstall my  grub, but for some reason it did not 'see' my ESP at sda1, only sda and  sda2 which is my root partition.

So, probably a mistake, I let it go ahead and install grub in sda2.

After rebooting, same result, blinking cursor.

Next I relaunched gparted from a live USB and reexamined my partitions.

Now I was seeing an error icon on my ESP at sda1, saying it wasn't  recognized because I was missing certain files (see attached  esp_warning)

I am also getting a warning whenever launching gParted about a  discrepancy between Linux and the driver descriptor in regards to  physical block size. (attached LibParted_warning)

I realize this is a long post but trying to include as much information as possible.

Thanks for any feedback!


Question> For my GPT partitioned drive, does it matter what partition
flag I have set for my ESP ?
It was set to 'boot', then I tried 'uef-grub' but neither worked.


Results of boot-repair here
[http://paste.ubuntu.com/23750353/](http://paste.ubuntu.com/23750353/)

---

### Post by Bucky Ball on 2017-01-06
Bit off topic, but why on earth have you got a 128Gb /swap??? You don't need anything like that. Some people don't even bother with one if they have a decent amount of RAM. 2Gb /swap is fine or the same size as installed physical RAM if you are intending to hibernate ...

Your issue may be related to the fact that it appears you have Ubuntu installed in BIOS mode and Windows is probably in UEFI. Also, you say Windows is on your second SSD. There is no second SSD shown in your Boot Repair output. Looks like you have Ubuntu in BIOS mode on sda and sdb is probably a live USB or disk.

As for your ESP partition, that is a Win thing. I suggest you have a [good read of this]("https://msdn.microsoft.com/en-us/library/windows/hardware/dn640535(v=vs.85).aspx#gpt_faq_esp_partition"). Looks like you have the ESP partition on a BIOS mode install and are trying to boot a UEFI Win install with it. Apparently that won't work, but I'm no expert. Putting two and two together to make five from what I'm reading.

Lastly, from the bottom of your Boot Repair output:

> Please do not forget to make your BIOS boot on sda (1000GB) disk! 

You have sda set as first boot device in BIOS I presume?

Good luck and hope that gives some clues. ;)

---

### Post by ubuntini2 on 2017-01-06
Thanks for the reply and info!

The Boot repair results Do seem to indicate a lot of things wrong.
I assume that  reinstalling grub with Boot repair  AFTER setting my ESP flag to bios-grub may be part of the reason

Probably need to repartition once more  but before I need to know what I did wrong in my first attempt. Yes I definitely DID remember to set my UEFI bootloader to my ESP, but perhaps it didn't 'take' for some reason

Also, does the LibParted warning suggest something wrong with my partitioning?
As to swap size
1- storage is relatively cheap.
2- I use my Linux PC primarily for particle simulations in Houdini and got some feedback from Linux-Houdini experts a lot more knowledgeable than I
3- If after several months of use I discover I rarely use that amount, I assume I can easily increase my home partition and reduce swap.

---

### Post by oldfred on 2017-01-06
Best to not mix UEFI & BIOS.
And then is hardware is UEFI and Windows is UEFI only use gpt partitioning.

With gpt partitioning gparted/parted use boot flag only as indicator to add a very long GUID to the ESP - efi system partition which is really how UEFI knows to find the ESP & boot files. Boot flag with UEFI/gpt is totally different than boot flag in BIOS which is for Windows to find more Windows boot code.
With gdisk you assign the GUID by using ef00 as code/flag/indicator.

So boot flag is for UEFI boot on gpt partitioned drives. The ESP is a standard FAT32 formatted partition and boot flag converts it to ESP.
But if booting in BIOS mode from gpt partitioned drive you need a 1 or 2MB unformatted partition with the bios_grub flag. Otherwise grub will not install correctly to that drive.
And grub in UEFI mode, only installs to the ESP on drive seen as sda during install. Some have had a BIOS/MBR second drive, but installed in UEFI mode and if sda has ESP on gpt drive Ubuntu/grub will boot in UEFI mode thru gpt's ESP on sda to MBR drive. Not recommended. 

Best to have all drives as gpt if UEFI.
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
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
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

Edit:
Are you running Boot-Repair from its own live ISO? That is now older. Script did not show NVMe drive.
Better to just add Boot-Repair to your Ubuntu live installer.

---

### Post by ubuntini2 on 2017-01-06
Thanks for the great info and the tip about boot-repair!  Had to read the 3rd paragraph 3 or 4 times:) I still have some questions about UEFI firmware settings, whether I should leave Fast Boot enabled, Secure Boot and what setting to use for CSM(whether I should use UEFI only, or auto, or...)

Also, one last point of confusion, why would you try and accommodate booting in BIOS mode on a GPT formatted drive?

ie (gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI))

Is this only to provide compatibility with older OS's or is there some other advantage?

---

### Post by oldfred on 2017-01-07
The bios_grub partition allows use of the newer gpt(GUID) partitioning on older systems or if for some reason you want to boot in BIOS mode. I normally keep the full installs on flash drives separate or one for BIOS and one for UEFI, but there are ways to install grub twice, once for UEFI and once for BIOS boot. Both ESP at 300 to 500MB (I only use 100MB on flash drive full install) and 1 or 2MB do not use much space on new large drives or even most SSDs. So I just automatically add both to all drives.

I converted to gpt back in 2010 with my BIOS systems. Then started adding both bios_grub & ESP so I could later move drive to a newer UEFI system.
Only Windows requires MBR for BIOS and gpt for UEFI. Ubuntu can boot from gpt with either UEFI or BIOS.

I think gpt really only has minor advantages, but find once I started using it, it has just worked. I like that it has a backup partition table.
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

I turn off secure boot. May want to turn it on later, but for now I see little advantage.
I turn off fast boot, when configuring system. My system boots thru UEFI so fast that I have no time to press a key to get into UEFI. But my motherboard has a delay setting, so once mostly configured, I was able to change to 3 sec delay, just to have a chance to press a key to get into UEFI. And I have separate settings for cold (full power off/on) and warm (reboot), so set cold boot to full UEFI reset or check for changed hardware or settings.

I also found that update of BIOS or UEFI resets most settings to vendor default. So I document those. But one new UEFI lists changes before asking me to save new settings. And my UEFI has screenshots, were old BIOS I had to use camera.

My Asus UEFI required me to have USB flash drive set to UEFI only to boot in UEFI mode. Even UEFI or CSM, only booted in CSM/BIOS mode. 
I think some Dells work better with CSM on even for UEFI boot. 
But most systems only boot in BIOS/CSM/Legacy mode when CSM mode is on.
UEFI Secure boot will not allow BIOS boot. And will require turning on allow USB boot as that is not considered secure, but you may need that turned on anyway.

Many users do not realize difference between UEFI & BIOS. And then may boot install in one boot mode which is how it installs, but have system boot set to a different boot mode. But if Windows is installed, you should install Ubuntu in same boot mode as drive will be MBR for BIOS/CSM or gpt for UEFI.

There are 3 boot modes, UEFI with Secure boot, standard UEFI, and BIOS/CSM/Legacy.  I suggest just making sure both system boot & boot of flash drive is standard UEFI. And then later could upgrade to Secure boot, if desired. 

But if installed in BIOS mode (and do not have gpt with ESP) then drive has to be repartitioned/reformated & reinstalled to convert to UEFI.

---


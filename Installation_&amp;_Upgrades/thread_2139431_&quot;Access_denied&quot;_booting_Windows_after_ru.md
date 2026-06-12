---
title: "&quot;Access denied&quot; booting Windows after running Boot Repair"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by mikesmithv on 2013-04-26
I have a new laptop (Dell 17R SE) with Windows 8 pre-installed.  I sized down the NTFS partion down to make room for an ext4 partition for data and used the 32 GB SSD second drive to install Ubuntu 13.04 beta 2.  This was a while back and everything has been working fine except Windows 8 required "secure boot" mode and Ubuntu "legacy boot" mode, so dual booting was a hassle.  I ran Boot Repair hoping to fix this by booting in "legacy mode" off a USB drive.  I could not figure out how to boot Ubuntu 13.04 in "secure boot" mode either off the CD or a USB startup drive, so maybe that's the root of the problem but the result of letting Boot Repair run with default options (booted in legacy mode) is that "secure boot" mode no longer boots into Windows 8.  It just comes up with a dialog that says "Image failed to verify with *access denied*  Press any key to continue".

The URL Boot Repair reported was:
[http://paste.ubuntu.com/5605293/](http://paste.ubuntu.com/5605293/)

I'm thinking of running Boot Repair a second time but this time selecting the option "Restore EFI backups" in "Advanced Options" to see if Windows 8 will boot again.  I'm afraid of just digging my hole deeper so I'm holding off on that.

If the problem can be solved by running in "secure boot" mode, here is what I ran into trying to do that.  In secure mode the Ubuntu 13.04 CD does not show up as a boot choices on the Dell when I press F12.  I have to enter Setup and choose the Boot tab, then select "Add Boot Option".  Then a panel comes up that shows a "File system list" with the entry:

PciRoot(0x0)Pci(0x1F,0x2)/Sata(0x3,0x0,0x0)/CD

I assume this is how the Dell detects a UEFI bootable CD and I have to manually add it to have it appear in the boot options list, and this indeed turned out to be the case.  I gave the new boot option a name but had no idea what to enter for the "file path" field so I left it blank.  But when I restart  in "secure boot" mode and select that new boot option it give me the "Access denied" dialog.

I really have no idea how to proceed from here.  Any ideas are welcome.

---

### Post by oldfred on 2013-04-27
To get a UEFI install you have to install to a gpt partitioned drive. Your 32GB SSD is MBR(msdos). 
Some systems only boot in BIOS mode from DVDs, and may boot from a flash drive in UEFI mode?
How you boot installer is how it installs.
Boot repair can convert a BIOS install to UEFI, but it has to be on a gpt drive. Some computer will only let you install in BIOS mode.

I do not have UEFI, but was hoping to build a new UEFI system an might move SSD to that system. So I created both efi partition for future use, and bios_grub for current BIOS booting.

```
fred@fred-Precise:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```

An install of Ubuntu may use efi partition on sda, but I suggest you create an efi partition on every gpt drive, so you can have boot loaders on that drive when other drive fails. I have my SSD configured to fully boot without my hard drive where most of my data is. I keep just /home inside my /, but create data partitions on rotating drive for all data including some that is normally in hidden folders in /home. 

I partition in advance with gparted and right click to set flags. Then I use Something Else or manual install to choose and format partitions.

       Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by mikesmithv on 2013-04-27
> **oldfred said:**
> To get a UEFI install you have to install to a gpt partitioned drive. Your 32GB SSD is MBR(msdos). 
My SSD drive is formatted as Ext4, but looking at the system profile I posted I see why you thought it was msdos.  The USB drive which I used to boot Ubuntu with Boot Repair was included in the list, and that drive is msdos.  The USB drive is sdc1 and the SSD is sdb1.

One thing I didn't mention in the original post is that to boot Ubuntu I now have to select the Windows Boot Manager option in the list of UEFI boot choices.  Even though I am in the "legacy mode" it shows UEFI boot options.  So it appears that it did convert to UEFI boot but Windows 8 requires "secure boot" mode so none of the Windows choices in the Grub menu work.  And if I switch to "secure boot" mode I get the access denied message, but that may be due to running Boot Repair in legacy rather than secure boot.  I have since seen this post in the Dell forum that addresses how to do that:

[http://en.community.dell.com/techcenter/os-applications/f/4613/p/19501016/20340857.aspx#20340857](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19501016/20340857.aspx#20340857)

Apparently on a Dell you hold the shift key down while booting Windows 8 to get the menu choice to boot from a Ubuntu USB startup disk.  When I figure out how fix my windows boot I will try that next.

---

### Post by mikesmithv on 2013-04-29
I solved the initial problem and I can boot into Windows again.  Boot Repair backed out of the screwed up boot configuration very nicely by running it again and selecting "Restore EFI backups" and unchecking "Reinstall Grub".  It put the configuration back exactly like it was.

As for the larger question as to how reduce the steps for dual booting on a Dell 17R SE it appears that's just not possible until Dell does something on their end.  Once I was comfortable with Boot Repair's ability to restore tried various other things and basically nothing works.  My final attempt was with just one disk with an efi partition (fat32, 200mb, bootable) and Ubuntu 13.04 installed and even that didn't work.  If I check "secure boot" in Boot Repair and let it run I got "access denied" after rebooting in secure boot mode.  If I started over with a blank efi partition and ran Boot Repair again without checking "secure boot" it almost worked.  I got the grub menu with the correct choices but selecting any choice just left me with a blank screen forever.  This was with rebooting in efi mode and secure boot NOT enabled.  From my experience and from reading other posts about this it is a Dell problem and not a Boot Repair issue.  Congratulations to the Boot Repair folks for building in robust restore options.  It made this kind of tinkering around possible.

Funny thing is that I love this Dell.  Ubuntu boots in seconds on the SSD and the illuminated keyboard is very nice.  The messy dual boot situation minor really, someday it will be fixed with a firmware upgrade or I could just reinstall Windows 8 from the DVD they included and boot everything in "legacy mode".

---

### Post by oldfred on 2013-04-29
I think these have all worked.

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

Supposedly all of sputnik updates are now in 13.04 or if you install the 12.04.2 LTS you need to install sputnik.

With ULtaBooks you have the extra issues of Intel SRT and removing RAID from drive(s) and dual video which requires bumblebee.

---

### Post by mikesmithv on 2013-05-03
Thanks oldfred for those links.  I finally got the good old grub menu (no hitting F12) and everything works.  I can boot into Ubutnu or Windows with no muss, no fuss.  The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on.  It seems weird that the only way to install Ubuntu is launching it from Windows, but if you want to run Boot Repair under secure boot mode that's the only way to do it on this Dell.  The strange thing is that after doing all that and running Boot Repair it didn't work initially when I rebooted.   With EFI on and secure boot either on or off the Grub menu came up but clicking on either choices (unbuntu or windows) didn't work.  It only works if the boot mode is set to "legacy boot" (EFI off, secure boot off).  This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.  I have rebooted many times and everything continues to work so I will just let this sleeping monster lie.  All's well that ends well.

---

### Post by oldfred on 2013-05-03
Glad you got it working, not sure it makes sense. But this entire UEFI secure boot has lots of options and each vendor and maybe even each model seems to have differences.

You may just want to document you system by running just the BootInfo report from your Boot-Repair.

---

### Post by mikesmithv on 2013-05-04
> **oldfred said:**
> ...You may just want to document your system by running just the BootInfo report from your Boot-Repair.
This is the paste-in from Boot Repair that pretty much tells it all.

[http://paste.ubuntu.com/5630490/](http://paste.ubuntu.com/5630490/)

---


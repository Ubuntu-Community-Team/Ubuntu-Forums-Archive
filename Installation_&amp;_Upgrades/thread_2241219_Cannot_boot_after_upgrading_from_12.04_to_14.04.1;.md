---
title: "Cannot boot after upgrading from 12.04 to 14.04.1; Boot Repair doesn't help"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by redrabbit2 on 2014-08-25
After completing the distribution upgrade process from 12.94 to 14.04.1, the PC rebooted but I get

Error: file not found
grub rescue>

I tried running Boot Repair (64 bit), but it won't do any repair.  It pops up "Please close all your package managers (Software Center, Update Manager, Synaptic, ...).  Then try again."  Except I didn't start any other applications.

My BootInfo is [http://paste.ubuntu.com/8137431/](http://paste.ubuntu.com/8137431/).  Any idea how I can fix this?

---

### Post by kansasnoob on 2014-08-25
There's more than one problem but lets just focus on what may be an easy way to get you to boot.

Windows is on /dev/sda which is a 750 GB drive.

Ubuntu is on /dev/sdb which is a 1 TB drive.

But according to the Boot Info grub is installed to the mbr of both drives:

> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

There are two additional drives, /dev/sdc which is 2 TB and /dev/sdd which is 4 TB.

Since all 4 drives are different sizes it should be easy to tell them apart in BIOS so I'd access BIOS and look at the hard drive boot priority. I'd almost bet you'll find that the 1 TB drive is set as first priority, if so try setting the 750 GB drive to the top priority. This is usually done using the page up/down keys.

If changing the boot priority gets you booted then we should fix things so that doesn't happen again the next time you have a kernel update and also get rid of this old legacy grub menu.lst:

> sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

If changing the hard drive boot priority doesn't work it's easy to change it back again.

---

### Post by fantab on 2014-08-25
> grub2 purge cancelled
Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb (1000GB) disk!


Try what kansasnoob suggested and set your Bios to boot your second HDD or /dev/sdb first.

Also you seem to have old kernels since ubuntu 10.04. You must remove those as well, later.
I'd recommend that you consider re-installing ubuntu after Backing up your data.

---

### Post by kansasnoob on 2014-08-25
> **fantab said:**
> Try what kansasnoob suggested and set your Bios to boot your second HDD or /dev/sdb first.

Also you seem to have old kernels since ubuntu 10.04. You must remove those as well, later.
I'd recommend that you consider re-installing ubuntu after Backing up your data.

Before reinstalling Ubuntu anyone with a dual-boot needs to be acutely aware of this horrible bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by oldfred on 2014-08-25
With multiple drives do not run auto fix in Boot-Repair. That just installs grub to every MBR.
You really want to keep a Windows boot loader in sda, so you can directly boot from BIOS or one time boot key,  it if you have issues with sdb.
You can reinstall just a Windows boot loader with Boot-Repairs advanced options. Choose operating system and choose drive. Also reinstall grub just to sdb.

You probably are getting errors from Boot-Repair when it tries to install grub to sdc & sdd as they are gpt partitioned. For grub to install to gpt partitioned drive it need a tiny 1 or 2MB unformatted partition with the bios_grub flag if using gparted. That sets the correct very long GUID that grub needs to see to find the partition to install core.img into for booting. Normally with BIOS/MBR core.img is just in the unused sectors after the MBR, but that does not exist with gpt.

If you do reinstall you must use Something else, both for the bug Kansasnoob posted and to get the choice on which drive to install the grub2 boot loader into. Otherwise with auto install it just installs grub bootloader to sda and erases an entire drive with Windows 8. May not erase entire drive with older Windows but not worth the risk.

---

### Post by redrabbit2 on 2014-08-25
Thanks! Switching the boot priority to the first disk gives me a very old but  usable grub menu.  I can boot windows successfully, so this is  progress.  The only ubuntu options on that menu are for 12.04, almost certainly my initial install of that version.  I  suspect that the associated kernel is long gone, so I didn't try it. I  burned a LiveCD and can see all my partitions when I boot from it.
I'm looking into reinstalling grub on /dev/sdb, but want to proceed cautiously, esp. after hearing about the various bugs and gotchas that can wipe out complete partitions in a single return.  I see I have grub 1.99, but the newest version is 2.  Can I just use grub-install from the live cd, or do I need to do something special?

---

### Post by oldfred on 2014-08-25
Since it is 12.04, did you try a sudo update-grub. It may add the newer install to its menu so you can boot it.
Then from within your install you can easily install grub to sdb.

       sudo grub-install /dev/sdb
sudo update-grub

But grub does remember settings, you may need to make sure they are correct so when grub does a major update, it will reinstall to the correct drive.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

If you cannot boot your install, you can use Boot-Repair or manual install grub to MBR using Live installer or 12.04.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Once you get Ubuntu booting from sdb, reinstall the Windows boot loader to sda, so you can boot it directly.

Since you have a couple of large data drives, review this poster's logic.
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

### Post by fantab on 2014-08-26
> **kansasnoob said:**
> Before reinstalling Ubuntu anyone with a dual-boot needs to be acutely aware of this horrible bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I didn't know about this bug, Thanks.

However, when I said 'reinstalling' I meant a fresh and clean install (after formatting the partition, etc) and NOT 'reinstall' option given by the installer.
Personally, I don't trust ubiquity with partitions, especially its auto functions. I have had my share of bad experiences with it.

---


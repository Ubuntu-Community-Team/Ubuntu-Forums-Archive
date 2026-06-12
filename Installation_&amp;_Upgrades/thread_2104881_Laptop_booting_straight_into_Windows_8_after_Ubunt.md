---
title: "Laptop booting straight into Windows 8 after Ubuntu installation and boot-repair"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by oustiti on 2013-01-14
Hi,

I've managed to get Ubuntu installed alongside windows 8, however when I reboot the system it goes straight into Windows.

I ran boot-repair from a USB key and generated this : [http://paste.ubuntu.com/1531146/](http://paste.ubuntu.com/1531146/) , but the situation hasn't changed, it always boots straight into Windows 8.

Any suggestions greatly appreciated!

---

### Post by oldfred on 2013-01-14
It looks like your system is UEFI capable but you have Windows & Ubuntu in BIOS mode. Boot-Repair says it installed to the MBR, but it is not there? Windows boot loader is still in MBR.

It looks like you may have this error from line 474:
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Windows will install to gpt drives, but only converts primary gpt partition table. gpt has a backup and usually Linux does not install. Maybe now it installs, but grub does not? Run fixparts to remove backup gpt table. Then rerun Boot-Repair.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by rreyes3713 on 2013-01-14
I experience a similar problem. So what I did was going into the bios, and set the booting order to UEFI Ubuntu ( I think ) and save settings. 

I would get the Grub and everything checks out fine.

But I did experience going selecting Windows 8 from the Grub, and I think somehow it corrects itself in the Bios and reset to opening "Window 8" first. It happened twice to me. As of now (after saving the bios setting), I'm getting the Grub so far.

Try that, changing the booting order in the bios, select "UEFI Ubuntu" first.

---

### Post by oldfred on 2013-01-14
@rreyes3713
If you look at OP's boot info script you can see he has MBR not gpt partitions and not efi boot partition. So he has to be in BIOS mode. If he was in UEFI mode then your suggestion is exactly what he should do, but he is not.

Since drive is MBR(msdos) partitions and you have a boot loader in the MBR, you need to continue to boot in BIOS/Legacy or whatever your system calls it, but not UEFI mode.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ben222qmz7 on 2013-01-14
I too have a problem getting into Ubuntu. I have winxp and when trying to boot the system goes to Windows.

Could sombody see the report because I do not understand a thing of it:[http://paste2.org/p/2748701](http://paste2.org/p/2748701)

(I do not understand why it shows the date [Boot-Info November 20th 2012]???)

---

### Post by oldfred on 2013-01-14
@ben222qmz7
That is the date Boot-Repair was last updated or released. It is newer as before it was last spring. 

Have you rebooted after Boot-Repair? It looks like you have grub in MBR and should only boot to grub menu. then choose Ubuntu or Windows.

---

### Post by YannBuntu on 2013-01-15
**@oustiti:** please disable UEFI in your BIOS , then retry the Recommended Repair and tell us the new URL that will appear. Reboot. If still not good, use Gparted to format your entire disk with GPT partitioning, then reinstall Ubuntu.

**@ben222qmz7:** please use your own thread, which is [http://ubuntuforums.org/showthread.php?t=2104801](http://ubuntuforums.org/showthread.php?t=2104801)

---

### Post by oustiti on 2013-01-15
@YannBuntu - is there no way of getting Grub to work as it currently or using fixparts?
The BIOS on this laptop is locked so I can't go in to change it. I believe it's currently set to CMS + UEFI...

Thanks

Edit : Should have mentioned if I format the drive as GPT then Ubuntu (Secure remix) still doesn't boot as UEFI and cannot see the Windows partition...

---

### Post by oldfred on 2013-01-15
How you boot install media for both Ubuntu & Windows is how it installs, or if you boot the installer in UEFI mode it installs in UEFI mode. You choose how to boot from the UEFI menu which will give both choices. 

And both Windows & Ubuntu have to be installed in the same mode or both in UEFI or both in BIOS.

---


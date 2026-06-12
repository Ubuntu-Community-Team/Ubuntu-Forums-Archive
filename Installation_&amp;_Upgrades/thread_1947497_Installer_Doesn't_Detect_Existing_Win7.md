---
title: "Installer Doesn't Detect Existing Win7"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by steve_c on 2012-03-26
I'm attempting to dual-boot Windows 7 (64-bit) and Ubuntu. Currently using Ubuntu 11.10 desktop, 64-bit.

I installed Windows 7 first and set it to use 500GB of my 1TB drive, theoretically leaving the other half for Ubuntu.

However, when I boot the live CD and attempt to install Ubuntu, the installer does *not* see the Windows partition and only gives me the option to install across the entire disk.

This is a relatively new computer with an EFI motherboard, so I don't know how much that contributes to the problem.

Disk Utility detects the NTFS partition and says the disk has MBR formatting. Gparted, however, doesn't detect it and says that the partition table is GPT. As mentioned before the Ubiquity installer does not seem to see the NTFS/Windows partition.

I've been beating my head against this for a while. Thank you for any help!

---

### Post by oldfred on 2012-03-26
If drive was gpt and Windows installs to MBR it converts the gpt back to MBR. But gpt keeps a backup partition table (one of its advantages) that Windows does not see nor delete. Then in Ubuntu & most Linux tools they get confused on whether it is MBR or gpt.

Window will only work in gpt if you are booting in UEFI mode and the first gpt partition is the efi partition. 

If MBR, Windows 7 normally installs a hidden 100MB boot/repair partition and then a second main (c: ) partition.

delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by darkod on 2012-03-26
If the disk came with gpt table, and you created new msdos table with windows, it seems it replaces the main table but not the backup. gpt has also a backup partition table.

So later systems like ubuntu are confused is the msdos or gpt table the real one.

If you did use msdos table, you can try fixparts which will let you know you have unused backup gpt table and ask if you want to delete it. That is the cleanest way I know.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If on the other hand you are using gpt, you need to find out why there is a msdos/gpt confusion.

---

### Post by steve_c on 2012-04-01
So according to the Win7 Disk Management utility, the disk does have a 100MB System Reserved partition, and it says the partition style is MBR. I also notice if I right-click on the disk there I see the option to "Convert to GPT disk" is grayed out, but there is a select-able option to "Convert to dynamic disk."

From what I've read, the advantages to GPT are partition size >2TB (not applicable to me), greater number of partitions (not applicable to me), and greater protection from partition table corruption (applicable to me). Being one of those latest-techology-loving-type nerds, I'd probably prefer to use GPT if possible but I'm not sure at this point if that's actually an option, nor how I'd get there from here.

Is it possible for me to do that, or is using the Latest Thing a waste of my time here and I should just use fixparts to get my dual-boot running as smoothly as possible?

Thanks again for the replies!

---

### Post by darkod on 2012-04-02
Depending how you define your waste of time. :)

You would have to reinstall win7. At least I haven't heard of a way to switch to gpt without losing the data on the disk.

Also, it will make things easier if you use BIOS boot and not EFI boot, even though you have efi board. The combination win7 + ubuntu + efi + gpt still has lots of hiccups it seems.

I have no idea how you would tell windows to create the disk as gpt. Very easy way is with the ubuntu cd in live mode, in terminal just do:
sudo parted /dev/sda

Once in the parted prompt:
mklabel gpt

That creates new blank gpt table, deleting all data of course!!!!

Now, if using gpt it is important to create one small 1MB partition for grub2 that has NO filesystem. It's important not to create any filesystem on it, just leave it. So, on the parted prompt it would be like:
unit MiB (change unit to mebibyte)
mkpart primary 1 2

That will create the partition with start/end 1MB/2MB on the disk. You can list the partitions with:
print

If the partition was created correctly, you need to set the bios_grub flag on it. Something like:
set 1 bios_grub on

That will set the bios_grub flag to ON on partition #1.

From there on you can continue with parted creating the ntfs partition for win7 too, or start the installation with the win7 dvd. If you create a ntfs partition in advance, you save one primary partition because in that case win7 doesn't create the small 100MB system reserved partition.

So, you could create ntfs partition like:
mkpart primary ntfs 2 512002

That should create it from 2MiB to 512002MiB in other words exactly 500GiB (note, not 500GB where one GB is 1,000,000,000 Bytes).

That should be it, simply quit parted with:
quit

From there continue installing win7 on the created partition and then ubuntu.

---

### Post by oldfred on 2012-04-02
It is my understanding that Windows will only boot from gpt if UEFI not BIOS. Ubuntu will boot from gpt with BIOS (I am using gpt on two drives and a flash drive just to see how it works with BIOS only systems).

Most new desktop systems with Intel i3, i5 or i7 cpus have motherboard with UEFI, not sure about portables.

And Darko is correct, many users are having issues with UEFI and Ubuntu. There were (are) some bugs in the installer or grub2. It actually seems Windows installs to UEFI easier than Ubuntu.

Once I learned to create a bios_grub partition of 1MB, using gpt with BIOS has not been an issue on drives without any Windows.

The Arch site has some good info:

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by steve_c on 2012-04-09
Thank you all!

Fixparts did help remove the GPT data, and I was able to install Ubuntu on the unpartitioned half of my drive.

I'm still having issues because now when the machine boots it still isn't seeing grub, for some reason, and still just boots straight into Windows. But that's a different issue. I'll try and work on that a bit before coming back to the forums for help.

Thanks again!

---

### Post by darkod on 2012-04-09
Maybe just the part of grub2 that goes to the MBR was not installed. Or it is installed on another disk (if you have more than one), so just try booting from the other disk.

In case you need to reinstall grub2 to the MBR, the procedure is here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---


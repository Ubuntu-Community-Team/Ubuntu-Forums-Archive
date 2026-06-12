---
title: "Installing 12.04 on SSD to have dual boot : not seeing windows!"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2012-05-15
I have an SSD as the main HD. I already installed Windows 7 on it. I had already created the partitions where I reserved an unallocated 15Gb for Ubuntu. Windows works without problem. I took an ISO of the whold SSD as backup.  It is brend new PC with new Windows 7 64 bit CD.

Now when I try to install Ubuntu 12.04, it does not see any partitions at all on my /dev/sda. It only sees an unallocated space. I did several internet search but I got fed up looking for an answer and I am tired.

I tried installing Ubuntu first but when I try to install windows 7 after, it says it sees the disk as being a GPT partition. So I went back to restore my /dev/sda with Windows on it and trying to install Ubuntu 12.04


sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa53626ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    83888127    41840640    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001e20e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   134219775    67108864    7  HPFS/NTFS/exFAT
/dev/sdb2       134219776   301991935    83886080    7  HPFS/NTFS/exFAT
/dev/sdb3       302005996  1953520064   825757034+   5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sdb5       302005998   318761729     8377866   82  Linux swap / Solaris
Partition 5 does not start on physical sector boundary.
/dev/sdb6       318761793   335533589     8385898+   7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sdb7       335533653  1409269994   536868171    7  HPFS/NTFS/exFAT
Partition 7 does not start on physical sector boundary.
/dev/sdb8      1409270058  1953520064   272125003+  83  Linux
Partition 8 does not start on physical sector boundary.

---

### Post by lilmagnus on 2012-05-15
I think the easiest thing may be for you to start over, reinstalling Windows onto an MBR-partitioned disk. This would require a reinitialization of the disk as MBR. You say it's an SSD. GPT-partitioned disks are designed to be over the 2TB size limitation inherent in MBR-partitioned disks. I don't believe your SSD size would be over 2TB.

---

### Post by oldfred on 2012-05-16
Windows will only boot from a gpt disk if UEFI. And wiht BIOS you need MBR partitioning.

Ubuntu works with gpt or MBR and either BIOS & UEFI. I boot gpt partitioned drives with BIOS, but have to have a bios_grub partition to get grub to install correctly.

With only 60GB and Windows I might just install Ubuntu on the rotating drive. It will not be as fast but will not crimp your Windows as it will want lots of space. Or if using Ubuntu a lot then put Windows on the rotating drive.

Since Ubuntu does not need much room, I did put two 27GB / (root) partitions on my 60GB SSD so I can have the current install and test the next install. I still have my old install on the rotating drive and another old drive with XP. So every drive has at least one system.

---

### Post by Browser_ice on 2012-05-16
My SSD is 60Gb.
The partition I had reserved for Ubuntu is 15Gb at the end of the SSD.
The rest is to be used for Windows 7.

I do not know where the GPT came from. I can only assume it is because I have an SSD as O/S disk. I had followed the Windows 7 install and based on what was used and done, there were no choices of doing a different partition setup (I mean nothing other then create my Ubuntu reserved partition and selecting the rest to be used by Windows 7).

I already configured my WIndows for the following :
- have the My Document folders on the 2nd HD
- have all temp folders on the 2nd HD
- have the windows swap file (forgot its name) on the 2nd HD
- deleted the Hibernation file and disabled it
- disabled indexing of files on the SSD
- defrag is someone automatically disabled for my SSD

All I have left to do is to successfully install Ubuntu as a dual boot on my SSD.

What do you mean by "Windows will only boot from a gpt disk if UEFI." ?  What is UEFI ?

Having an SSD O/S HD, I am stuck with GPT partitions or can I replace them with MBR ones ?

Can someone give me the solution and the steps to this dual boot installation ?

---

### Post by darkod on 2012-05-16
Actually, this looks like gpt leftovers, not gpt disk.

If the SSD was using gpt earlier, and you repartition with windows tools, often they convert the main table from gpt to mbr but do not delete the backup table that gpt disks have.

Linux detects this backup table and is confused not knowing if the disk is mbr or gpt.

The easiest tool for getting rid of the unused backup table is fixparts. Boot into live mode from the ubuntu cd, download fixparts, and open the disk with it. It will report the gpt/mbr difference and ask you if you want to delete the backup table.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by oldfred on 2012-05-16
Darko is correct, I should have noticed you do not have the efi partition that you would have to have if UEFI and gpt. So the gpt is just the left over backup (one of the advantages of gpt is that it has a backup).

---

### Post by Browser_ice on 2012-05-16
Ok I will check your recommendations.  But the thing I do not understand is that my SSD is brand new. My first time using it was installing Windows 7 on it 5 days ago. It is a brand new system I built. So why all of a sudden would it decide to have a left over GPT after I installed Windows 7 on it for the very first time ?

My SSd was blank. I created a blank 15Gb partition at the end and when everytimes I install Windows 7, it always create a 100Mb partition at first and if I had installed Ubuntu on that 15Gb, Windows 7 would add an additional small partition before the actual Windows partition. I never had this with the previous Windows versions. So I am assuming this is how Microsoft is now doing things with Windows 7 partitions.

Or could it be because before I installed Windows 7, I used a Ubuntu (or Xubuntu, I do not recall) Live CD 10.04 to create that last 15Gb partition I wanted to use for Ubuntu ? 

I just want to understand where did this GPT came from if everything was brand new.

---

### Post by oldfred on 2012-05-16
Ubuntu only converts very large and empty drives  of over 1TB to gpt and even those do not have to be converted. Only over 2TB needs to be gpt.

Some sites recommend gpt for SSD as it is the newer partitioning. 

If you booted Windows in UEFI mode it would create gpt partitioning.

---

### Post by darkod on 2012-05-17
Since you asked about UEFI (you can google it too), it's a newer type of boot process. It would be good to look around in your bios and make sure you don't have uefi enabled. In some boards that support uefi, there is an option to disable it. In that case it would use the standard bios boot.

If it's set up for uefi, the windows install might have tried to make the disk gpt because windows can only work on gpt with uefi boot.

Another thing I noticed, you keep talking about that 15GB partition you created for ubuntu, and I don't see it. On the SSD you have sda1 (the 100MB win7 boot partition) and sda2 (the win7 system partition). There is unallocated space of about 15GB but not a partition in it.

This might have something to do with not seeing win7 too. Not only that it's not seeing win7, that 15GB partition is missing too.

One tool that is letting you know about msdos/gpt tables is also parted:
sudo parted /dev/sda print

Towards the top it will print the disk size, model etc, and also the partition table type. If it asks you whether you are using msdos or gpt you better say msdos I guess. Not sure if parted can also delete the gpt leftover table like fixparts can, that's why I suggested fixparts first.

---

### Post by Browser_ice on 2012-05-17
WHen I said I had created a 15Gb partition for my Ubuntu, I said it the wrong way. I meant when I created it with Gparted but did not format it. I wanted to be sure I had a partition space reserved for Ubuntu which meant I did not have to bother downsizing my Windows-7 partition while inside Windows 7.  That was the first thing I did with my new SSD. Then I proceeded with installing Windows.

After that, GParted simply did not see any partitions at all on my /dev/sda. It only saw a 60Gb of unallocated space.


I will check with the BIOS setting as I never mentioned anywhere that I wanted UEFI. It could have been a default Bios value.

But in any case, I did use that fixparts tool to delete that GPT and then I was able to install Ubuntu 12.04 as dual boot. It now works. I had to get the windows version of fixparts as the Debian version could not work because of some package dependencies.

---

### Post by darkod on 2012-05-17
Glad it worked.

On a side note, you never had to use Gparted just to allocate space without actually creating a partition. During the win7 installer when you are creating the win7 partition, you have the option to select the size. By default it's usually the whole disk, but you can adjust it to be 15GB smaller and it will leave 15GB unallocated after the partition.

---


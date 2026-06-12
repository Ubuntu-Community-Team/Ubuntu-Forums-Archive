---
title: "Ran into a snag installing 12.04 in efi mode (incl error message)"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2013-03-19
Hi,

I tried this before (about 6 mos ago). After a few failed attempts I just gave up and installed as a bios install. Now I've learned a little more and want to really make this happen (whatever it takes). I know the arguments against efi, and that's all well and good, but and efi install is what I want. So, without further ado...

Here is where I'm at with it:

I'm using the 12.04 alternate install cd and select "Install Ubuntu" from the boot menu (not sure that's the exact words but it should convey what I selected). So, last night, I went through the steps all well and good, util it got to the bootloader installation step. I don't recall the exact error message from last night but I do recall that it said the installation failed, and that the words "fatal error" were in there somewhere. I just stopped at that point and went to bed. Now, here we are again this morning. I also noticed that it had tried to install grup-pc (not grub-efi)

// =============================================== //

  **** Some info about my partitioning scheme (probably important): ****

// ========================================================================================= //

There are 3, 3 tb disks in the desktop machine I'm installing on.

Partitioning, the boot flag, and partition type was done using gparted live (downloaded and burnt 2 days ago).

- /dev/sda1 is /boot/efi, formatted in fat 32 @ 250 Mib (or 262 Mb)
- There is a /dev/sdb1 and /dev/sdc1 which are the same size as /dev/sda1 (250 Mib), are unformatted, and are just there as spacers so that the partitions following start in about the same pace on sdb and sdc
- /dev/sda2, /dev/sdb2 and /dev/sdc2 are just under 3 tb each (the lions share of the avialable disk space)
- There are swap partitions as /dev/sda3, /dev/sdb3 and /dev/sdc3 wich are roughly 5.3 Mib in size

- Raid 5 was created across sda2, sdb2, and sdc2 using the installer in the 12.04 alternate cd (/dev/md0)
- With the same installer, a volume group and logical volumes were created on /dev/md0, they are...
  * /system/flamingamino (the name of my website (@ 512 Mib/ 500 Mb)
  * /system/storage (place for home directory and all regular user data stuffs @ roughly 2 tb)
  * /system/programming (place for development work (@ 512 Mib/ 500 Mb)
  * /sytem/virtualization (place for vm's @ 512 Mib/ 500 Mb)
  * /system/root (place for the core system to reside @ 512 Mib/ 500 Mb - not including the boot loader [which 'should' be in /boot/efi?] )
// ========================================================================================= //


-> This morning I boot the alternate install cd, select "Install Ubuntu" and proceed through the steps. I make a pit stop in the partitioner to check whether everythinng is still set up properly. md0, and all lvm stuff are detected (along with the physical partitions). I visit each logical volume and have to re-enter the mount point, the use as feild (now set to ext4 for all lv) and the instruction telling it to reformat it - for each of the logical volumes. I also visit /boot/efi. I see that it doesn't have much you can do with it in the partitioner but I notice that the boot flag is set and the use as field is set to efi system partition and that the mount point is /boot/efi. I exit out "done with this partition" <- or something like that.

// ================================================== //

  **** Clue from the partitioner and where I'm stuck this very moment... ****

// ========================================================================================= //

Right after clicking the button in the partitioner to go forward and format everything - I get the following error message. I'm hoping it indicates a way I can solve the issue on the comand line and then move forward with the install. Until I can determine what to do from here I don't plant to do anything with it. It says...

```

  ------------------------------------| [!!] Partition disks |-----------------------------------------

  The attempt to mount a file system with type vfat in SCSI1 (0.0.0), partition #1 (sda) at
  /boot/efi failed.

  You may resume partitioning from the partitioning menu.

  Do you want to resume partitioning?

  <Go Back>                                                                            <Yes>    <No>

------------------------------------------------------------------------------------------------------


```


**** ?? What is it telling me that I can use to get back on track and succeed with this install ?? ****

Thanks in advance for helping.  I'm stuck and I really need some suggestions.

---

### Post by ClientAlive on 2013-03-20
bump

---


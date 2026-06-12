---
title: "Trouble with 12.04 64Bit installation"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by hijackMe on 2012-06-05
Hello World,
I am new to this Forum, read a few topics here and there but now I need your people's help.

While installing Ubuntu 12.04 64bit  from an USB stick (created with startup disk creator, after thousands of tries with installing it from disk), I always get the message "couldn't read file" and "need to load kernel first".

I am on a 12.04 live disk system now, so I hope to fix this via this live disk..
I gathered some informations for you, but don't know what exactly to do.

version of kernel: 3.2.0-23-gerneric
grub version: 1.99-21ubuntu3

Do I have to update the kernel?
If yes, do I have to mount the root partition (partitioned the disk into root (sda1) for /, home (sda2) for /home and swap (sda3)) and update the kernel there?

And do i have to install the boot loader into sda (mbr of diskß) or sda1, the root partition?

I read something to introduce kernel  in grub.conf but all I can find is:
```
/boot/grub# ls
gfxblacklist.txt  grubenv
```and

```
/etc/grub.d# ls
00_header        10_linux      20_memtest86+  40_custom  README
05_debian_theme  20_linux_xen  30_os-prober   41_custom
```If you wish a log file, please tell me how I can create it being in this live mode.
Lots of questions, I know, but I am unexperienced facing this kind of trouble while installing ubuntu.

Thanks for your time reading my posting!

---

### Post by dino99 on 2012-06-05
it seems that grub is not well installed.

from the livecd, open a terminal and run: 

sudo grub-install /dev/sda
sudo update-grub

then try to boot from hdd again

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-06-05
You have to mount the partition first if installing from the liveCD. Dino's install instructions work to reinstall from inside your install or install to another MBR from inside your install.

You can run the Boot-Info report so we can make suggestions or try the auto repairs.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by hijackMe on 2012-06-05
Hey, couldn't answer faster, came home just a few minutes ago.

So here's the BootInfo's link [http://paste.ubuntu.com/1025397/](http://paste.ubuntu.com/1025397/)

sdb is my usb stick from which the live cd is running and the installation comes from.

[COLOR=Red]EDIT:[/COLOR]
_I have to add some new information._
When I select the Ubuntu distribution from the bootscreen and hit enter the following message appears:
```

[2.128057]Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
[2.128096] Pid: 1, comm: swapper/0 Not tainted 3.2.0-23-generic #36-Ubuntu
[2.128131] Call Trace:
[2.128168] [<ffffffff81644023>] panic+0x91/0x1a4
[2.128205] [<ffffffff81cfc0a5>] mount_block_root+0x163/0x18e
[2.128241] [<ffffffff81cfcc2a>] handle_initrd+0x4c/0x295
[2.128276] [<ffffffff81cfceb9>] initrd_load+0x46/0x5d
[2.128311] [<ffffffff81cfc33b>] prepare_namespace+0xdf/0x1a6
[2.128347] [<ffffffff81cfbd63>] kernel_init+0x149/0x14e
[2.128383] [<ffffffff81666bf4>] kernel_thread_helper+0x4/0x10
[2.128418] [<ffffffff81cfbc1a>] ? start_kernel+0x3c7/0x3c7
[2.128454] [<ffffffff81666bf0>] ? gs_change+0x13/0x13

```


Thanks so far!

---

### Post by oldfred on 2012-06-05
Boot script looks like everything is installed in the correct place. Grub2's boot loader in the MBR is looking into sda1 for the rest of grub & /boot folder which has the kernel & initrd.img files.

But kernel panic is a major error. Not sure why. Usually that is saying it cannot find the rest of the files or something. Not seen that too often except when I boot ISO directly and have wrong paths for files in ISO. 

Did install complete normally? Does recovery also give same error? You get grub menu by holding shift from BIOS until menu appears. Then you should also have a choice of a recovery mode, but I expect it to have the same error.

You can chroot into your install and do a full update/repair.

Instructions on chroot:
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then once chrooted.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by hijackMe on 2012-06-05
> **oldfred said:**
> 
But kernel panic is a major error. Not sure why. Usually that is saying it cannot find the rest of the files or something. Not seen that too often except when I boot ISO directly and have wrong paths for files in ISO. 

Did install complete normally? Does recovery also give same error? You get grub menu by holding shift from BIOS until menu appears. Then you should also have a choice of a recovery mode, but I expect it to have the same error.


Yes, by holding down shift I get the Grub menu, but as you expected, the recovery mode has the same error.

It installed completely and normally, that's why i can't imagine what's going wrong there..
All I can say is, that I used the "startup disk creator" from Dash Home to make my USB stick bootable. I downloaded an iso-file twice which I used for the disk creator to get the installation on my stick.

But I have to mention, that I never got so many crashes, freezes etc etc while installing Ubuntu on this machine. I used the ubuntu-12.04-desktop-amd64.iso for an AMD Phenom II X4 965 Processor x4 64-bit.

Boot-Repair didn't work too :(
I will try your chroot advice, otherwise I reinstall everything again..

---

### Post by hijackMe on 2012-06-06
OMG, I can't imagine why nothing is working to get any OS installed on this machine.. Tested the HDD, it's fine, CD-ROM drive is working too..

Yesterday night, I installed Ubuntu 12.04 via CD again, it installed fine without anything, I boot -> error.

What I am trying now is to format the entire HDD to GUID Partition Table from former MBR.
I will download two other distributions of Ubuntu, just to look if it's this 12.04 which causes this problems.

[COLOR=Blue]EDIT:[/COLOR] 
After reading this: [https://help.ubuntu.com/12.04/installation-guide/index.html](https://help.ubuntu.com/12.04/installation-guide/index.html)
I will try the alternate releases instead of desktop stuff.
I am at university right now, but will give new informations in the evening.
Wish me luck.

---

### Post by oldfred on 2012-06-06
If using gpt with BIOS, but sure to create the extra 1MB unformated bios_grub partition. 

I use gpt and once I created that installs were just like any other install, but without it, it can be a big issue. Grub needs a place to put core.img and with gpt the space after the MBR does not exist so it needs that bit of extra room in gpt partitioned drives.

If booting with UEFI then you do not need the bios_grub partition but have to have a efi partition which should be the first partition on the drive, FAT32 and 200 or 300MB. I normally suggest both partitions for new gpt drives as it is difficult to go back and add a new partition at the beginning of the drive even if not UEFI today.

---

### Post by hijackMe on 2012-06-07
Ok nice, this is something i didn't know.

> **oldfred said:**
> If using gpt with BIOS, but sure to create the extra 1MB unformated bios_grub partition. 


Do you mean I should left about 1MB empty at the beginning?
Something like:
_____________________________________________________________
|  1MB unformated  |  / mount point  |  /home mount point  |  swap  |

What was curios for me was, that I formatted the entire disk with guid, after installing the alternate-iso the disk's partitioning was MBR..

Is it useful to partition the disk with 'Disk Utility' from the live disk before going into the installation?
My thoughts were that it would save me a little bit of time, because to read here I have to boot with live disk anyway :/

EDIT: by partitioning UEFI, the first partition which will be FAT32, do i have to set a mount point? If yes, which one?

Thanks, hijackme

---

### Post by oldfred on 2012-06-07
No mount for efi partition, but you do install grub to the efi partition. If BIOS you create the bios_grub partition, but never see nor use it again. Since it is unformated many tools do not even show it. And If BIOS boot with gpt you install to the MBR just like BIOS. In gpt it is called the protective MBR and normally  is just used to let old disk tools know it is not MBR(msdos) partitioning.

Some have had issues with Disk Utility, I use gparted without any issue for creating my gpt partitioned drives.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table.
 In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

---

### Post by hijackMe on 2012-06-08
First, I want to thank you, that you still answering me although I'm a little hard to handle and my english isn't the best.

I guess I had to spend more time with this filesystems and formatting stuff.
I  believe my Mainboard (Asus m4a77t) doesn't support (u)efi mode, but I  read you can GPT partition without EFI by following this steps:

*you need a special boot partition with these properties*

[LIST]
[*]nr of partition: 1
[*]identifier: ef02
[*]name: bios_grub (GParted) - BIOS Boot-Partition (gdisk)
[*]filesystem: nothing - RAW-state
[*]size: 34-100 KiB
[/LIST]
I will use gparted, so we can communicate about one application and maybe [COLOR=Black]it's easier for you to give me concrete instructions to follow.[/COLOR]

My steps in gparted, outgoing from an unallocated 500 GB disk:

1) Device -> create partition table with GPT

2) create a unformatted 1MB sized primary partition labeled bios_grub
[COLOR=RoyalBlue]Q:[/COLOR] *[COLOR=RoyalBlue]Where can I set identifier to ef02 in gparted?[/COLOR]*

[I][COLOR=Red]apply operations to drive

[/COLOR][/I][COLOR=Red][COLOR=Black]3) right click on the 1 MB partiotion -> manage flags[/COLOR][/COLOR][COLOR=Red] [COLOR=Black]-> bios_grub[/COLOR][/COLOR][I][COLOR=Red]
[/COLOR][/I]
I  add a screenshot, please tell me where I did go wrong, or if it's ok so  far. The unallocated ~460GB would be partitioned while running the  installation or should I do it before?
And do I set the root-partition with the bootflag in the installation?
[[IMG]http://img209.imageshack.us/img209/7831/screenshotfrom201206081.png[/IMG]]("http://imageshack.us/photo/my-images/209/screenshotfrom201206081.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

I guess my installations crashed so many times because I did not know anything about the partitioning.

---

### Post by oldfred on 2012-06-09
In gparted it is the bios_grub flag. If you download and run gdisk you will then see the ef02 setting.

My flash drive is also gpt, & I have used gparted to format all my gpt drives.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdb
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 31375360 sectors, 15.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ECD862C9-27C6-44EF-846C-5272FE5A465F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31375326
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  KingstonData
   2            4096        14749695   7.0 GiB     0700  
   3        14749696        29327359   7.0 GiB     0700  
   4        29327360        31373311   999.0 MiB   0700  
fred@fred-Precise:~$ 

```

---

### Post by hijackMe on 2012-06-10
Yeah, it showed me ef02, too. 
While another installation of Ubuntu, it asked me if I wish to install grub2 into MBR, I accepted. The installation told me there where no complications if this is the only running os.
But while first boot, grub didn't came up and it showed me a purple plain screen.
Second time, I got this damn kernel panic error message..

In installation's partition menu, do I have to set a boot-flag to the /-root partition  as well? Because that's what I did..
Which would be the booting partition when I don't set any boot flag?
Because it didn't showed me a place to install the boot loader to while installing.

picture from my root partition type efi system partition correct?
[[img]http://www.abload.de/img/screenshotfrom2012-0638caq.png[/img]](http://www.abload.de/image.php?img=screenshotfrom2012-0638caq.png)

greets from live disk, hijackMe

---

### Post by oldfred on 2012-06-10
In BIOS/MBR boot flag is only used by Windows, but some BIOS will not let you boot unless you have a boot flag on a primary partition.

In UEFI/gpt you set a boot flag from gparted to make the efi partition ef00 or the boot partition. It is not really the same thing as a boot flag in MBR.

You only set a boot flag on an efi partition in gparted, never on any other partion. But we have seen some Intel motherboard with BIOS that will not boot from a gpt partitioned drive unless you have a boot flag. I normally suggest creating both efi & bios_grub and  let the installer sort out which it is using. You do not need both, but efi only is 200 to 200MB and bios_grub 1MB so with new drives, creating both does not use much of a drive.

If you get a purple screen, you have have booted thru grub2's boot loader and then had video issues. Some very new (and older) systems also need other boot parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by hijackMe on 2012-06-11
Still not further in progress..

I tried the nomodeset param:
[[IMG]http://www.abload.de/img/imag0122-168kba.jpg[/IMG]]("http://www.abload.de/image.php?img=imag0122-168kba.jpg")

I still get this error message. 
[[IMG]http://www.abload.de/img/imag0124jbcvw.jpg[/IMG]]("http://www.abload.de/image.php?img=imag0124jbcvw.jpg")


This site told me it could be a System RAM specific error, is this right?

[http://www.dedoimedo.com/computers/kdump-vfs-error.html](http://www.dedoimedo.com/computers/kdump-vfs-error.html)

Beside, I looked in gparted and 'Disk Utility' in live disk mode and see what I am seeing right now:
[[IMG]http://www.abload.de/img/screenshotfrom2012-06ijur2.png[/IMG]]("http://www.abload.de/image.php?img=screenshotfrom2012-06ijur2.png")

Why is my swap-partition showed as unknown file system?
While installing the step, I rememer it was called something like "wiping swap space" took me very very long to proceed.

I'm sorry for the big pictures, but I want to document this as exact as I am able to, reduced the size to the optimum to see the details.

What I will try to do now:
- do a complete RAM check
- after RAM check, if successful, chroot to fix grub entry if possible
- otherwiseI will install Ubuntu again with recommeded settings not my manual setup partitioning

regards, hijackMe

---

### Post by hijackMe on 2012-06-11
Going further towards the error:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

```sda1 is my unformatted bios_grub boot partition, I believe it is unable to boot from there because its just unformatted right?
I read, that it has to be an ext-formatted drive to chroot it.
How to proceed?

Edit:
while chroot I entered the apt-get upgrade command and got this kind of message:
dpkg: error: parsing file »/var/lib/dpkg/available«, near line 6590 package »libxslt1.1«:
 after field name »
E: Sub-process /usr/bin/dpkg returned an error code (2)


regards, 
hijackMe

---

### Post by YannBuntu on 2012-06-11
Hi
according to your log, you have grubenv error, so it may be useful to indicate the URL that will appear after running the Boot-Repair's "Recommended repair". It will probably indicate the type of error you get when installing GRUB.

---

### Post by hijackMe on 2012-06-11
> **YannBuntu said:**
> Hi
according to your log, you have grubenv error, so it may be useful to indicate the URL that will appear after running the Boot-Repair's "Recommended repair". It will probably indicate the type of error you get when installing GRUB.
[COLOR=RoyalBlue]
[COLOR=Blue]Here's the boot-repair log:[/COLOR][/COLOR]
[http://paste.ubuntu.com/1035480/](http://paste.ubuntu.com/1035480/)

but as you will see there is no grub installed at the moment on sda.. this is my problem

can't fix with recommended repair, because this command
```
sudo chroot "/mnt" apt-get install -y --force-yes grub-pc

``` which I have to enter gets me this error (trying to translate cause language is set to german):
preconfiguration of packages ...
```
dpkg: error: parsing of file »/var/lib/dpkg/available«, near line 6590 package »libxslt1.1«:
 after field name »
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by oldfred on 2012-06-11
fdisk is for the older MBR(msdos) partitioning. You have to use gdisk or parted to list partitions for gpt partitioning. 

The bios_grub partition should be unformated. Also swap may show as unknown if you encrypted your /home as it also encrypts swap. Disk tools cannot see encrypted partitions, they are encrypted. The only info they can see is from partition table.

Does not advanced repairs from Boot-Repair work. That is easier than any of the manual procedures.

---

### Post by hijackMe on 2012-06-11
> **oldfred said:**
> fdisk is for the older MBR(msdos) partitioning. You have to use gdisk or parted to list partitions for gpt partitioning. 

The bios_grub partition should be unformated. Also swap may show as unknown if you encrypted your /home as it also encrypts swap. Disk tools cannot see encrypted partitions, they are encrypted. The only info they can see is from partition table.
Ah ok thanks for information, I did encrypt it indeed.
> 
Does not advanced repairs from Boot-Repair work. That is easier than any of the manual procedures.

The not advanced repair from Boot-Repair showed a window where I had to enter this commands in a terminal:
sudo chroot "/mnt" apt-get install -fy
sudo chroot "/mnt" dpkg --configure -a
sudo chroot "/mnt" apt-get install -y --force-yes grub-pc

The 1st and 2nd command are going thru, 3rd is giving me the error i posted above.

---

### Post by YannBuntu on 2012-06-11
> **hijackMe said:**
> [COLOR=RoyalBlue]
[COLOR=Blue]Here's the boot-repair log:[/COLOR][/COLOR]
[http://paste.ubuntu.com/1035480/](http://paste.ubuntu.com/1035480/)

ok, you made big changes since last log.
You now have a GPT partitioning. Your BIOS-boot partition seems correct. Your EFI partition too.
Your BIOS is currently setup in Legacy mode (not EFI) , so your BIOS-boot partition will be used, not your EFI partition.

I don't know how to solve the dpkg error. If nobody has better idea, i would try this: burn a SuperGrubDisk, boot on it, in its menu let it boot your installed Ubuntu, then when you are in your installed Ubuntu session, **connect internet**, open a terminal (Ctrl+Alt+T) and type the following command:
```
sudo apt-get install grub-pc
```

---

### Post by oldfred on 2012-06-11
The only other thing I see is two efi partitions. sda4 has to be a data partition not an efi partiton. You should be able to use gparted to just change flag.

You have grub2's core.img in the bios_grub partition which is correct for BIOS/MBR boot, but no grub.cfg in the main partition. That may be because it was flagged as an efi partition and grub2 would not write its grub files into an efi partition, just a boot loader when using UEFI.

So try changing "boot" or efi flag on sda4 and reinstalling grub2 again.

---

### Post by hijackMe on 2012-06-11
[COLOR=Red]NOTE: EDITED POST[/COLOR]

Thanks for reply.

I removed the boot-flag in gparted from sda4.

I tried to reinstall grub via ```
apt-get install grub-common grub-pc
```but like the last time I got this error message
```
dpkg: error: parsing of file »/var/lib/dpkg/available«, near line 6590 package »libxslt1.1«:
 after field name »
E: Sub-process /usr/bin/dpkg returned an error code (2)
```Maybe I should try burning a SuperGrubDisk like you mentioned before YannBuntu.
Really I have no clue what to do otherwise :/

---

### Post by YannBuntu on 2012-06-11
i agree with oldfred. You can remove the boot flag from sda4 via the gParted utility.

---

### Post by hijackMe on 2012-06-11
To fix the package error, I entered this command:
```
sudo dpkg --clear-avail
```I was lucky, could have been harder and 
[COLOR=DarkRed]apt-get install grub-common grub-pc[/COLOR] was able to finish.

I was able to finish the "HOWTO: Purge and Reinstall Grub2" Tutorial, btw great work to the author [COLOR=RoyalBlue]drs305[/COLOR][COLOR=Black].
I will do a reboot and let you guys know if it worked, keep your fingers crossed for me ;-)

[COLOR=Red]EDIT:[COLOR=Black]
First boot I got this purple screen again and had to reboot cause it seemed frozen..
Second boot, grub showed up and I could select Ubuntu or Ubuntu - recovery mode
after pressing enter the kernel panic error showed up again.

Does it damage the grub files in any sort? Because the first boot is with purple screen and the second gets me thru but ends in a kernel panic error..

At third boot I appended the nomodeset parameter to linux /boot line but nothing changed and I ended up in the kernel panic error.

I try the grub options from Boot-Repair to set the boot parameters.

[COLOR=Blue]EDIT 2:[COLOR=Black]
I failed to use Boot-Repairs "set kernel options"
I have access to the grub.cfg via chroot.
Could you guys tell me how I can append something like 'nomodeset' or 'acpi=off' to the grub file?
Can I edit the grub.cfg at all because 2nd line tells me "# DO NOT EDIT THIS FILE".
[/COLOR][/COLOR] [/COLOR][/COLOR][/COLOR]

---

### Post by oldfred on 2012-06-11
First boot had error so grub automatically showed menu, so you could boot with recovery mode. You should be able to hold shift key from BIOS until menu appears otherwise.

Are you replacing quiet splash with nomodeset. Then you can sometimes see other errors as it is booting. It may not be last command posted, though.

Sometimes other boot parameters are required in addition to nomodeset.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You should  edit grub.cfg. And you should be able to manually add boot parameters until you find what works, then you edit /etc/default/grub from inside your install once you have finalize what works.

---

### Post by hijackMe on 2012-06-12
> **oldfred said:**
> 
Are you replacing quiet splash with nomodeset. Then you can sometimes see other errors as it is booting. It may not be last command posted, though.

I tried different variations after the 'quiet splash' and before ' $vt_handoff like here:
[IMG]http://www.abload.de/image.php?img=imag0122-168kba.jpg[/IMG][[IMG]http://www.abload.de/img/imag0122-168kba.jpg[/IMG]]("http://www.abload.de/image.php?img=imag0122-168kba.jpg")

I replaced quiet splash with nomodeset etc etc
All tries ended up showing this error:
```

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```I don't think it's due to graphic issues.. Rather the kernel does cause the problems.
But I don't know what I could change.
Should I change the version?

[COLOR=Blue]NOTE:[/COLOR] On the second page of this thread, I posted a detailed error message with a black screen.

---

### Post by oldfred on 2012-06-12
This thread with same issue had grub in wrong location and BIOS showing wrong size.
[http://ubuntuforums.org/showthread.php?t=1751574](http://ubuntuforums.org/showthread.php?t=1751574)

This one says it may be an issue with initramfs. And your boot files are missing a link file which normally is not used, but it shows it did not finish the install correctly.
[http://askubuntu.com/questions/116635/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-oo-swapper](http://askubuntu.com/questions/116635/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-oo-swapper)

```
   6.857421875 = 7.363100672    boot/initrd.img-3.2.0-23-generic               3
   4.662830353 = 5.006675968    boot/vmlinuz-3.2.0-23-generic                  1
   4.662830353 = 5.006675968    vmlinuz                                        1

```

---

### Post by hijackMe on 2012-06-26
Today my new hdd arrived.
All errors were caused due to a damaged hdd, which the SMART test couldn't reveal..
I used [COLOR=RoyalBlue]Hiren's Boot CD[/COLOR] with a great choice of utilities to analyze the hdd with manufacturers' tools for almost every hdd.

Thanks to everyone who tried to help me in this thread especially oldfred and YannBuntu!

---


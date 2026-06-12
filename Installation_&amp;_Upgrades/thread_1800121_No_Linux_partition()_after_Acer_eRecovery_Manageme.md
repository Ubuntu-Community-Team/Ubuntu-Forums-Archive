---
title: "No Linux partition(?) after Acer eRecovery Management messed up things"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by hero2 on 2011-07-08
Hi everybody!

I tried posting this problem on a thread called "Grub/XP/Vista Bootloader" here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) but noone seem to be reading that, so now I am moving the subject to this new thread.

A have an Acer netbook with Windows 7 Starter pre-installed and a recovery-partition, later I split the windows 7 partition into 2 and recently I installed Ubuntu 10.04.2 to see if that runs faster.
On the boot-menu, beside Ubuntu, there is "Windows Vista" and "Windows 7", and unfortunately I was curious and wanted to see what "Vista" is. This started a backup/restore program called Acer eRecovery Management, and although I did NOT ask it to do anything before terminating it, it has destroyed the Ubuntu GRUB booter, so when I try to boot the machine, I get this message:

"error: no such partition
grub rescue>"

According to the above mentioned guide on "How to restore the Ubuntu grub bootloader", there is supposed to be a partition called "Linux", but as you can see below, there is NO "Linux"-partition, after Acer eRecovery has messed up things, so what do I do now?

The "/dev/sdb: 4011 MB" below is a USB-memory stick I am booting from, to run the Unix Terminal program.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b987600

Device - - - Boot - - Start - - - End - - - - Blocks - - - Id - - System
/dev/sda1 - - - - - - - - 1 - - - 1567 - - - 12586896 - - 27 - Unknown
/dev/sda2 - - * - - 1568 - - - - 1580 - - - 104422+ - - 7 - HPFS/NTFS
/dev/sda3 - - - - - - 1581 - - 11158 - - 76929562+ - - 7 - HPFS/NTFS
/dev/sda4 - - - - - 11158 - - - 30402 - 154575873 - - - f - W95 Ext'd (LBA)
/dev/sda5 - - - - - 17792 - - - 30402 - 101289984 - - 7 - HPFS/NTFS

Disk /dev/sdb: 4011 MB, 4011851776 bytes
88 heads, 24 sectors/track, 3710 cylinders
Units = cylinders of 2112 * 512 = 1081344 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot Start End Blocks Id System
/dev/sdb1 * 4 3711 3913792 c W95 FAT32 (LBA)
ubuntu@ubuntu:~$


Can anyone help me, please?


Best regards,
Henrik Rosenø

---

### Post by doas777 on 2011-07-08
well, if you have another harddisk, you can try TestDisk to see if the old partition can be salvaged, but it does look like your partitions were at least partially overwritten, so recovery is likely to fail. Photorec is a good tool for finding lost files of specific file types, and may be able to recover some of the data from the currently blank sectors of the drive. Be sure to recover the files to a differant physical hard disk, so you don't recover one file and in the process overwrite 3 others.

Instructions for testdisk and photorec here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by confused57 on 2011-07-08
If you need to recover files(or possibly the linux partition), do as doas777 has suggested.

If you're unable to boot into Windows, you might try installing lilo to the mbr:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive#Step_2__Restore_the_MBR_of_the_internal_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive#Step_2__Restore_the_MBR_of_the_internal_drive)

---

### Post by hero2 on 2011-07-08
> **doas777 said:**
> well, if you have another harddisk, you can try TestDisk to see if the old partition can be salvaged, but it does look like your partitions were at least partially overwritten, so recovery is likely to fail. Photorec is a good tool for finding lost files of specific file types, and may be able to recover some of the data from the currently blank sectors of the drive. Be sure to recover the files to a differant physical hard disk, so you don't recover one file and in the process overwrite 3 others.

Instructions for testdisk and photorec here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I don't get this?!

In the document you refer to it says: 
"Use [any method]("https://help.ubuntu.com/community/InstallingSoftware") to install the **testdisk** package."
But on the website [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) it says:
"TestDisk & PhotoRec are portable applications, extract the files and  the applications are ready to be used. No need to run an installer."
And when I boot the netbook on a USB-memory (I also have an external DVD-drive BTW) and download TestDisk 6.12 for Linux on the above mentioned website, opening it with Archive Manager (default) and extracting everything to a folder on the Desktop, I can't seem to execute any of the files?! And if I open the terminal and write "sudo testdisk" I just get a "command not found"...???

- Hero2

---

### Post by doas777 on 2011-07-11
well, I often use the [ubuntu rescue remix]("http://ubuntu-rescue-remix.org/") live cd which has it built in, but I would try to install it from the repositories.
```
sudo apt-get install testdisk
```as for running it, if you want to run an application that you have unpacked on your desktop, you need to make sure the file is executable, cd to the directory, and then launch it with ./
```

cd ~/Desktop/<AppFolder>
sudo chmod +x ./testdisk
sudo ./testdisk

```

there really isn't much to "installing" most packages in linux. it's pretty much just copying the to /usr/bin or where ever is appropriate, and setting appropriate permissions (including execute).

---

### Post by hero2 on 2011-07-11
> **doas777 said:**
> well, I often use the [ubuntu rescue remix]("http://ubuntu-rescue-remix.org/") live cd which has it built in, but I would try to install it from the repositories.
```
sudo apt-get install testdisk
```

That sounds smart, but didn't really work. I got this message (in the Terminal):

** E: Couldn't find package testdisk**

And I DID connect to the Internet first.

- hero2

---

### Post by jlh68 on 2011-07-11
Try to use the Ubuntu live CD to access your Linux partition.   I suspect that you have reformatted the whole HD.
  
When I set up my dual-boot Acer I resized the WIN7 partition to as small as I could and still have some room (about 35-GB).  I then set up a Linux boot partion, a swap partition, a Linux root partition, and a home partition.  I also installed a GRUB2 customizer program to setup my GURB2.  In Grub2 customizer I x'ed out the vista partition from the start menu so I would not accidentally do what you did. The Grub customizer will also allow you to uncheck past Linux kernel versions. With the 

Remember you will be able to access your windows files with Linux.

See image of my file system.

Here is the Grub2 program: > Grub Customizer 2.1.2

So I suggest starting over.:KS

---

### Post by hero2 on 2011-07-11
> **confused57 said:**
> If you need to recover files(or possibly the linux partition), do as doas777 has suggested.

If you're unable to boot into Windows, you might try installing lilo to the mbr:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive#Step_2__Restore_the_MBR_of_the_internal_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive#Step_2__Restore_the_MBR_of_the_internal_drive)

Why do my attempts to solve ONE problem always lead to NEW problems????

For instance:

The procedure you link to instruct me to do the following command in a terminal:

"sudo apt-get install lilo"

That leads to a message saying something like:

"After this install run liloconfig(8) and execute /sbin/lilo"

But when I write this: "liloconfig(8)" or  "liloconfig (8)" or "sudo liloconfig(8)" or "sudo liloconfig (8)"  in the terminal I just get the message:

"bash: syntax error near unexpected token `8'"
or
"bash: syntax error near unexpected token `('"

This is increasingly annoying. 

- hero2

---

### Post by psusi on 2011-07-11
The (8) is a reference to the man page for that program being in section 8 of the manual, not part of the command.  You don't want to muck with lilo unless you want to get rid of grub.

Did you have a Linux partition to begin with, or was this a WUBI install?

At the grub rescue prompt, type the following commands and post the results:

```

set
ls

```

---

### Post by doas777 on 2011-07-11
> **hero2 said:**
> Why do my attempts to solve ONE problem always lead to NEW problems????

For instance:

The procedure you link to instruct me to do the following command in a terminal:

"sudo apt-get install lilo"

That leads to a message saying something like:

"After this install run liloconfig(8) and execute /sbin/lilo"

But when I write this: "liloconfig(8)" or  "liloconfig (8)" or "sudo liloconfig(8)" or "sudo liloconfig (8)"  in the terminal I just get the message:

"bash: syntax error near unexpected token `8'"
or
"bash: syntax error near unexpected token `('"

This is increasingly annoying. 

- hero2

hmmm, I would not have suggested that, since I recommend attempting to restore the linux partitions. installing lilo might make your windows boot correctly, but it won't fix the lost linux partitions.  but the choice is yours. a better alternative to fixing windows, would be to boot on the windows install disk, and run a [startup repair]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html"). if you do want to restore the lost data, do it now, not later. 

**IF** you want to attempt to restore your linux partitions, here is how I would do it.
we need two hard disks: your current drive (source drive) and the drive you want to recover the files to (dest drive).


[LIST=1]
[*]download and burn off a ubuntu live CD (but not to the source drive).
[*]boot off the live cd
[*]run ```
sudo apt-get install testdisk
``` (I have confirmed that testdisk is in the [universe repositories]("http://packages.ubuntu.com/natty/testdisk").)
[*]identity the device name (/dev/sdX) for both the source and destination drives. fdisk -l may help
[*]run ```
sudo testdisk
``` and walk through the menu as the link I sent above shows.
[/LIST]

with luck, you will be able to restore the missing linux partitions from your source drive to the destination drive. then you can just swap them, or you can use dd to copy the data back to the source drive. let me know when you get to this point.

---

### Post by hero2 on 2011-07-11
> **psusi said:**
> The (8) is a reference to the man page for that program being in section 8 of the manual, not part of the command.  You don't want to muck with lilo unless you want to get rid of grub.

Did you have a Linux partition to begin with, or was this a WUBI install?

At the grub rescue prompt, type the following commands and post the results:

```

set
ls

```

I don't know what a "WUBI install" is, I just know that I installed Ubuntu 10.04.2 from a CD, because installing it from a USB-memory stick did not work.

"set" command result: 

prefix=(hd0,6)/boot/grub
root=hd0,6

"ls" command result: 

(hd0) (hd0,5) (hd0,3) (hd0,2) (hd0,1)

- hero2

---

### Post by doas777 on 2011-07-11
> **hero2 said:**
> I don't know what a "WUBI install" is, I just know that I installed Ubuntu 10.04.2 from a CD, because installing it from a USB-memory stick did not work.

a WUBI install, is an installation where you were already booted into windows when you performed the install. it installs ubuntu as an application inside windows and does not require the formatting of partitions. after install it works like a dualboot, but the ubuntu partitions are actually virtual disks on the windows partition. does that sound like what you did, or did you boot from the liveCD to install?

---

### Post by hero2 on 2011-07-12
> **doas777 said:**
> **IF** you want to attempt to restore your linux partitions, here is how I would do it.
we need two hard disks: your current drive (source drive) and the drive you want to recover the files to (dest drive).


[LIST=1]
[*]download and burn off a ubuntu live CD (but not to the source drive).
[*]boot off the live cd
[*]run ```
sudo apt-get install testdisk
``` (I have confirmed that testdisk is in the [universe repositories]("http://packages.ubuntu.com/natty/testdisk").)
[/LIST]
 Dear doas777

Why do you repeat instructions that don't work?

Now I tried (again):

1. I booted on a CD with Ubuntu 10.04.2.
2. I connected to the internet (making sure it works).
3. I started the Terminal (Applications -> Accessories -> Terminal)
4. At the prompt (ubuntu@ubuntu:~$) I write: sudo apt-get install testdisk
5. I get the following messages:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package testdisk

6. And if I write this command: sudo testdisk
I get this response: sudo: testdisk: command not found

- hero2

---

### Post by doas777 on 2011-07-12
> **hero2 said:**
> Dear doas777

Why do you repeat instructions that don't work?

Now I tried (again):

1. I booted on a CD with Ubuntu 10.04.2.
2. I connected to the internet (making sure it works).
3. I started the Terminal (Applications -> Accessories -> Terminal)
4. At the prompt (ubuntu@ubuntu:~$) I write: sudo apt-get install testdisk
5. I get the following messages:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package testdisk

6. And if I write this command: sudo testdisk
I get this response: sudo: testdisk: command not found

- hero2

because I've duplicated this on 3 boxes, both 32 and 64, desktop and server:
```
user@Lucid:~$ sudo apt-get install testdisk
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  testdisk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,547kB of archives.
After this operation, 4,784kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe testdisk 6.11-1 [1,547kB]
Fetched 1,547kB in 3s (422kB/s)     
Selecting previously deselected package testdisk.
(Reading database ... 351550 files and directories currently installed.)
Unpacking testdisk (from .../testdisk_6.11-1_i386.deb) ...
Processing triggers for man-db ...
Setting up testdisk (6.11-1) ...
user@Lucid:~$ 
```

the instructions work, just not for you. why I don't know.. you may have disabled the universe repositories I suppose, but that would be silly.

if you are having trouble getting it installed, then you might want to look at the ubuntu-rescue-remix livecd that I linked earlier in the thread. testdisk and photorec are already installed.

---

### Post by hero2 on 2011-07-12
> **doas777 said:**
> because I've duplicated this on 3 boxes, both 32 and 64, desktop and server:
```
user@Lucid:~$ sudo apt-get install testdisk

```the instructions work, just not for you. why I don't know.. you may have disabled the universe repositories I suppose, but that would be silly.

if you are having trouble getting it installed, then you might want to look at the ubuntu-rescue-remix livecd that I linked earlier in the thread. testdisk and photorec are already installed.

I guess I will have to use the 'rescue-remix'... But I have to protest against your wording. I did NOT disable anything! If the repository is disabled then it is because ubuntu-10.04.2-desktop-i386.iso decided to disable it on my Acer Aspire One netbook (both when booting it from a CD and from a USB-memory).
Should I report it as a bug? And in that case, where?

---

### Post by doas777 on 2011-07-12
> **hero2 said:**
> I guess I will have to use the 'rescue-remix'... But I have to protest against your wording. I did NOT disable anything! If the repository is disabled then it is because ubuntu-10.04.2-desktop-i386.iso decided to disable it on my Acer Aspire One netbook (both when booting it from a CD and from a USB-memory).
Should I report it as a bug? And in that case, where?

Fair enough. I didn't mean to imply that you did; in fact quite the opposite (because it would indeed be a silly thing to do).

it may help to run:
```
sudo apt-get update && sudo apt-get install testdisk
``` in case your system has never yet scraped the repository and updated its inventory.

Further up the thread, I gave instructions for launching an application that you have downloaded as a compressed archive, without an install. does that work for you, with the version of testdisk you had already downloaded to your desktop?

---

### Post by hero2 on 2011-07-13
> **doas777 said:**
> Fair enough. I didn't mean to imply that you did; in fact quite the opposite (because it would indeed be a silly thing to do).

it may help to run:
```
sudo apt-get update && sudo apt-get install testdisk
``` in case your system has never yet scraped the repository and updated its inventory.

Further up the thread, I gave instructions for launching an application that you have downloaded as a compressed archive, without an install. does that work for you, with the version of testdisk you had already downloaded to your desktop?

I haven't tried downloading and running a compressed archive. Remember that we are talking about booting on an external device, so I would have to download it again everytime I boot. 
Reserving a space for saving files on a bootable USB-memory didn't work for me, neither with unetbootin-win-549.exe nor usb-creator.exe! Actually I wasted a lot of time trying to install Ubuntu with a USB-stick. It wasn't possible on my Acer Aspire One netbook. I HAD to use a CD (in an external USB DVD-drive). 

I tried booting on the 'rescue-remix' and running testdisk, and it found 2 Linux-partitions and tried to restore them, but that only changed the error-message from GRUB ("unknown filesystem" I think). So in the end I followed the instructions "Windows 7 - MBR - Restore Windows 7 Master Boot Record" here:
 [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html) 
First trying "Startup Repair" with no apparent result, then the command "bootsect /nt60 SYS /mbr" and THAT made the machine bootable again. So I guess I will have to reinstall Ubuntu all over. But I didn't have any files on ubuntu yet, so no big problem.

But isn't it strange that apparently LILO could be installed by the command "sudo apt-get install lilo" but NOT testdisk??

BTW: I also sent this question to Acer support a week ago, but although the autoresponse said that I would hear from them within 24 hours, I haven't heard from them - until this moment, while I am writing this message. They just inform me that the (1 year?) warranty has ended, so I can call a phone number that costs 50p/min.

So I will finish by saying: Thank you everybody for helping me solving the problems created by Acer eRecovery Management!

Now I think I will burn a GParted liveCD and 'thoroughly' delete the Linux partitions to avoid any problems in the reinstall.

- hero2

---

### Post by hero2 on 2011-07-13
UPS! This is kind of strange. GParted 0.8.1-3 thinks that there are no partitions at all on the harddisk!? Why is that?

Testdisk 6.11 finds them all.

And now I can't install Ubuntu 10.04.2, because it cannot see any partitions at all...

---

### Post by doas777 on 2011-07-13
are you recovering them to a differant drive? that is essential for this to work. I hope the recovery in place didn't overwrite everything.

---

### Post by psusi on 2011-07-13
You probably corrupted your partition table.  What does sudo fisk -lu show?

---

### Post by hero2 on 2011-07-13
> **psusi said:**
> You probably corrupted your partition table.  What does sudo fisk -lu show?

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b987600

   Device - - Boot      - - - Start         - - - - - End - - - -      Blocks - - - -   Id - -  System
/dev/sda1 - - - -              - - - 63 - - - - 25173854 -    12586896 -    - 7  - - HPFS/NTFS
/dev/sda2 -   * -    - 25173855 - -    25382699 - -      104422+ -   - 7  - - HPFS/NTFS
/dev/sda3 - - - -        25382700   - - 179241812    - 76929556+ -   7  - - HPFS/NTFS
/dev/sda4       - - - - 179241867 -   488408129   - 154583131+   - f  - - W95 Ext'd (LBA)
/dev/sda5 - - - -       179243008 -   281366527    - 51061760   - - 83  - Linux
/dev/sda6       - - - - 281368576   - 285812719     - 2222072   - - - 82  - Linux swap / Solaris
/dev/sda7       - - - - 285814784   - 488394751   - 101289984    - - 7  - HPFS/NTFS

Disk /dev/sdb: 4011 MB, 4011851776 bytes
88 heads, 24 sectors/track, 3710 cylinders, total 7835648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7835647     3913792    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by psusi on 2011-07-13
Yep, your extended partition extends past the end of the disk.

---

### Post by hero2 on 2011-07-14
> **psusi said:**
> Yep, your extended partition extends past the end of the disk.

Urrgh! And thank you for being able to spot that!

Since GParted can shrink a partition, it would be nice if it could deal with this problem, but it won't recognize any partitions at all...

But what about fdisk or testdisk or other utilities on the 'rescue-remix'?

Do I have to backup valuable stuff in the extended partition and then delete it and recreate it?
Or is there a tool that can simply change the value of its end-point in the partition table? Or something like that?

BTW: There is a discussion of the same problem here: [https://bugzilla.gnome.org/show_bug.cgi?id=624078#c5](https://bugzilla.gnome.org/show_bug.cgi?id=624078#c5) 

Thank you very much.

- hero2

---

### Post by psusi on 2011-07-14
If you note the exact start and end locations of the logical partitions ( 5, 6, and 7 ) and delete them, as well as the extended partition, you should be able to recreate the extended partition to be the correct size, and then recreate the logical partitions in the same places.  Make sure you use the -u switch to fdisk so it uses sectors instead of cylinders.

---

### Post by hero2 on 2011-07-16
> **psusi said:**
> If you note the exact start and end locations of the logical partitions ( 5, 6, and 7 ) and delete them, as well as the extended partition, you should be able to recreate the extended partition to be the correct size, and then recreate the logical partitions in the same places.  Make sure you use the -u switch to fdisk so it uses sectors instead of cylinders.

Hi psusi!

Thank you for explaining the elegant solution, but when I had deleted the extended partition with testdisk on a 'rescue-remix', I decided to shrink an original partition with GParted, so the new extended partition got a new starting-point. 
After restoring the NTFS-partition in the extended partition I installed ubuntu succesfully.
Now I am going to use Grub Customizer to avoid future execution of that terrible Acer eRecovery Management!

So thank you to everybody!

- hero2

---


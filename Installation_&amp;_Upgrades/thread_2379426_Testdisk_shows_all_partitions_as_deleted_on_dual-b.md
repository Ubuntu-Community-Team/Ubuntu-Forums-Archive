---
title: "Testdisk shows all partitions as deleted on dual-boot system, OK on parted"
date: 2017-12-05
forum: Installation &amp; Upgrades
---

### Post by chiefpokagon on 2017-12-05
After allowing Windows 10 to upgrade my dual boot PC which uses an  SSD it is not booting.  I ran boot-repair and now I get a bootmgr  missing.  So I ran testdisk from the live CD and all partitions show as  deleted.
  TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdf - 120 GB / 111 GiB - CHS 14593 255 63
 Partition               Start        End    Size in sectors
>D HPFS - NTFS              0  32 33    63 221 30    1024000
 D HPFS - NTFS             63 221 31  8111 174 63  129288192
 D HPFS - NTFS           8111 175  1  8218 229 11    1722368
 D Linux                 8219  39 13 13616 190 14   86712320
 D Linux Swap           13616 190 15 14593  66  1   15687680

  A similar (but not the same) question and response asked for a parted  listing of the disks (and I have backed up the partition data to a txt  file).  Although I have included /dev/sda it is used as data, I do see  it does have a boot record, probably a left over from a prior life.

  ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD15EARS-00Z (scsi)
Disk /dev/sda: 2930275055s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End          Size         Type     File system  Flags
 1      206848s     976814079s   976607232s   primary  ntfs
 2      976814080s  2766430207s  1789616128s  primary  ntfs         boot

ubuntu@ubuntu:~$ sudo parted /dev/sdf unit s print
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sdf: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       1026047s    1024000s    primary   ntfs            boot
 2      1026048s    130313813s  129287766s  primary   ntfs
 3      130314240s  132036607s  1722368s    primary   ntfs            diag
 4      132040702s  234440703s  102400002s  extended
 5      218753024s  234440703s  15687680s   logical   linux-swap(v1)

  The partitions seem to be correct in parted so why does testdisk show  them as deleted?  What do I need to do to get my  machine to boot from the SSD (/dev/sdf)?  I suspect that Windows 10 is  not done upgrading, so I need to let that run it's course perhaps before  getting grub back into control.  I don't want to make the situation  worse by choosing the wrong settings in testdisk.

  Although I have used Linux for many years, I am not much of a system administrator.

  I am also confused with too much and sometimes what appears to be  conflicting information about fixing dual-boot issues.  I wish that there is a definitive, simple to  execute procedure to recover from this recurring dual boot/upgrade  error, which appears to not be going away as long as Microsoft refuses  to "support" dual boot and frustrates the upgrade process by wiping out  the boot record.

---

### Post by oldfred on 2017-12-05
Every time you change partitions, it is  another entry that testdisk usually finds. So those may just be old  partitions or old sizes of existing partitions. 

But if you look at your  extended, there is a large gap between start of extended and start of  swap.  

You can use testdisk or parted rescue, many threads with examples:

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 
   [SOLVED] Windows 10 update, Stuck in grub rescue 
[https://ubuntuforums.org/showthread.php?t=2373061](https://ubuntuforums.org/showthread.php?t=2373061)
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by chiefpokagon on 2017-12-14
I did manage to solve this issue using parted, but as I expressed, I felt overwhelmed by the options and the fact that some of the referenced posts are now incomplete because the pastes have disappeared.  I am going to try to post my solution with complete output and hopefully it will help someone see and diagnose the problem clearly.

As I stated in my question, Windows changed the partition table and I could no longer dual boot, it went into grub-rescue.  Whatever I did in grub-rescue (I don't remember) didn't work, but now I am convinced that restoring the partition table is the first (and perhaps only) step to success.  Here are the steps I followed.

0) Obtain a livecd/usb to run Ubuntu since obviously it won't boot off the hard drive.  I found the boot-repair-cd to contain everything that I needed to fix this issue.  See [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

1) Backup the partition table as oldFred posted above:

backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

2) Analyze the output to determine what has gone missing.  What is observed is that there are overlapping partitions in the table.  See my example below.
3) From this determine the starting and ending sectors containing the Ubuntu partition
4) run parted rescue
5) reboot

Example output after booting machine from boot-repair-disk and running parted with annotations [COLOR=#008000]<==[/COLOR]:

(parted) select /dev/sdf                        [COLOR=#008000]<== my OS's are on sdf an SSD [/COLOR]                         
Using /dev/sdf
(parted) print                                                            
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sdf: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  525MB   524MB   primary   ntfs            boot
 2      525MB   66.7GB  66.2GB  primary   ntfs
 3      66.7GB  67.6GB  882MB   primary   ntfs            diag
 4      67.6GB  120GB   52.4GB  extended
 5      112GB   120GB   8032MB  logical   linux-swap(v1)

(parted) unit s                                     [COLOR=#008000]<== set parted to use sectors to simplify entering parameters [/COLOR]                     
(parted) print                                                            
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sdf: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       1026047s    1024000s    primary   ntfs            boot
 2      1026048s    130313813s  129287766s  primary   ntfs
 3      130314240s  132036607s  1722368s    primary   ntfs            diag
 4      132040702s  234440703s  102400002s  extended                                [COLOR=#008000]<== note partitions 4 & 5 have same end so 4 must be ubuntu[/COLOR]
 5      218753024s  234440703s  15687680s   logical   linux-swap(v1)

(parted) rescue                                                           [COLOR=#008000]<== run the rescue option specifying the start and end sectors from 4 & 5 above[/COLOR]
Start? 132040702                                                          
End? 218753020                                                            
Information: A ext4 logical partition was found at 132040704s -> 218753023s.  Do
you want to add it to the partition table?
Yes/No/Cancel? y                                                          [COLOR=#008000]<== Whoo Hooo Found it[/COLOR]
(parted) print                                                               [COLOR=#008000]<== print the results after rescue[/COLOR]
Model: ATA SanDisk SDSSDA12 (scsi)
Disk /dev/sdf: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       1026047s    1024000s    primary   ntfs            boot
 2      1026048s    130313813s  129287766s  primary   ntfs
 3      130314240s  132036607s  1722368s    primary   ntfs            diag
 4      132040702s  234440703s  102400002s  extended
 6      132040704s  218753023s  86712320s   logical   ext4                         [COLOR=#008000] <== This looks much better[/COLOR]
 5      218753024s  234440703s  15687680s   logical   linux-swap(v1)

Now I just rebooted without the boot-repair-disk and grub appeared before Microsoft so helpfully upgraded Windows for me.

I have also encountered this problem with a laptop using UEFI.  As more computers adopt UEFI, this problem will change, but I doubt if it will go away--I still have not been able to get grub to run on the UEFI laptop without using the function key to enter the boot sequence, but that's another fix.  Plus I think Ubuntu users are a thrifty lot and will continue to use older hardware because Ubuntu doesn't demand as many hardware resources as Windows.  It also appears that it is next to impossible to stop Windows from replacing itself periodically with "upgrades". So for those of us who need software which only runs on windows making the dual boot option attractive, the upgrade/"grub-rescue" fiasco will continue to happen.

Thanks to those who have commented and helped.  I still don't know why I got conflicting information, but the parted solution worked and I understand it.  I was apprehensive of this fix until it actually worked!

---

### Post by oldfred on 2017-12-14
Glad you got it working. :)

You can change to solved, so others will find this thread.

Usually with UEFI, Windows does not delete partitions, but does change to make itself first in boot order. Ubuntu also on UEFI install  or major grub update will reset system to make Ubuntu first in boot order.
But some vendors do have totally comply with UEFI standards and then we have to do a work around.

---


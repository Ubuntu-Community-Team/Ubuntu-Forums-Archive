---
title: "Unable to boot Windows 8 after installing Ubuntu 14.04"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by Varun_Maheshwari on 2014-08-12
Hi,

I installed Ubuntu 14.04 on my HP laptop which has Windows 8 installed by manufacturer. I disabled SecureBoot from BIOS and then made a bootable USB for Ubuntu.
First installation of Ubuntu didnt work for me as it kept on rebooting to Windows. So I re-installed Ubuntu from USB, and after that, I am unable to find a way to boot into Windows 8.

I tried checking options in BIOS, but there is nothing like Linux OS or anything else specific to Ubuntu. I have OS boot menu specified as first option in boot options. Still, its booting in Ubuntu everytime and there is no option to boot Windows 8.

[B]One thing that I would like to mention is that while installing Ubuntu, I created 3 partitions from the free space. One was Ext4 mounted as root, another was swap, and third was EFI which I created separately. There was an existing EFI partition that I didnt use, and I mounted the bootloader to the new EFI partition.
[/B]
I tried boot-repair which throws many commands to run in terminal. I did all that, and eventually this is the output -



[COLOR=#0000cd]An error occurred during the repair.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]Please write on a paper the following URL:[/COLOR]
[COLOR=#0000cd]http://paste.ubuntu.com/8032091/[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]In case you still experience boot problem, indicate this URL to:[/COLOR]
[COLOR=#0000cd]boot.repair@gmail.com[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]You can now reboot your computer.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))[/COLOR]


Please help as I need Windows OS. Let me know if you need any more information. And the steps to get that info since I am new to Ubuntu and I wanted to try it out.

Thanks in advance.

---

### Post by kansasnoob on 2014-08-13
I'm sorry to tell you this but you completely erased Windows:

> 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


There is a known bug regarding that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Did you have all of your data backed up?

---

### Post by Varun_Maheshwari on 2014-08-13
Damn it. I didnt back up my data. I thought re-install was going to use the same partitions that I provided it the first time and overwrite the previous Ubuntu install. :(
Do you know of a way to recover my data? I am okay with Windows partition going away, but I had other partitions on that disk which had data. Please oh Please, tell me that there is a way to recover that data.

---

### Post by oldfred on 2014-08-13
Only some of the data and only with lots of work.
The ext4 file system writes all over drive, but Ubuntu is small so not a lot overwritten, but it makes it very difficult to recover.

The free Linux choices are testdisk & photorec. Try testdisk and its deeper search. It looks for the old partitions and if you happen to be lucky the old partition data is intact or not the bits overwritten. Or if that does not work you can use tools to scan drive for anything that looks like a file. Since it just is looking for files it does not find file names, just extensions. You have to manually rename your files, but if photos or music they have internal data that can be used to rename. I only wanted to recover some text files and it took me weeks to compare to last backup as file was written many times and it also recovered all the deleted versions. 

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by kansasnoob on 2014-08-13
> **oldfred said:**
> Only some of the data and only with lots of work.
The ext4 file system writes all over drive, but Ubuntu is small so not a lot overwritten, but it makes it very difficult to recover.

The free Linux choices are testdisk & photorec. Try testdisk and its deeper search. It looks for the old partitions and if you happen to be lucky the old partition data is intact or not the bits overwritten. Or if that does not work you can use tools to scan drive for anything that looks like a file. Since it just is looking for files it does not find file names, just extensions. You have to manually rename your files, but if photos or music they have internal data that can be used to rename. I only wanted to recover some text files and it took me weeks to compare to last backup as file was written many times and it also recovered all the deleted versions. 

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

+1!

Stop using the freshly installed OS ASAP and use only the live USB/DVD that you used to install.

---


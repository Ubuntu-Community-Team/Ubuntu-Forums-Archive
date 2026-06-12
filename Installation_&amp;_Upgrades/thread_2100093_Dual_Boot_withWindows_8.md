---
title: "Dual Boot withWindows 8"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by pc999 on 2012-12-31
Hi, 

I upgraded my PC to a Windows 8 ready machine, but  I cant dual boot WIndows 8 with Ubuntu 12.10.

I install  Windows 8 then I try to install Ubuntu but it says I have no OS installed! On the manual partitioning tool I only get free space too!

What can I do?

Thanks in advance.

---

### Post by oldfred on 2012-12-31
Did you install Windows 8 in UEFI or BIOS mode? 

Have you turned off hibernation in Windows 8?  Not just the standard but the always on one.

Post this from liveCD terminal:

       sudo parted /dev/sda unit s print
    
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)

---

### Post by pc999 on 2012-12-31
Many thanks.

I think I installed it on UEFI mode (does the Hard drive need to be on FAT32 too?).



Turning hibernation off seems very hard, from what I have googled :icon_frown: .



I am suposed to run this "sudo parted /dev/sda unit s print" from the terminal before doing the dual boot install?



This used to be so simple, but I tried with W7 and got the same problem too...

Thanks again, I just a few apps and games way from turning Ubuntu/Linux only :D

---

### Post by oldfred on 2012-12-31
Yes, just to confirm your current partitioning.

You also want to use Windows to shrink the Windows partition and reboot a couple of times so it can run chkdsk and make whatever other repairs it does on a resize. But do not create any new partitions with Windows.

If you want the default install of / (root) & swap you can then just use auto install option into the unallocated space. But you have to boot install media DVD or Flash drive in the same mode UEFI or BIOS as Windows is installed.

---

### Post by pc999 on 2013-01-01
I tried that command and got this

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags



I try to install it after doing that and I still get all the disk as free space although I do have W8 installed and I shrined the W8 partition with W8.

Any idea idea?

BTW I have been looking in the bios and I am not sure if there is a bios mode, in the securo options it allow to other OS, but I do have it in secure W8 UEFI mode right now!

Thanks!

---

### Post by oldfred on 2013-01-01
Parted and therefore gparted which is graphical parted are not seeing any gpt based partitions.

Did you have Windows installed with dynamic partitions? But it still should have seen the underlying msdos partitions??

Does Windows still work?

---

### Post by pc999 on 2013-01-01
> **oldfred said:**
> 
Does Windows still work?

Perfectly :confused:

---

### Post by spankler60 on 2013-01-01
Is there a thread where step-by-step instructions are given to do *everything* to set up a dual boot with Windows 8 and Quetzal Xubuntu? Including repartitioning, best disk formatting, etc.?

---

### Post by oldfred on 2013-01-01
@spankler60
A lot of how you set up system depends on individual plans on use of system. My own best plans change over time so there is not one optimal configuration. You will find many posts and suggestions and most are not wrong. Best to open your own thread, post system, and what you want to use it for. Then you should get several suggestions.

@pc999
Post screen shot of Windows partitioning from Windows if that is all we can see?

---

### Post by pc999 on 2013-01-01
> **oldfred said:**
> 

@pc999
Post screen shot of Windows partitioning from Windows if that is all we can see?

Where is a screen shot, anything else I can do say it.

Thanks.

---

### Post by oldfred on 2013-01-01
Small SSD or Intel SRT which somehow uses RAID. And RAID is not working with Desktop installer. In fact it never did, but you had to use Alternative installer or server installers  with RAID or other normal server type configurations.

I do not have Intel SRT, but several have posted. It does not seem to matter who the vendor is as it is Intel.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> 
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   

> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
    

---

### Post by darkod on 2013-01-02
> **pc999 said:**
> I tried that command and got this

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags



I try to install it after doing that and I still get all the disk as free space although I do have W8 installed and I shrined the W8 partition with W8.

Any idea idea?

BTW I have been looking in the bios and I am not sure if there is a bios mode, in the securo options it allow to other OS, but I do have it in secure W8 UEFI mode right now!

Thanks!

This means the disk had gpt table earlier but you converted it to msdos table using windows. But in this process windows doesn't delete the backup gpt table so linux gets confused because it can see both tables and doesn't know which one is correct. Run fixparts and it will delete the backup gpt table.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

After that the disk partitions will be correctly shown.

You say you are using UEFI with secure mode, but it doesn't sound like that to me. Look at your screenshot, you have 350MB NTFS system reserved partition for the windows boot files.
But UEFI only works with UEFI system partition which should be FAT32 and the first partition on the disk. You have no uefi system partition.

---

### Post by pc999 on 2013-01-02
Thanks!

Just to simplify, if I re-instal everything but format the HDD before as a FAT32 (using gparted) will it work ok then?

---

### Post by darkod on 2013-01-02
> **pc999 said:**
> Thanks!

Just to simplify, if I re-instal everything but format the HDD before as a FAT32 (using gparted) will it work ok then?

This has nothing to do with FAT32 or formatting the hdd. If you use Gparted and create new msdos table, it will probably solve the backup gpt problem because linux tools usually do it properly, unlike windows.

But FAT32 has nothing to do with it, and it's very old filesystem. You would usually use ntfs for the windows system partitions, ntfs for any shared data partition (so that both OSs can read it), and ext4 for the ubuntu partitions.

Fixparts can remove the backup table without affecting the disk content, so you will not need to reinstall anything. Unless you want to...

---

### Post by pc999 on 2013-01-02
Thanks!

I did used fixparts and as been able to install Ubuntu alongside W8 without any problems but...

It goes directly to W8, it doesn't give me the option to go to Ubuntu???

---

### Post by darkod on 2013-01-02
Sounds like grub2 didn't install on the MBR correctly. Run the boot-repair to create the bootinfo and post the link it gives you so that we can see more details. You can run it from live mode.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want to, you can run the recommended repair without waiting for advice, or only create the bootinfo, post the link and wait for an opinion.

---

### Post by pc999 on 2013-01-02
> **darkod said:**
> Sounds like grub2 didn't install on the MBR correctly. Run the boot-repair to create the bootinfo and post the link it gives you so that we can see more details. You can run it from live mode.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want to, you can run the recommended repair without waiting for advice, or only create the bootinfo, post the link and wait for an opinion.


Hi again,

I did  run boot repair, I tried the recomend repair but then it asks me to write some new stuff on the terminal and says that if it open a new windows to say yes to remove grub< I past that in the terminal and get this 

> ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 222 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*


And the boot repair says the grub is still installed!


Anyway I did the boot info and here it is the result

[http://paste.ubuntu.com/1489634/](http://paste.ubuntu.com/1489634/)

Many thanks, again.

---

### Post by darkod on 2013-01-02
Grub2 needs to be completely reinstalled. You can do this from live mode in terminal. I have a bookmarked post from earlier, but in your case you will need to adjust two of the commands, so READ THIS carefully before you start.

In the first block of commands, the first command should be:
```
sudo mount /dev/sda5 /mnt
```

In the second block of commands, the last command should be:
```
grub-install /dev/sda
```

That is the only difference. All the other commands are exactly the same, to the letter. Run them one by one, and reboot without the cd and it should work. The procedure is here:
[http://ubuntuforums.org/showpost.php?p=11858371&postcount=29](http://ubuntuforums.org/showpost.php?p=11858371&postcount=29)

---

### Post by YannBuntu on 2013-01-02
Hello

> **pc999 said:**
> ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common shim-signed linux-signed* 

You need to press the Enter key after writing (or copy/paste) this command. Only then, click the "Next" button.

---

### Post by pc999 on 2013-01-02
> **darkod said:**
> Grub2 needs to be completely reinstalled. You can do this from live mode in terminal. I have a bookmarked post from earlier, but in your case you will need to adjust two of the commands, so READ THIS carefully before you start.

In the first block of commands, the first command should be:
```
sudo mount /dev/sda5 /mnt
```

In the second block of commands, the last command should be:
```
grub-install /dev/sda
```

That is the only difference. All the other commands are exactly the same, to the letter. Run them one by one, and reboot without the cd and it should work. The procedure is here:
[http://ubuntuforums.org/showpost.php?p=11858371&postcount=29](http://ubuntuforums.org/showpost.php?p=11858371&postcount=29)


I tried that but it didnt work out and I do know why see bellow...


> **YannBuntu said:**
> Hello



You need to press the Enter key after writing (or copy/paste) this command. Only then, click the "Next" button.


That did work out :oops:, sorry guys I am a idiot on the linux terminal (I past it and it gave me more stuff so I thought it was done). Probably the reason why the above code didn't work out it is me too. But it seems like everything is fine now :D and I can go to both W8 and Ubuntu!!!



Thank you, to the three of you, you are great and make the world a better place, we need more people like you! Thanks!!!

---


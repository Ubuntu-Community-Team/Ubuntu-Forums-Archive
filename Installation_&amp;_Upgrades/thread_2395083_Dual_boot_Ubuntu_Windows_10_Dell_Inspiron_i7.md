---
title: "Dual boot Ubuntu Windows 10 Dell Inspiron i7"
date: 2018-06-26
forum: Installation &amp; Upgrades
---

### Post by Peet on 2018-06-26
I know there are many posts out there with this exact question, I have been through a great many of them so far today, I do apologise for this, but so far none of the posts have helped me past the critical step of Ubuntu seeing the partitions on my hard drive. 
- I have turned off fast boot,
- I have disabled hibernation,
- I have shrunk my Windows partition and have free, un allocated space on the drive,
- My hard drive is AHCI,
- I have updated my BIOS,
- I have disabled secure boot,
- I have disabled legacy ROM boot in BIOS
- BIOS is booting in UEFI
- I do shut down windows, not restart.
- I may have missed some steps that I have taken since this morning - I really tried not to post my problem, but solve it myself.

I can boot from the DVD without problems, if I run Ubuntu Studio 18.04 live I can mount my windows drives, see and navigate the files.  If I try to install, or just run Gparted it can see SDA, but says it is unalocated, no partitions created yet.

Any help would be greatly appreciated, I have now spent about 5Hrs on this today, without having a resolution.
Thank you,
Regards,
Peet.

---

### Post by oldfred on 2018-06-26
It seems like you have done everything, but a few things to double check.

Windows fast start up is hibernation, but settings may be different.
Also in rebooting Windows if it does an update, it may turn fast start up back on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also is drive a SSD? Many Dell have needed firmware update.

What model Dell?
But issues are often common across many similar models. Bigger difference if Intel based or AMD based.

        
 Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en
      [/URL]
 Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488) 
    [URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]
[/URL]

---

### Post by Peet on 2018-06-26
Hi Oldfred,
Thank you for the reply, I will look at all the threads you posted, but the one thing I notices that I can mount and use the Windows file system from within a live DVD boot, but then the disk manager cannot see the partitions - Have I got the Windows settings wrong problem, or something else?

---

### Post by Peet on 2018-06-26
OK, I have now confirmed that I have done everything indicated on the links you posted where applicable, some of which from the links you posted.
This is not a SDD, but I did update the BIOS and drivers earlier today.
I have a Dell Inspiron 15, i7, Intel core, NVIDIA Graphics.  I am happy to post all technical specks if that may help me move to a successful install.
My main concern remains that I can access all my Windows files from a live boot, but not recognise the partitions.  I feel there is something small missing in my config, not the Windows settings problems.

---

### Post by oldfred on 2018-06-26
If Windows is hibernated, it often may be mounted read only in your install.
But the installer wants full access, even though not writing to the NTFS partition and does not seem to work.

Since nVidia are you using nomodeset? But that is not related to partitions missing issues.

There are a lot of other reasons installer does not see partitions.
Some:
Drive was converted from Basic to dynamic in Windows. Linux now will see dynamic but not work with it. It used to not even see anything before.
Drive was converted from gpt to MBR using Windows which does it incorrectly.

       Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html) 
    
       Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642) 
    [https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

Post these:
sudo parted -l
sudo fdisk -lu
sudo gparted -l /dev/sda

they should essentially be the same, but some give slightly different info.

---

### Post by Peet on 2018-06-27
I have checked - the system mounts the Windows drives as RW, not read only (I created a folder successfully).

I will look in to the rodsbooks link and try his advice to fix this.

I did sudo su, hence not using sudo per command.

> root@ubuntu-studio:/home/ubuntu-studio# parted -l
Error: Can't have the end before the start! (start sector=1934356480 length=0)
Model: ATA ST1000LM024 HN-M (scsi)                                        
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: MATSHITA DVD+-RW UJ8E2 (scsi)                                      
Disk /dev/sr0: 3031MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      2994MB  2996MB  2392kB               EFI


> root@ubuntu-studio:/home/ubuntu-studio# fdisk -lu
Disk /dev/loop0: 2.8 GiB, 2943705088 bytes, 5749424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4AF91851-F031-4025-8052-D8FFA315B1A5

Device          Start        End   Sectors   Size Type
/dev/sda1        2048    1026047   1024000   500M EFI System
/dev/sda2     1026048    1107967     81920    40M unknown
/dev/sda3     1107968    1370111    262144   128M Microsoft reserved
/dev/sda4     1370112    2906111   1536000   750M Windows recovery environment
/dev/sda5     2906112  967609088 964702977   460G Microsoft basic data
/dev/sda6   967610368  969320447   1710080   835M Windows recovery environment
/dev/sda7   969320448 1788520447 819200000 390.6G Microsoft basic data
/dev/sda8  1934356480 1953523119  19166640   9.1G Windows recovery environment
/dev/sda9  1934356480 1934356480         0     0B Windows recovery environment


> ======================
libparted : 3.2
======================
Could not stat device -l - No such file or directory.
Can't have the end before the start! (start sector=1934356480 length=0)


---

### Post by Peet on 2018-06-27
Not sure if this helps, but trying to run fixparts I got the following:

> root@ubuntu-studio:/home/ubuntu-studio# fixparts /dev/sda
FixParts 1.0.3

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!


---

### Post by oldfred on 2018-06-27
Parted has real issues with your drive:
 Partition Table: unknown 
Fdisk sees it as gpt.
Did you run gdisk, it may have told more.

but you cannot have this with gpt, partitions overlap:
      
 /dev/sda8 [COLOR=#ff0000]1934356480[/COLOR] 1953523119 19166640 9.1G Windows recovery environment
/dev/sda9 [COLOR=#ff0000]1934356480[/COLOR] 1934356480 0 0B Windows recovery environment  

 First backup partition table, use your drive for sdX or sda, sdb etc. Save to another device.
sudo sfdisk -d /dev/sdX >parts_ sdX.txt
sudo sfdisk -d /dev/sda > parts_sda.txt 

 repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
      [/URL]
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. 
In your case you may have to delete sda9? 
    [URL="http://www.rodsbooks.com/gdisk/repairing.html"]
[/URL]

---

### Post by Peet on 2018-06-28
Thank you Oldfred!
I fixed it I think!
I can now see my partitions and install Ubuntu.  The fact that it does not recognize my WiFi is currently very secondary, though might have to pop up later - here's hoping not.
I truly appreciate your help.
BTW I cannot see how to mark this thread as solved, or a way to give you credit with the forum tools.
Thank you!
Peet.

---

### Post by oldfred on 2018-06-28
See last line in my signature for quick instructions.

Details:
       Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Some Dells seem to have Internet issues.
If you do have Wifi issues post in the correct sub-forum on Wireless and follow instructions in sticky thread to run script & post details of your configuration. Some of the users there are very knowledgeable on wireless issues.

---


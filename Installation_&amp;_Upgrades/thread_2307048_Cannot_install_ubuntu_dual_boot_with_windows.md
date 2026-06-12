---
title: "Cannot install ubuntu dual boot with windows"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by antiriad7 on 2015-12-21
Hi,
I wanted to install dual boot Ubuntu 14.04.3 with Windows 10 Pro. I made a pen drive USB Bootable stick. Booted it, everything was going well, when I got to one problem: I had 2 partitions, one with 350 GB and another with 100 GB. I don't know why, but it automatically selected the smaller one, with 30 GB files on it, and asked me to shrink it. I shrinked  it, everything was going well, but, finally I got a single 450 GB partition, type - lvm. I cannot boot windows too. So I cannot boot without my live USB stick. I have also a Windows 7 installation disk, booted it, and tried to install on the partition, but it couldn't do it, cause the partition was GPT type. I googled it and found some ways to change type, but it required formatting. I cannot access the partition, but I want some files kept. Maybe it's BIOS problem, - UEFI or Legacy type... If I use UEFI, Disk reader and HDD aren't detected. So I cannot boot HDD...
Please help!

---

### Post by yancek on 2015-12-21
Your life would have less problematic had you read the link below which explains dual booting windows and Ubuntu in UEFI.  Note at the beginning that if you are dual-booting, both systems must be UEFI or both must be MBR. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Although the partition manager used in Ubuntu can resize partitions, when you are resizing a windows partition, you should always use windows tools.  Windows 10 it is Disk Management.  After doing that you should reboot windows and run chkdsk at least once.

You selected to use LVM installation type which is definitely not the default type.   An LVM install overwrites everything and I don't think that is clearly explained in the installer.  Stop using the drive.

My understanding is that with windows, if you are using GPT you must also use UEFI which you apparently were not doing.  If you can still boot the Ubuntu install flash drive, go to the site below and get the boot repair software and run it and post the output or a link to it here and someone familiar with UEFI should be able to give you some suggestions on possible solutions.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have problems/questions in the future, post a question before beginning some actions.  Saves a lot of headaches for you.

---

### Post by antiriad7 on 2015-12-22
OK. I have never used GPT. I always used legacy boot. Why did the partition become GPT? I only want to get some data from it. I downloaded boot repair. It has 2 options Recommended Repair, or Create a BootInfo summary. I tried bootinfo summary. It gave me this URL: [http://paste.Ubuntu.com/14136275/](http://paste.Ubuntu.com/14136275/)
What does "stop using drive" means? No chances?
I even don't want my PC to boot, I only want data! Please, help!

---

### Post by Bucky Ball on 2015-12-22
Welcome. If you only want to retrieve data, boot from the Ubuntu USB, 'Try Ubuntu', save the data to an external device.

If you can't boot without the USB, boot from the Win disk and do a Win repair. The option is there as far as I've read (or is it Win recovery disk?). Once Win is working you can try again with the knowledge of experience and a bit more research. 

You are going to need free space to install Ubuntu, no partition. That will happen during install.

---

### Post by antiriad7 on 2015-12-22
I was using Win 10 Pro, but I don't have a disk of it... I downloaded it... Here's a pic:
[http://oi63.tinypic.com/10gz81w.jpg](http://oi63.tinypic.com/10gz81w.jpg)
I want files from the sda3... It was not partitioned before starting ubuntu install... (It isn't installed, it's just live USB). It became partitioned... Help

---

### Post by oldfred on 2015-12-22
You either choose LVM or LVM with encryption as drive does not have anything but Ubuntu.

The LVM install is an advanced logical partitioning over the physical partitions. And that is always a full drive install using the selection in the installer. LVM is always a full drive as its advantage is the logical partitions which are easier to change. But if you want other partitions then it does not offer much.

You cannot restore a working system. But because Ubuntu is not large, and it also writes data to random locations on drive, and Windows typically writes data at beginning of drive, not all data is lost.

If lucky testdisk can find older partitions and deeper search finds files. If not you have to use tools like photorec (part of testdisk) to scan drive for anything that looks like a file. Some say that for NTFS, Windows tools may be better.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS
      [/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

    [       ]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS")
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

    [URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by antiriad7 on 2015-12-22
I installed TestDisk, analysed the drive, and here's the result: 
[http://tinypic.com/r/208y1sg/9](http://tinypic.com/r/208y1sg/9)
then tapped Enter:
[http://tinypic.com/r/11j172p/9](http://tinypic.com/r/11j172p/9)
No what should I do?
Sorry for a stupid question... I am just a tech beginner. And this is first time I posted in a forum...
I don't know how to use TestDisk.
EDIT: If TestDisk can find that partitions, why is Ubuntu installer forced to act stupid and hide them?
EDIT2: May use thing like TeamViewer to help?! I am not English, so it is one more difficulity for me...

---

### Post by oldfred on 2015-12-22
Did you try p for list files on second screenshot?
It may take a while, but is best case at possible recovery of files.

---

### Post by antiriad7 on 2015-12-23
I'll give it a try

---

### Post by antiriad7 on 2015-12-23
> **oldfred said:**
> Did you try p for list files on second screenshot?
It may take a while, but is best case at possible recovery of files.

Thank you! TestDisk recovered my photos! But...
I accessed only second partition. I copied photos, but they're damaged. Some of them are OK, but some are damaged. 0.00B photos? and cannot see em'. Almost 2/3 downloaded to my phone. Then I tried second time, now all photos were 0.00B. Now I have two questions:
1.Why I cannot access the first partition (~350GB)?
2.How can I copy photos from smaller partition without any damage? (If it copied some photos correctly, but second time not, it's not problem of damaged files on partition).
Almost solved...

---

### Post by antiriad7 on 2015-12-23
TestDisk was a solution. I know why photos were damaged. It's problem of space. Now I copy a photo folder to my Pictures, than to my phone, but I cannot delete it from Pictures, so I restart every time I copy a folder. If it will be done correctly, I will mark this thread as Solved!
But I have two questions:
1. Why I cannot access my bigger partition?
2. What did cause the problem?

---

### Post by Bucky Ball on 2015-12-23
> **antiriad7 said:**
> 2. What did cause the problem?

Probably this bit:

> **antiriad7 said:**
> I had 2 partitions, one with 350 GB and another with 100 GB. I don't know why, but it automatically selected the smaller one, with 30 GB files on it, and asked me to shrink it. I shrinked  it.

You shrunk it when you weren't sure what the consequences would be. You were unsure of the process during install. We live and learn. :)

I always encourage new users to make a solid plan with a pen and paper prior to going anywhere near the digital and the process where things can go horribly wrong without one. Perhaps put it down to experience.

With Win installed, the general, and safest procedure, is to choose 'Something Else' at the partitioning section of the Ubuntu install and create the partitions in free space manually, making sure not to go anywhere near the Win partitions or format or resize any of them. 

Another tip, just for the heck of it, not that you've done this, but for future reference: Always resize the Win OS partition with Win disk management tools or Win specific software, NOT Gparted in Ubuntu or during Ubuntu install. And vice versa. Always resize the Ubuntu partitions (EXT*) with Linux tools. Win can't do anything useful with EXT* partitions. 

Good luck and glad you're having some success. Mark as solved when you have things safely tucked away. This will not close the thread to further discussion, just helps others. Thanks (see first link in my signature).

---

### Post by antiriad7 on 2015-12-23
And... How can I find my Lenovo android phone in TestDisk? (Some folders don't fit in pc availible memory)

---

### Post by Image on 2015-12-23
Connect an external drive and copy them to that?

---

### Post by antiriad7 on 2015-12-24
Ummm... Why does TestDisk copy 0.00B photos and videos? I cannot copy em'!

---

### Post by antiriad7 on 2015-12-24
When I try to copy them, some are OK, some are 0.00B, but some aren't present at all... USB Flash is OK, but when I try to create a folder, see image: [IMG]http://i66.tinypic.com/wl1tmx.png[/IMG]but the flash has more than 6 GB left! Please help...

---

### Post by Bucky Ball on 2015-12-24
Perhaps, but how much are you looking to put on it? If more than 6Gb, it won't start the operation. 

As far as I'm aware, testdisk retrieves partitions, not individual files, so perhaps you are attempting to retrieve the whole partition.

---

### Post by antiriad7 on 2015-12-26
...
OK,
Done it! Thank you all for support!!!

---


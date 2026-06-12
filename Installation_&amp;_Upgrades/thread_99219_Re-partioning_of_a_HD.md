---
title: "Re-partioning of a HD"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by eskild on 2005-12-05
Everything worked well after a Ubuntu Linux 5.10 amd64-installation. But I wanted to be able to switch to Windows XP, too. Therefore I had to uninstall Linux first. I used the Linux-CD-ROM, but unfortunately - just after the beginning of formatting the harddisk - I clicked the restart-tast. And now it is impossible for me to get in contact with the HD.
The deleverer's support tells me, that I have to re-partion the HD, but not how to do it in Linux.
How can I do this?
eskild (DK)

---

### Post by bwog on 2005-12-05
[QUOTE=eskild] Everything worked well after a Ubuntu Linux 5.10 amd64-installation. But I wanted to be able to switch to Windows XP, too. Therefore I had to uninstall Linux first. [/QUOTE]

That is not correct, you dont have to uninstall linux to get into XP.


[QUOTE=eskild] I used the Linux-CD-ROM, but unfortunately - just after the beginning of formatting the harddisk - I clicked the restart-tast. And now it is impossible for me to get in contact with the HD.
The deleverer's support tells me, that I have to re-partion the HD, but not how to do it in Linux.
How can I do this?
eskild (DK)[/QUOTE]

I am not convinced yet that you have to format the disk. You say that you cannot get in contact with the hd. Can you tell us more about what you try to do, where you get stuck, and what you see on screen when you get stuck?

---

### Post by Herman on 2005-12-05
Hello, eskild, I think you mean you had Ubuntu installed on your hard-disk and you wanted to add Windows XP and make it 'dual boot'. Is that correct? So you used the Linux partitioner to delete the partition, and began to format it, but accidentally hit the restart button on your computer? Or restart test? (I'm not sure what you mean by that)?
Anyways, as long as your computer's BIOS can see your hard drive you should be able to just run the Windows XP install CD and it should reformat your hard drive for you and install Windows XP on the whole entire drive. You do not have to worry about this as the Ubuntu partitioner will be able to take some of the hard-drive back using Ubuntu's own partitioner that is in the Ubuntu install CD.
So don't worry, just try installing Windows XP first and see if that goes in okay. If it does, then you can install Ubuntu after that. There are two examples of how I do that in my signature link below this post. One is for if you have Windows XP (or any other Windows) has a FAT32 file system like I have, (that's the simplest), and the other is for when Windows XP has an NTFS file system. By reading that you should be able to see how to use the Ubuntu partitioner to create a new partition for Ubuntu, and will then install itself like you had before.
Is this what you wanted to know?

---

### Post by eskild on 2005-12-05
Thank you, bwog and Herman.
I will add a little more information:
First - it is a quite new PC with an AMD64 processor and a Hitachi SATA 160GB HD, Deskstar T7K250.

Curious to se, what a 64 bit PC could do, I installed Ubuntu Linux Linux 5.10 amd64.
Fine, except some trouble to run existing Windows applications. I therefore read about "dual boot", and there that the best choice should be to install Win XP first.
However, I could not make Win XP format properly, why I inserted the Linux-CD-ROM again to format the HD by Linux without installing anything. And here - at the start of this proces - it was, that I clicked the restart buttom. 
After this incident I have not been able to get in touch wit the C-drive (the HD).
Well, I have since that tried several times to install Win XP as well as Linux. And it works to some extent.
Winn XP formats the 131 GB, it seemingly can find. (I wonder, where the resting 29 GB have gone. The install-files are copied, but when the installing proces should start, I get the following message (tranlated from Danish): Installation of more than one opetative-system in one partition is not recommended." If I try anyway, it starts from the beginning again.

Linux finds 161 GB and suggests 2 partitions:  partition 1 - ext3 and partition 5 - swap. After some working-time I am told to remove the CD-ROM. After a restart I after some search get the message: "Disk boot failure. Insert system disk and press Enter". That was not the idea; but when I do so, is the RAM-drive the only C-drive to be found.  When I instead click Enter: setup atp -  CLIENT MAC ADDR: and a lot of numbers - followed by GUID: and a lot of F's. Then PXE-M0F: Exiting NVIDIA Boot Agernt. And finally: PXE-E53: No bootname received.

The PC-producer's support tells me not to worry, that I just must have repartioned my HD, but he could not tell me how.   Well, I think, I have allready tried to do so. 

I hope you or somebody else in this group can give me some good advice.

---

### Post by az on 2005-12-05
The Windows XP installer is not good at working with a non-pristine partition table.  You can boot the ubuntu installer and let it detect your hardware.  Drop to the shell (CTRL-ALT-F2) and run fdisk.  Tell fdisk to create a blank partition table and quit.

Boot the windows installer and it should see the whole disk.

Then install Ubuntu after windows is installed and it will automagically shrink the windows partitoin for you.  It will ask how big you want it.

---

### Post by eskild on 2005-12-06
Thank you, "azz", for this simple and easy option.

I have reached fdisk and the list of commands. But I can't find a command, which allows me to "Tell fdisk to create a blank partition table ".
How can I do that?

---

### Post by poptones on 2005-12-06
Simple way to clean up the blank partition table is to write zeroes to it.

dd if=/dev/zero of=/dev/hda

Let it run a few seconds and your partition table will be history. Windows will then be able to start from scratch.

---

### Post by az on 2005-12-06
[QUOTE=eskild]Thank you, "azz", for this simple and easy option.

I have reached fdisk and the list of commands. But I can't find a command, which allows me to "Tell fdisk to create a blank partition table ".
How can I do that?[/QUOTE]

fdisk /dev/hda

the option is o


The above suggestion should work, too.


Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): q

---

### Post by eskild on 2005-12-06
Thank you for your patience, "azz". I'm afraid, I need a little more of that.
Let me write exactly, what I have done - and what I see on the screen:

fdisk /dev/sda
"The number of cylinders for this disk is set to 20023. There is nothing wrong with that, but it is langer than 1024, and could in certain setups cause problems with 
1. Software ......
2. booting and partioning software from other OSs"

Ok - I click "m" 
and get a list of options.

Then "o"
I get the above message but added with
"Warning: invalid flag 0x0000 of partition table 4."

I click "w"
"Calling ioctl() to re-read partition-table"
and
"Syncing disks"

So far I start the Win XP installation disk. But still, there is only 131 GB available out of 160. 
The proces runs as usual, but ends up in the same frustrating driving in a circle. I still can't make a proper Win XP installation.

Whar do I do wrong?

---

### Post by az on 2005-12-06
[QUOTE=eskild]
"Calling ioctl() to re-read partition-table"
and
"Syncing disks"


Whar do I do wrong?[/QUOTE]


It sounds like a hardware problem.

---

### Post by eskild on 2005-12-08
Once again, thank you for the assistance, you have offered me.
My problem is solved. Shortly about how:
SATA-drives require configuration of RAID, if you want to install Win XP. After that you will have to copy some files from the delievered CD-ROM to a floppy. That has to be used in the installation proces.
Apparently finds LINUX without any trouble these files, or they are not necessary at all. Anyway there were no suchs problems during the LINUX-installation.
It must therefore have been the switch from LINUX- to Windows-installation, that createt my trouble

---

### Post by bwog on 2005-12-08
[QUOTE=eskild]Once again, thank you for the assistance, you have offered me.
My problem is solved. Shortly about how:
SATA-drives require configuration of RAID, if you want to install Win XP. After that you will have to copy some files from the delievered CD-ROM to a floppy. That has to be used in the installation proces.
Apparently finds LINUX without any trouble these files, or they are not necessary at all. Anyway there were no suchs problems during the LINUX-installation.
It must therefore have been the switch from LINUX- to Windows-installation, that createt my trouble[/QUOTE]

I suppose you mean that linux did not need the sata drivers for windows that you put on floppy in order to install windows.

I understand that. Could you tell more about solving your problem with linux, is it just that you removed that floppy?

---


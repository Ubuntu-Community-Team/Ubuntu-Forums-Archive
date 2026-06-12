---
title: "Recover MBR"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by MrGrieves on 2007-12-15
I don't usually resort to posting something unless I'm really stumped.  I've spent too much time troubleshooting this seemingly simple problem already.

Here was my setup before the problem occurred

Disk 1: 120GB running Ubuntu Edgy with Grub
Disk 2: 500GB running Fedora 8

I then installed Debian 4 on Disk 1 ("use full disk" option).  After playing around with it for a while, I decided to go back to Ubuntu.  I thus installed gutsy using the "Use full disk" option and asked it to install the boot loader.

Result:  On boot, Grub Error 15.

After reading on forums about this error, I attempted to solve it by reinstalling Grub.  This I did from my Fedora system.  

Result:  No booting.  The system would simply idle after doing hardware checks.

I tried reinstalling Ubuntu with the boot loader option.  No change.  I tried reinstalling Ubuntu without the boot loader.  No change.

After reading some more and growing irritated,  I downloaded Ultimate Boot CD and tried to fix my MBR (whatever that may mean), using TestDisk.

Result:  After hardware checks, the system shows me a 1234F: prompt.  Pressing enter just adds another line.


A.  Where can I find very explicative information about the system boot sequence ?  E.g. bootstrapping, the MBR, the /boot partition, kernel startup, things of the sort.  All the information I can find is incomplete or lacks details.  I'd like to understand overall what's going on.

B.  What do I have to do to my first hard disk to get Gutsy running on it?  Grub would be nice.  I intend to remove Fedora and put Windows in it's place.

Thank you kindly.

Mark

---

### Post by Pumalite on 2007-12-15
Super Grub could help fix your MBR, but if you have messed up things, then, better start from scratch. Windows first, Ubuntu last.

---

### Post by MrGrieves on 2007-12-15
But installing Windows on my second disk won't fix the MBR of my first disk will it?

---

### Post by Pumalite on 2007-12-15
Don't think so.

---

### Post by njparton on 2007-12-15
There are freeware MBR recovery tools out there.  Google for them. You usually have to burn them to a CD and boot from it.

---

### Post by MrGrieves on 2007-12-15
Yeah, I've tried a few that are on the Ultimate Boot CD to no avail.  I've burnt the Super Grub CD but I'm not exactly what it is I'm trying to do.

What does it mean to "Recover the MBR"?   Does an MBR for Windows look exactly the same as an MBR for Linux?  What does that mean?

Mark

---

### Post by Pumalite on 2007-12-15
You recover your Master Boot Record.

---

### Post by MrGrieves on 2007-12-15
What I mean is more:  How does the MBR point to the Linux kernel and how does it point the Windows kernel.  How could these operations be identical?

The BIOS passed the cpu to the code found in the MBR, no?  Then, the MBR passes the cpu to the kernel.  Yes?

---

### Post by helix_r on 2007-12-15
I am not sure exactly what your specific problem is but in the past whenever I've messed up my MBR, I used the command "fdisk /mbr" to format it.

You can download an bootable CD image of [freedos]("http://www.freedos.org/"), making sure that it has fdisk and try it. Note that "fdisk /mbr" it will wipe the master boot record on the disk that you apply it to. As far as I know, the freedos fdisk app does the same things as the [old MS DOS app]("http://support.microsoft.com/kb/69013").

---

### Post by Herman on 2007-12-15
> What does it mean to "Recover the MBR"? Does an MBR for Windows look exactly the same as an MBR for Linux? What does that mean?Hello MrGrieves,
The MBR is in the first sector of every formatted hard disk.
There are three main parts in the MBR. plus a few other minor bits and peices. The main areas of the MBR are:
the boot loader code area, (for the stage1 of any boot loader), 446 bytes
the partition table for the hard disk, 64 bytes
the 55aa bootable disk signature, 2 bytes.
446+64+2=512 bytes 
512 bytes= 1 sector.

When most people talk about 'fixing' their MBR, they mean just the bootloader part of it. It is quite safe and acceptable to install the stage1 code from a boot loader in any operating system or partition to the MBR. This will make the MBR 'point to' the chosen boot loader in the chosen partition.
If you 'install GRUB to MBR', you are really just installing this 'stage1 code there as a 'pointer' to the GRUB files in the Ubuntu partition.

When you run 'FIXMBR', from a Windows XP recovery console, that will over-write your 'stage1' code for GRUB and replace it with the 'stage1' code for Windows, and make your MBR 'point to' Window's boot sector, and from there the boot will be directed to Windows boot-up files, (NTLDR if it's XP).
The command 'fdisk /mbr' will also work, you can use that command from a Windows 98 boot floppy disk, it's a Windows 98 command really, but it will restore the MBR well enough to boot XP if you can't get a Windows XP Recovery Console for any reason.

Then when you 're-install GRUB, you will be overwriting the Windows 'stage1' code in the bootloader area of your MBR with the 'stage1 for GRUB once again. That will cause the MBR to 'point to' GRUB's stage2 files in your Ubuntu file system, which will open your /boot/grub/menu.lst file to give you a GRUB menu, from where you can choose to boot either Windows or Ubuntu.

Although boot loaders can write to certain parts of the partition table too, minor changes such as to 'hide' or 'unhide' a partition, or mark a partition as 'active' (set the boot flag), generally any major or important changes to the partition table are left to specialized partition editing programs.

If you have a problem with the partition table part of the MBR, that's when you might want to use a program like TestDisk to come to your rescue.
Most of the time, it isn't necessary to use TestDisk for your regular everyday routine MBR tasks.
The main specialty of TestDisk is the ability to scan your hard drive for the start blocks of file systems and rebuild your partition table from traces of lost or deleted partitions and recover your old operating systems and data after a disaster of some kind. TestDisk is an excellent program, I recommend it, but it should not be needed for everyday use. :)

---

### Post by Herman on 2007-12-15
> What I mean is more: How does the MBR point to the Linux kernel and how does it point the Windows kernel. How could these operations be identical? It the bootloader code area of the MBR is empty, but a partition is marked as 'active' in the partition table, (the boot flag is set in that partition), then the BIOS will go to the boot sector of that partition and if there is boot loader code there then the boot loader for that operating system will start up.

In the case of Linux, the boot sector (the first sector of the partition), is empty by default, but it is easy to install a bootloader to the Linux partition.
 
In the case of Windows, the boot sector has bootloader code in it by default, so it points to the appropriate bootloader files in the Windows file system to load the Windows kernel into the computer's memory and run whatever other files and programs are necessary for Windows to boot up.

When Windows 'stage 1' code is in the bootloader area or the MBR it still makes the MBR 'point to' Windows boot sector, and the Windows partition must still be marked 'active', or Windows won't boot,  The Windows boot sector points to the appropriate bootloader files in the Windows file system to load the Windows kernel into the computer's memory and run whatever other files and programs are necessary for Windows to boot up.

When GRUB is installed in the MBR, it writes its 'stage1' code there, overwriting whatever was there previously, and GRUB also installs the optional 'Stage1_5' to the next fifteen sectors of the otherwise empty first track of the hard disk. GRUB's 'stage1_5' 'understands file systems', so GRUB is able to help the stage1 to find GRUB's stage2 file.
GRUB's stage2 file finds /boot/grub/menu.lst and presents you with your GRUB menu.
If you select Windows then GRUB  it points to Windows, makes sure the Windows partition is active, (sets the boot flag) with its 'makeactive' command ,and chainloads Windows by it's boot sector, (hands over control to whatever bootloader is represented there in that boot sector, be it for Windows 98, XP or Vista's new boot loader, and Windows boots.

If you select Ubuntu from your GRUB menu, then GRUB will point  to the Ubuntu partition and directly load the specified Linux kernel into the computer's memory and run whatever other files and programs as are needed to boot Ubuntu, (initrd.img). Ubuntu will boot.

Regards, Herman :)

---

### Post by Herman on 2007-12-15
> I then installed Debian 4 on Disk 1 ("use full disk" option). After playing around with it for a while, I decided to go back to Ubuntu. I thus installed gutsy using the "Use full disk" option and asked it to install the boot loader.

Result:  On boot, Grub Error 15.

After reading on forums about this error, I attempted to solve it by reinstalling Grub.  This I did from my Fedora system.  

Result:  No booting.  The system would simply idle after doing hardware checks.
Here's my link about your original GRUB error: [     Grub error 15]("http://users.bigpond.net.au/hermanzone/p15.htm#15"). That would be a good place to start thinking about what might be wrong and what to do about it.

---

### Post by psusi on 2007-12-15
> **Herman said:**
> It the bootloader code area of the MBR is empty, but a partition is marked as 'active' in the partition table, (the boot flag is set in that partition), then the BIOS will go to the boot sector of that partition and if there is boot loader code there then the boot loader for that operating system will start up.

The boot area of the MBR is never empty.  It is the boot code installed there by msdos/windows that looks for an active partition and tries execute the boot sector there.  The bios only loads and executes the mbr, and that is all.  It knows nothing about partitions.

As for the original problem, it is most likely caused because the bios and the kernel see your drives in different orders.  Post the output of sudo fdisk -l and indicate which of the two disks your bios is set to boot from.

If the bios is set to boot from a different disk than the one linux sees first, you will have to either change the bios boot order, or manually install grub, telling it the correct order.

---

### Post by Herman on 2007-12-15
> After reading some more and growing irritated, I downloaded Ultimate Boot CD and tried to fix my MBR (whatever that may mean), using TestDisk.

Result:  After hardware checks, the system shows me a 1234F: prompt.  Pressing enter just adds another line.
If you read the documentation for TestDisk you'll find the explanation for that. Here is the link, [http://www.cgsecurity.org/wiki/Menu_MBRCode](http://www.cgsecurity.org/wiki/Menu_MBRCode)

You should use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to re-install GRUB to the MBR of your first hard disk.

---

### Post by froy02 on 2007-12-15
Here's the website for  simpliest way to install grub:
 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

In your case you might come up with 2 stage1 and you mayl have to edit the /boot/grub/menu.lst.  It really is a simple solution.

---

### Post by MrGrieves on 2007-12-15
I used Super Grub Disk.

Booting off sda now goes into Grub and allows me to boot into Fedora (on sdb).

Booting off sba also goes into Grub and contains 2 entries for Fedora that don't work.

Setting BIOS to boot on disk 2 (sdb), boots up Fedora.
[SIZE="1"][FONT="Courier New"]
[root@jalapeno sbin]# ./fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0b98

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3988    32033578+  83  Linux
/dev/sda2            3989        4113     1004062+  82  Linux swap / Solaris
/dev/sda3            4114       14204    81055957+  83  Linux


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c39a6


   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        5099    40957686    5  Extended
/dev/sdb2            5100       24732   157702072+  83  Linux
/dev/sdb3           24733       44364   157694040   83  Linux
/dev/sdb4           44365       50993    53247442+  83  Linux
/dev/sdb5   *           1         191     1534144+  83  Linux
/dev/sdb6             192        1976    14337981   83  Linux
/dev/sdb7            1977        2613     5116671   83  Linux
/dev/sdb8            2614        3059     3582463+  83  Linux
/dev/sdb9            3060        3314     2048256   83  Linux
/dev/sdb10           3315        3951     5116671   83  Linux
/dev/sdb11           3952        4588     5116671   83  Linux
/dev/sdb12           4589        5098     4096543+  83  Linux

[/FONT][/SIZE]

---

### Post by MrGrieves on 2007-12-15
When I mount my new Gutsy root partition (for which I'm certain that I chose the option to install boot loader), there's no grub folder inside of /boot.

---

### Post by Herman on 2007-12-15
AHA! 
That is rare, but it can happen.

You should use Super Grub Disk to boot into Ubuntu by booting the kernel directly, (bypass the menu.lst file, since you don't have one at all).
'English Super Grub Disk'--> 'Gnu/Linux'-->'Boot Gnu/Linux Directly'-->'Boot Gnu/Linux Directly'--'SCSI'-->'Ubuntu 7.10'-->'Ubuntu 7.10'-->'Ubuntu 7.10'

Then once Ubuntu has booted, you can open a terminal and make your self an empty /boot/grub durectory,
```
sudo mkdir /boot/grub
```Then run grub-install to re-install GRUIB to MBR in your first hard disk and simultaneously generate GRUB files in /boot/grub from within your Ubuntu operating system.
```
sudo grub-install /dev/sda
```Then run 'sudo update-grub' to have a generic menu.lst file made for you, 
```
sudo update-grub
```Then you just need to edit your generic menu.lst file to make it suit your computer and customize & personalize it.

Regards, Herman :)

---

### Post by MrGrieves on 2007-12-15
When I boot my gutsy / partition from the Super Grub CD, I get
Error 13: Invalid or unsupported executable format

---

### Post by Herman on 2007-12-16
Oh.

Can you boot the Ubuntu CD that you used to install with and when you get to the black screen where it has 'Start or Install Ubuntu', select 'Check CD for defects'. [IMG]http://img255.imageshack.us/my.php?image=feistysingle01fb0.png[/IMG][IMG]http://img255.imageshack.us/my.php?image=feistysingle01fb0.png[/IMG]
Maybe you installed from a corrupted CD or the CD was made from an .iso file that was corrupt. [                  Why integrity check your downloaded .iso?]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Why_integrity_check_your_downloaded_.iso")
                       It seems to me as if something there is corrupt anyway, I'm not sure exactly what.

---

### Post by MrGrieves on 2007-12-16
[FONT="Courier New"]Check finished.  No errors Found[/FONT]

I think I might download and install Feisty all the same.

---

### Post by Herman on 2007-12-16
You had Edgy running okay and then Debian on this hard disk before you installed Gutsy and ran into problems.
It should be okay to install Fiesty Fawn there and see if it works any better.

For some reason re-installing Gutsy hasn't seemed to have helped so far. :confused:
I was about to suggest a file system check.

Yes, it would be worth a try to see if Fiesty will install and boot okay. That would be a good test.

There must be some logical reason for these problems though, it would be nice to be able to identify the real cause of all this and solve it properly. I imagine you would like to hurry up and get on with whatever work or hobby you use Ubuntu in your computer for though. 

By the way, when you used Super Grub Disk to try to boot Ubuntu with, did you use the 'Direct Kernel Boot' method? I was presuming you did because the other way would have tried to bring up your GRUB menu, which you don't have if you have no grub folder in /boot.
Now I am wondering if you tried to boot by the partition (boot sector) instead, (like your post may be implying), which by default has no bootloader code installed in most Linux distros, including Ubuntu, (you can do that yourself though). If you tried that it might be why you got [Grub error 13]("http://users.bigpond.net.au/hermanzone/p15.htm#13").
Try a 'Direct Boot' with Super Grub Disk maybe and see what happens.

There are basically three main ways to boot Linux, by the menu.lst file (configfile command), by the boot sector, (chainloader comamnd, but you need to install booloader code there yourself first), and by the direct kernel boot method, (kernel and initrd commands).
The 'Direct Boot' method with Super Grub Disk is the surest, because it bypasses all the places where you could have some kind of configuration  problem.

If Fiesty Fawn will install and work okay, and you're happy with it, then good.
If you have the same problems all over again, think about any hardware changes you may have made recently (especially to do with adding/removing disks or plugging/jumpering or BIOS settings).

---

### Post by MrGrieves on 2007-12-17
The **direct boot** of Linux for my root partition on sda (sda1) results in

[FONT="Courier New"]Error 15:  File not found.
[/FONT]
The line before that reads

[FONT="Courier New"]selectfile /boot/initrd.img /initrd.img
[/FONT]

If I try the **boot partition** option and boot my sda1 partition, I get

[FONT="Courier New"]Error 13:  Invalid or unsupported executable format[/FONT]


Of course, if I boot MBR, I get my Grub menu that points to Fedora grub files.


From fedora, if I mount sda1, there doesn't seem to be a proper initrd file in /boot.  These are the contents of /boot:
[SIZE="2"][FONT="Courier New"]
[root@jalapeno boot]# ls -l
total 10124
-rw-r--r-- 1 root root  424317 2007-10-14 21:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-14 21:39 config-2.6.22-14-generic
drwxr-xr-x 3 root root    4096 2007-12-16 10:50 grub
-rw-r--r-- 1 root root 7124250 2007-10-15 19:26 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2007-10-14 21:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1764280 2007-10-14 21:39 vmlinuz-2.6.22-14-generic
[/FONT][/SIZE]


Note that the grub folder comes from my attempts to manually fix grub.  If I use the simple **Boot Linux** option on Super Grub CD, I get a grub menu that contains the entries from this grub installation's menu.lst.   Thus, my conclusion is that my MBR is fine and that my Linux installation is corrupt.



I'll wait for your reply before going ahead with installing Feisty.  I'd also like to get to the bottom of this.  All this time is wasted unless I learn something.

---

### Post by MrGrieves on 2007-12-17
I removed the .bak on the initrd file and now Gutsy is booting.

---

### Post by psusi on 2007-12-17
I am confused... selectfile is not a valid grub command, and Ubuntu installs an initrd ( well, it's actually an initramfs these days ) with the kernel.

---

### Post by Herman on 2007-12-23
Hello psusi,
MrGrieves was talking about selectfile in [Super Grub Disk]("http://sgd.benjamin-butschko.de/") when booting with that.

You were right about the empty MBR.  I zeroed my MBR with a 'dd' command to run a test with it and  it wouldn't boot. However, with the TestDisk MBR it does boot whichever partition has the boot flag. I didn't know TestDisk had a special booting code for the MBR, until I found the documentation about it. Now I know.
Thanks for correcting me, I wouldn't like to be going around spreading bad information.

Regards, Herman :)

---


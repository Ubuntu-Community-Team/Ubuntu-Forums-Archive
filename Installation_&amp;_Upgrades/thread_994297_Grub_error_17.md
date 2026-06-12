---
title: "Grub error 17"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by bjolen on 2008-11-26
Have installed Desktop Ubuntu 8.04.1 (from a cd from the downloaded ISO-file) OK on part0 on my hd3 (the last of 4 HDD:s) The grub boot code also installed on that disk and bios was alterd for boot from that disk.
When starting, the Grub boot menu displays OK and 1st alt (boot hd(3,0))starts but I got error 17 (cannot mount partition).
Using the edit facility in the grub boot menu i tried boot from all partitions from 0--5 on hd3 but all failed did the same with hd2 and hd4 (disk dont exist) no luck.
The partitioner on CD was used (manual) and the syspart. was mounted  /  (root) so I cant see any reason why the filesystem should be faulty. 
Whith the same CD I installed Ubuntu from within Windows and that worked OK. from here I could inspect the above file system and could not find anything unnormal.
Can anyone please hint me on what to do to be able to start the system on my hd3 (dev/sdd)? Thanks in advance  / Bjolen

---

### Post by cdtech on 2008-11-26
> 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.

Can you boot into the live cd open a terminal and type:
```
sudo fdisk -l
```

---

### Post by caljohnsmith on 2008-11-26
Getting that Grub error 17 when booting Ubuntu after a fresh install is unfortunately a known bug with the installer, based on many other threads I've seen with the same problem. How about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by Pumalite on 2008-11-26
From Super Grub:
'In a computer with more than one hard disk
GRUB error 17 could be caused by any of the above mentioned problems for single hard disk machines or else some confusion or disagreement between your computer's BIOS, the Linux kernel, and GRUB over which hard disk is the first hard disk and which is the second hard disk and so on.
Symptoms include GRUB being installed to MBR on the wrong (non-first) hard disk, and the /boot/grub/menu.lst file having the hard drive numbering wrong in each operating system entry.

Mixed IDE and SATA hard disks
Error 17 also commonly occurs when we have a mixture of IDE and SCSI or SATA hard drives plugged into the same motherboard.
If this is your situation, just try switching the 'Hard Disk Boot  Priority' around in your BIOS.
Here's a series of illustrations showing how I do mine, Changing the hard Disk Boot Priority.
I realize of course that most computers will have a different BIOS from mine, it would be impossible to give exact information that will suit everyone, but you should be able to see what I mean.
This method is proving to be the fastest, easiest and best solution for GRUB Error 17.
No time consuming editing of files or re-installing GRUB is necessary when the problem can be solved this way.
This method worked for NavyRST in the following thread: HOW-TO install boot loader from Ubuntu.
This solution should be fine for most computers, and it's well worth a try before resorting to editing configuration files and re-installing GRUB.

Another thing that can definitely cause this kind mix up  is when someone changes their hard disk Boot Priority in their BIOS in a computer that was working okay.  Therefore, it is not too surprising that one of the best solutions to this problem is to try switching the order of your hard drives back again.'

---

### Post by bjolen on 2008-11-27
Hi again
Thanks caljohnsmith for your superb advice this worked 100%.
It seems that grub when numbering HDD:S (x) in the hd(x,y) parameter for some reason starts from the HDD where the bootloader is installed (very strange) instead of from the first HDD (dev / sda in the partitioner).
On the other hand the installation program presets the root parameter to hd(3,0) when it according to above should be hd(0,0).
I think it would be useful if this problem could be pointed out in the downloadpage for Ubuntu possibly under known issues and in the documentation.
Also thanks Pumalite and cdtech for your replies.

Regards / Bjolen

---

### Post by caljohnsmith on 2008-11-27
> **bjolen said:**
> Hi again
Thanks caljohnsmith for your superb advice this worked 100%.
It seems that grub when numbering HDD:S (x) in the hd(x,y) parameter for some reason starts from the HDD where the bootloader is installed (very strange) instead of from the first HDD (dev / sda in the partitioner).
On the other hand the installation program presets the root parameter to hd(3,0) when it according to above should be hd(0,0).
I think it would be useful if this problem could be pointed out in the downloadpage for Ubuntu possibly under known issues and in the documentation.
Also thanks Pumalite and cdtech for your replies.

Regards / Bjolen
Actually, the way it works is that Grub on start up sees the order of drives as the same as the BIOS boot order, so if Ubuntu is on the drive you boot on start up (which is your case), then that drive is (hd0); therefore your Ubuntu entries in the menu.lst should use (hd0,X). If you want a little more detailed explanation, please see post #17 in [this thread]("http://ubuntuforums.org/showthread.php?t=984640"). Anyway, glad it worked, cheers and have fun with Ubuntu.

---

### Post by Pumalite on 2008-11-27
Or this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---


---
title: "Should I create a /boot partiton while installing Ubuntu if I already have Windows10?"
date: 2021-01-16
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-01-16
Should I create one partition for /boot if I have Windows 10 pre-installed. If I should create one how much size should I allocate to it?

---

### Post by ajgreeny on 2021-01-16
Simple answer is probably  no, but as in your other thread about the two disk system, it's difficult to be certain what you have already, what you want to have at the end of this, and therefore, how best to get there.

Please give us as much i formation as you possibly can otherwise we are just guessing!

---

### Post by EngineerStrange on 2021-01-16
Actually I have 1TB HDD and 256GB SSD. I use ubuntu mainly. Now I will be using SSD portion for apps and coding purposes(temporarily while doing it). But for storing data for long time I will use HDD .
(regarding the earlier post)
And want to make sure that the partition for ubuntu in HDD also gets automatically mounted. But I don't know how to do it.

---

### Post by ajgreeny on 2021-01-16
Gets automatically mounted when?

There is no point trying to mount or read the Ubuntu partition while running Windows as Linux partitions are invisible in Windows, but if you choose to boot Ubuntu from grub, which should show at boot in a dual boot system, the Ubuntu partition will automount at boot as you want.

---

### Post by EngineerStrange on 2021-01-16
No no I want it to get mounted while running Ubuntu.

---

### Post by Hagar Delest on 2021-01-16
What makes you think that you need a partition for /boot?
I would say the less convoluted the system, the better, for the system itself at least, especially for boot process.

---

### Post by C.S.Cameron on 2021-01-16
If you install Ubuntu on the same disk as Windows and in the same BIOS/UEFI mode as Windows, Ubuntu will take over the existing boot partition to run GRUB from. If Windows is installed in BIOS mode and you install Ubuntu the same, you do not need a boot partition.

If, for some reason, the other disk is not mounted on boot, open the partition in Disks click on the gears icon and Edit Mount Options.

---

### Post by yancek on 2021-01-16
You don't need a separate /boot partition.  If you are using windows 10 default it will be EFI on a GPT drive and Ubuntu will be installed EFI also.  The EFI files for both windows and Ubuntu will be in separate directories on the EFI partition.

If you have a second drive permanently attached it should be available under the directory /media/username (use actual username here) OR you could put an entry in the /etc/fstab file to mount it where you want.  If the drive is not permanently attached, don't put an entry in /etc/fstab.

---

### Post by EngineerStrange on 2021-01-16
I am unable understand what you said about directory/media/username?

---

### Post by CelticWarrior on 2021-01-16
It's not "[COLOR=#000000]directory/media/username"... It's about *the *directory **/media/username** where "username" is your actual username in the given system. This same directory is where all removable media is typically and automatically mounted.[/COLOR]

---

### Post by Hagar Delest on 2021-01-16
It's not clear at all what you're trying to do. What is wrong with your current installation?
I understand that you've a dual boot already and that you want to keep Windows.
Then what is the problem with all the drives or partitions being mounted at boot? Isn't it the default behavior to be expected?
You ask about /boot, do you got that it is a part of the system structure? Like /home for example?
A partition can be mounted anywhere you want, it can be mounted at boot or not. No need to fiddle with the fstab, there are utilities for that, more user friendly.
So, can you explain what is bothering you right now and what you want to have?
Note: I guess that you'll have an intensive use of your 2nd drive. Thus, better create a mounting point in your user profile (/home/your_user_name) so that it is accessible easily from any application/file browser.

---

### Post by EngineerStrange on 2021-01-16
The problem of boot is solved. Now the problem is that I have the OS installed in SSD but I want to store files in HDD. But I unable to do it?

---

### Post by Hagar Delest on 2021-01-16
First create a directory (a folder) where the drive has to appear (for example /home/your_user/Drive; use "Drive" or any other meaningful string). 
Use the Disk utility (that's what I have with Xubuntu) to have the HDD be mounted automatically on the mounting point defined above.
The application will take care of the fstab.

---

### Post by TheFu on 2021-01-16
> **EngineerStrange said:**
> The problem of boot is solved. Now the problem is that I have the OS installed in SSD but I want to store files in HDD. But I unable to do it?

a) Learn and understand Unix file and directory permissions.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) There isn't any way around learning this stuff, so rather than just ignore it, spend 45 minutes today and learn it now.  That will save you hours, days, weeks, months and for some people, YEARS of frustration.
b) Learn and understand what a "mount" is in Unix.  MS-Windows hid this very critical skill from you. It isn't automatic in any other OS.  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  Or google for "Ubuntu fstab" for some other how-tos.  
c) Please understand that with native Linux file systems, almost any method of mounting will probably be fast, but for foreign file systems like NTFS, exFAT, and FAT32, performance will suffer about 30% unless you mount them using the fstab and some specific mount options. Mounting dynamically using a file manager is almost always the worst performing method for any file system.  Plus, it won't happen until you actually click on the desired storage INSIDE the file manager.  There are ways to have storage mounted on-demand, as needed, by any process.  Plus, these other methods allow all the performance tuning and other options that foreign file systems need.  It is best to avoid foreign file systems on Linux systems so the system isn't full of compromises before necessary.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a reasonable reference book for Linux and many Unix commands.  Linux and Unix-like OSes are about 90% the same outside the GUI stuff.  Between Linuxen, that jumps up to about 95% the same with package management being where they split.  File systems management, mounting, ZFS, LVM, are all the same for data storage across all Linuxen.

Why are you dual-booting?  Really using a virtual machine would be much safer while your Linux/Unix skills improve.  There are all sorts of issues running on hardware that virtual machines make go away. Virtual machines bring all sorts of flexibility in other areas too.  For non-GUI stuff, 90% of native performance can be achieved using a tuned VM.

---


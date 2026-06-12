---
title: "trying to repair dual-boot system"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by Carl_Witthoft on 2016-02-09
I had a working ubuntu15.10 & windows 7 dual-boot system, until yesterday. The symptom was that the startup screen where I usually choose either ubuntu or windows failed to show the ubuntu choice (only windows or memtest). 
I booted from an install 15.10 and was able to see and read all volumes.  I followed the instructions to install boot-repair, which I installed on the sda volume (boot volume).   The pastebin is [http://paste.ubuntu.com/15001095](http://paste.ubuntu.com/15001095) .

So,I'm now stuck because when I boot the computer from the HD,  I drop directly into grub, about which I know nothing.  How do I get the  startup screen back that lets me choose to boot into either windows or ubuntu?   Do I need to run advanced repair options?  

Thanks for all advice
Carl

---

### Post by yancek on 2016-02-09
It's obvious why you can't boot Ubuntu based on the output of boot repair, it's because you have no menuentry for it in either the grub.cfg menu file from sda3 or sda5.  What exactly do you have on sda5?  It is a btrfs filesystem which is definitely not standard for Ubuntu.  Did you notice this error in the boot repair again referring to sda5:

> df: cannot access &#8216;/dev/sda5&#8217;: over-mounted by another device

Or this output, only 1 OS detected:

> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

What were you doing just prior to this problem?  Were you making some changes to the filesystem or bootloader?

---

### Post by Carl_Witthoft on 2016-02-09
> **yancek said:**
> It's obvious why you can't boot Ubuntu based on the output of boot repair, it's because you have no menuentry for it in either the grub.cfg menu file from sda3 or sda5.  What exactly do you have on sda5?  It is a btrfs filesystem which is definitely not standard for Ubuntu.  Did you notice this error in the boot repair again referring to sda5:



Or this output, only 1 OS detected:



What were you doing just prior to this problem?  Were you making some changes to the filesystem or bootloader?

I had downloaded the latest upgrades via the software update tool.  I got the  "restart required" notification,  but the battery died & the laptop shut down on its own shortly thereafter.  The next time I booted up, I was in this pickle.  
More info:  booting from a Ubuntu 15.10 install disk,  I can see all the volumes and their contents appear to be OK.   However,  I notice that the boot-repair gui has the two middle tabs (grub options) greyed out.  Can you confirm which volume I should install the repair, and then re-install grub itself, onto?   That is, I have a boot volume as well as the Ubuntu volume and the windows volume on this computer.    
I believe sda5 is a partition I created to "back up" files to a volume that the Windows OS can mount and read.  
I apologize for not reading the error messages I got, but since the repair-boot gui  reported complete success,  I had no inkling that it "fixed" things but that my volumes were still not properly configured.

---

### Post by oldfred on 2016-02-09
Your sda3 looks too small to be anything other than a /boot partition. But no kernels are found.
So your Linux system must be in sda5.

And your sda5 btrfs cannot be mounted. Boot-Repair tried running fsck on it, but fsck is only for ext2, ext3 or ext4. You need whatever is the equivalent to fsck for btrfs file systems and run that on your sda5.

Abnormal shutdown while system is running often corrupts files systems. And then a file check is needed.

You may then need to run the full uninstall/reinstall of grub2 with separate /boot ticked and install newest kernel ticked.

---

### Post by Carl_Witthoft on 2016-02-09
> **oldfred said:**
> Your sda3 looks too small to be anything other than a /boot partition. But no kernels are found.
So your Linux system must be in sda5.

And your sda5 btrfs cannot be mounted. Boot-Repair tried running fsck on it, but fsck is only for ext2, ext3 or ext4. You need whatever is the equivalent to fsck for btrfs file systems and run that on your sda5.

Abnormal shutdown while system is running often corrupts files systems. And then a file check is needed.

You may then need to run the full uninstall/reinstall of grub2 with separate /boot ticked and install newest kernel ticked.

Thanks; I'll try that tonight.   Since I have all my data backed up,  I could reinstall Ubuntu 15.10 into sda5.  Can I change the file system on that partition prior to reinstalling, and if so,  what FS do you recommend?

---

### Post by oldfred on 2016-02-09
The standard is ext4. And is better bases on most comparisons.
But it may have have some advanced features of some other file systems. But those have not yet proven to be reliable in Linux. Some have had no issues (until they do).

 6-Way File-System Comparison On The Linux 4.1 Kernel
[http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-41-filesystem&num=1)
Linux 4.0 File system HDD benchmarks
[http://www.phoronix.com/scan.php?page=article&item=linux-40-hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-40-hdd&num=1)

---

### Post by Carl_Witthoft on 2016-02-09
Well,  I have to say I have had no luck whatsoever.  I tried reinstalling Ubuntu after redefining sda5 as ext4 .    The installer told me the install was successful, but when I restarted, I got "unknown file system" and went right into grub-rescue.   
Now, I've been using Unix since 1985 and have a pretty good idea how to work on the guts of Windows and OSX, but this is a total mess.   boot-repair and fdisk and similar tools tell me they can see all my partitions, and I can mount them from the Ubuntu Install CD, and one of the partitions is described as "Windows" (which it is),  but I really have no idea how to convince the system to boot into the correct volume, let alone bring back the startup "select OS" grub screen.  Unless someone can walk me through the installer: exactly what mount point to pick for the "boot partition" and so on,  I'm pretty well stuck here.
While I appreciate advice like ""run the full uninstall/reinstall of grub2 with separate /boot  and install newest kernel"  ,  I do not see any such options when I try to reinstall grub from the command line or via the Ubuntu installer.   What am I missing?

---

### Post by yancek on 2016-02-09
> I tried reinstalling Ubuntu after redefining sda5 as ext4

Did you check the box to format that partition?
Did you leave the default for "Device for bootloader installation" at /dev/sda?
During the install of Ubuntu, you should have several options to install, Erase Disk, Install Alongside, Something Else, which are you using?
The mount point for the boot partition would be 'boot' which should be shown under the Mount point drop down box in the Edit partitions window whcih is available in the manual option, Something Else.

Take a look at the link below which is a very detailed tutorial specific to installing a current Ubuntu.  Also has info on a dual-boot install down the page.  See if that helps.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2016-02-09
And most desktop installs do not need a separate /boot partition. Often cleaner easier to maintain if just / and possibly /home or data partition(s). I use data partitions and have full system on SSD, and all data on HDD.
You may have needed /boot as ext4 when trying to use btrfs as there were (are?) issues directly booting from it.

---

### Post by Carl_Witthoft on 2016-02-10
Update: I have no idea why, but last nite I loaded repair-boot again, and this time all the GUI tabs were available.  I set the option to clear & reinstall the latest kernel.  BUt...  it's been sitting here for over 6 hours with the "now installing kernel, this may take a while" message.    When should I give up and restart the repair-boot app?

---

### Post by oldfred on 2016-02-10
Is Internet working? Boot-Repair has to download new copy of grub and/or kernels.

Are you using hard wired Ethernet, not Wi-Fi?
Not every wi-fi is supported with live installer, but almost all Ethernet are.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by Carl_Witthoft on 2016-02-10
> **oldfred said:**
> Is Internet working? Boot-Repair has to download new copy of grub and/or kernels.

Are you using hard wired Ethernet, not Wi-Fi?
Not every wi-fi is supported with live installer, but almost all Ethernet are.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

I am on hardwired Ethernet;  had no problem downloading updates & "extras" while installing Ubuntu and installing repair-boot.    Do I need to add some other repository to the ppa list?

---

### Post by yancek on 2016-02-10
>     Do I need to add some other repository to the ppa list? 		

Scroll down the page at the boot repair link below under second option under Getting Boot Repair.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Carl_Witthoft on 2016-02-10
Thanks, yancek, but that's not the problem.  I have boot-repair running.  It just can't complete the kernel replacement task.

---

### Post by oldfred on 2016-02-10
Then there may be some corruption in one of the files systems it needs to write into.
If now ext4, you can run fsck on the LInux partition.
Or if drive is older, use Disks and icon in upper right corner to check Smart Status of hard drive. 

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Carl_Witthoft on 2016-02-11
OK - finally fixed.    I'm not 100% sure, but I believe the two things that got things running were:  1) reformat sda5 as ext4 & reinstall ubuntu;  2) don't try to push anything into a separate partition for the boot directory.    I can now boot into either windows or ubuntu;  just have to reinstall apps on the ubuntu side and track down backups of some files.

THanks to all for providing guidance.

---

### Post by Geoffrey_Arndt on 2016-02-11
So, the lessons in this thread are:

1).   When performing large updates, make sure your laptop is plugged in to power, and, that your battery is at 100% in case of outage.
2).   Never experiment with your system and install non-supported file systems on it.
3).   Keep the install as simple as possible regarding partitions & file systems . . . start off by having a /root with all common or standard directories under it (/boot, /home, etc.)
4).   In the rare case an update is interrupted prior to finishing, . . . do not shutdown or reboot the system without running the system updater again, and picking up the missing files.
5).   Never do hard power downs (pressing on/off until system shuts down:   instead try:

ctrl + alt + PrtSc . . . and REISUB (**R**aising **E**lephants **i**s **s**o **u**tterly **b**oring . . . or . . . . **R**eboot **e**ven **i**f **s**ystem **u**tterly **b**roken).    I kind of like the second mnemonic because it make sense.

---

### Post by cmcanulty on 2016-02-12
I would change one item. Have a / partition for all boot and programs and system files and a separate /home partition. That way your docs and settings are protected if you reinstall or upgrade.

---

### Post by Carl_Witthoft on 2016-02-12
> **cmcanulty said:**
> I would change one item. Have a / partition for all boot and programs and system files and a separate /home partition. That way your docs and settings are protected if you reinstall or upgrade.
Well... I would modify that to:  Always backup anything you care about to a separate server or external memory unit.

BTW,  As best as I can recall, when I first set up my dual-boot,  I followed instructions (which may well have been out of date in 2014) so far as selecting btrfs  for the file system and creating a separate boot partition.  Now I know better :-)

---


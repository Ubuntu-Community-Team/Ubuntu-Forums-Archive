---
title: "Dualboot on separate physical drives (BIOS mode, MBR) - Win10(May) and Ubuntu 20.04"
date: 2020-07-27
forum: Installation &amp; Upgrades
---

### Post by ghristov on 2020-07-27
Hello everyone,

    I have a Dell Inspiron N5110 that is using BIOS and has no official UEFI support. I am using a Toshiba 640GB HDD with a HDD Caddy in the CD/DVD tray and a Samsung 860 Pro 256GB in place of the HDD. The Windows is installed on the SSD and Ubuntu on the HDD. I did the installation about a year ago and used **boot-repair** disk along with many different terminal commands to make it boot directly from the CD/DVD and eventually succeeded. However I don't remember the exact steps that I followed to make it happen. I am installing the operating systems using  Rufus 3.11 to create a bootable BIOS or UEFI-CSM, MBR USB stick with Ubuntu 20.04 and Windows 10 x64 Pro (may update).
    More than a week ago I had to reinstall Windows(due to permission problems), but didn't care to look at the boot config I used. I am now trying to replicate my previous dual boot config to no avail. The boot order currently is:


[LIST]
[*]CD/DVD 
[*]Hard Drive 
[*]USB storage 
[*]Network 
[*]eSATA 
[*]Diskette Drive 
[/LIST]
The OS configuration is as follows:


[LIST]
[*]/dev/sda - SSD 
[*]/dev/sda1 - System reserved 50MiB (I guess Windows is using it for some legacy support or other info) 
[*]/dev/sda2 - Windows System ~232GiB or smth (boot flag is placed here) 
[*]/dev/sda3 - System reserved ~513MiB (I guess recovery tools) 
[*]unallocated 2.18 MiB 
[*]/dev/sdb Toshiba HDD 
[*]/dev/sdb1 - ext4, Mounted **/**, 74.5GiB (also has boot flag, note that I tried using only 1 boot flag i.e. either Win or Ubuntu) 
[*]/dev/sdb2 - extended 78GiB
[LIST]
[*]/dev/sdb5 ext4, linux swap, 22.3GiB 
[*]/dev/sdb6 ext4, /home 55.88GiB 
[/LIST]
  
[*]Rest of drive is unallocated 
[/LIST]

The error message I keep getting while booting is - "**error: no such device: UUID of the HDD; error: unknown filesystem; grub rescue follows**". The only way I can boot in to the GRUB menu and select Win/Ubuntu/Memtest is if I press F12 to open the boot menu while the notebook is starting and manually select Hard Disk(it doesn't make sense to me). I have tried doing and mixing the following things, but none seemed to have any positive yield:


[LIST=1]
[*]Scramble the boot order to give the HDD some time to spin off 
[*]Place boot flag on sdb or sda only 
[*]Create a /boot partition for Ubuntu when installing it (I always install Ubuntu after I install windows) 
[*]Install GRUB using the Ubuntu installer either on sdb or sda - note, in sdX, not sdXY 
[*]Tried purging GRUB from Windows, because for some reason, part of it is getting placed there during Ubuntu install (according to Ubuntu logs) 
[*]Pulled the HDD with the Ubuntu in it, but the same error pops up (which confirms GRUB is installed in Windows partition, or there is a ROM that's keeping some settings; left the laptop unplugged for some days, without an external battery, but the CMOS battery is still good probably) 
[*]Boot-repair disk; multiple times - the yannubuntu version and the regular with recommended repair and targeted advanced options to place GRUB in Ubuntu install location 
[*]Before installing Windows, tried using **diskpart** to convert the SSD to GPT (not sure if this counts toward a hybrid GPT, might be talking nonsense) 
[*]Probably several other things I forgot about 
[*]Unicorn's blood 
[*]Haven't brought religion to it yet 
[*]A paste bin of what I tried today - [https://paste.ubuntu.com/p/VCmY8BBgxG/](https://paste.ubuntu.com/p/VCmY8BBgxG/) 
[/LIST]

   I read a lot of stuff over the course of a week, most of it describing how the Ubuntu system boots up, but everything is scrambled in my head right now. If it's loading GRUB from Windows and it's an MBR drive, it might not be able to read more than 4 partitions (don't believe it works in this manner accross deI hope it is not the HDD Caddy that's causing the late load, because it makes most sense. However this doesn't fit my previous experience with actually making it work seamlessly (for the end-user at least).
   I would be very glad if somebody can help me with a solution or at least elaborate what I am missing while doing the installation/repair of the OSes.

Thank you!

---

### Post by pbear42 on 2020-07-27
I've never tried to run a hard drive in the CD/DVD bay, but sounds like your computer is unwilling to treat it as a bona fide hard drive.  At least, that's what I infer from the fact it won't boot with CD/DVD at top of the list.  At a guess, it's looking for an ISO.  In any event, what I would try next is setting up to boot from sda.  You say you tried, but not what exactly you did.  Also, I notice boot repair claimed it was going to, but didn't.

Try this.  Move USB to top of the boot list.  Boot a live session.  Open Terminal and run:
```
sudo mount /dev/sdb1 /mnt 
sudo grub-install /dev/sda --boot-directory=/mnt/boot
```
Assuming this boots, you'll need to run sudo update-grub to pick up the Windows boot loader.
If it doesn't boot, you'll need to use chroot, but let's try this first.

---

### Post by ghristov on 2020-07-27
Hello pbear42,

   I have previously tried doing exactly as you  said - instructing grub where the actual boot is (in my case it's in the  root directory) and provided the new install location as /dev/sda. 
I  decided to do a clean install today, because I have modified too many  of the system files. I used the exact same setup I described in the  initial thread and for "device to install bootloader" I used /dev/sdb1.  The machine booted straight to Windows after the Ubuntu install. I then  went ahead and pressed F12 to boot the "Hard Disk" option manually,  entered Ubuntu and repeated the two lines you described + the "sudo  update-grub". At normal boot, I still got the same error I described  earlier.


Thank you!

---

### Post by oldfred on 2020-07-27
Some with drives in a DVD caddy could not directly boot from caddy, even though DVDs do boot from it.
So they have to have either MBR or /boot on the internal drive and rest of install on drive in caddy.

Windows only boots in BIOS mode from MBR partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.
Reformatting drive from MBR to gpt or vice-versa normally erases drive, but there are tools to convert that may not erase data, but good backups always required.

If BIOS mode, you are choosing drive to boot from. 
Grub only boots working Windows and that includes Windows cannot be hibernated. Windows fast start up sets hibernation flag, so fast start up must be off. And Windows regularly turns fast start up back on with updates. So you always need Windows repair/recovery flash drive and Ubuntu live installer for current versions of installs.

BIOS systems can only boot from MBR not from PBR - partition boot sector. So you never install grub to PBR or a partition like sdb1. You always install to a drive like sda, sdb, sdc etc.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pbear42 on 2020-07-27
> **ghristov said:**
> ... for "device to install bootloader" I used /dev/sdb1.
This is incorrect in any event, if you want the system you're installing to control Grub.  Always specify the device, not a partition.  This is true even in UEFI.

If you're able to boot Ubuntu, try again running just [COLOR=#ff0000]sudo grub-install /dev/sda[/COLOR].  The script should be able to figure out everything else.  
Then set boot order to USB, Hard Drive, then CD/DVD.  Maybe having that first in the list is what's confusing BIOS.

If that doesn't work, there's something squirrelly about your setup.  Grub install in MBR is pretty easy.  Do post a link to a boot repair report, as oldfred suggests.

---

### Post by ghristov on 2020-07-27
Oldfred,

[Here]("http://paste.ubuntu.com/p/MCxhs8j7bw/") is just the summary from the **boot-repair **disk in oldfred's post.****I am not sure why* **/dev/sda1*** is recognised as the Windows system when the actual system is on** */dev/sda2*.** ***/dev/sdc ***is the liveUsb. **uuid adf94cba-33a4-4dcc-9832-2b72fb8a0163** is the Toshiba HDD. Again, pressing F12 and choosing "Hard Disk", which evaluates to the internal HDD, not the ODD, opens the GRUB menu and presents me with working OS choices( Windows 10 choice is reported as ***/dev/sda1*** in the menu).

> Windows fast start up sets hibernation flag, so fast start up must be off.
This is the first thing when I turn off in a fresh Windows installation, along with hybrid sleep.

pbear42,

My latest install of Ubuntu has the bootloader installed directly in ***/dev/sda ***via the Ubiquity installer.

Thank you!

---

### Post by oldfred on 2020-07-27
Windows 7 or later typically has a smaller Boot partition in BIOS boot mode. Not normally shown in Windows. So your BIOS/MBR install on sda is standard Windows.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

You show grub installed to MBR of sda.
But do not have grub installed to MBR of sdb. If your system lets you directly boot sdb drive, you should install grub to sdb and install a Windows boot loader to sda.

Since grub only boots working Windows and sometimes Windows breaks, you need a way to boot Windows. Best is if you have two MBR (or UEFI as it supports multiple boots from one drive).
But if you can only boot from sda drive, you have to have grub in MBR of sda and when Windows will not boot have to temporaily install a Windows boot loader to sda, repair Windows and restore grub.

Or you always need both a Windows repair flash drive and Ubuntu live installer for current versions of installs.

---

### Post by ghristov on 2020-07-27
Oldfred,

According to the information you posted for BIOS/MBR partitioning schemes, I should have a bootable and fully functioning Windows 10 on my ***sda ***drive. In the current situation I would use a Windows Installation USB to recover the MBR via > bootrec /fixmbr in a CMD at boot time. I should then go ahead and install GRUB on ***/dev/sdb***, supposedly using the following from a live Ubuntu USB: > sudo grub-install --target=i386pc --boot-directory /mnt/boot /dev/sdb (this should place the GRUB files in the MBR of the Toshiba Drive) and then use utilize proper boot order to boot from ***sdb***. If I manage to boot in Ubuntu, I should probably do "sudo update-grub". Have I understood the task correctly?

One more thing that I noticed - the latest Pastebin shows that there is a /boot folder and some GRUB cfgs in sdb1. Doesn't this mean that there's actually a bootloader installed for Ubuntu and if so, why is it not getting loaded by Windows?

Thank you!

---

### Post by pbear42 on 2020-07-27
If you're installing Grub from a live session, you have to mount the root/system partition to /mnt, as in the form of command I gave earlier.

Obviously it makes a difference whether Ubuntu is on sda or sdb.  Meanwhile, does BIOS list both?  Or is it only HDD vs. CD/DVD?

---

### Post by ghristov on 2020-07-27
pbear42,

I fixed the Windows MBR, mounted the root/system as you instructed me earlier, and re-installed GRUB to** */dev/sdb*** from the LiveUSB* . *I am no longer getting the initial error, but it's still not booting automatically.
The BIOS recognizes both HDD and CD/DVD(marked as SATA ODD) by their device names and has them both in the boot menus.

Thanks!

---

### Post by oldfred on 2020-07-27
BIOS systems boot from MBR.
Windows uses boot flag to find primary NTFS partition with boot flag & has more code in partition boot sector.
Grub has code (core.img) in sectors just after MBR (if MBR partitioned or in bios_grub if gpt) that searches for rest of grub in your install. Grub does not use boot flag, but a few BIOS require a boot flag, so we usually suggest you have one partition with boot flag on every drive.

Pictures here worth 1000+ words Older Windows but same for all BIOS versions. See graphic for quick overview of BIOS boot process.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

---

### Post by pbear42 on 2020-07-28
> **ghristov said:**
> I am no longer getting the initial error, but it's still not booting automatically.
Sorry, but this has gotten too complicated, so I'm going to bow out.  Good luck.

---

### Post by ghristov on 2020-08-03
Oldfred,

    Going through the latest links you posted took me some time to read and digest. I can understand the boot sequence a bit better now and I can see how unforgiving the Windows boot process can be on some occasions. I eventually managed to configure the two OSes to work together by:


[LIST]
[*]Creating a 1GiB partition **(*/dev/sda1*) **in the beginning of ***/dev/sda*(the SSD placed in the SATA HDD)**
[*]Using the Ubuntu installation media i formatted ***/dev/sda1 ***as *ext4, *marked as **/boot** and installed the bootloader in ***/dev/sda***
[/LIST]
***&#8203;***   
   This is most probably the same thing that happened last time I successfully dual-booted these two, while installing(probably) the bootfiles in the Windows dir using boot-repair.

Thank you for the help!

---


---
title: "[HOWTO] Dual-boot Windows 7 and Ubuntu 9.10 on HP dm3-1010ed"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by simeon87 on 2010-02-06
The following is a step-by-step guide on dual-booting Windows 7 and Ubuntu 9.10 on a HP dm3-1010ed notebook. I'm just sharing it because it might save others some trouble.

**Requirements:** (aka, what I've used, yours could be similar)

[LIST]
[*]A desktop computer running Ubuntu 8.04
[*]A 4GB USB stick
[*]HP dm3-1010ed running Windows 7
[/LIST]

**Overview:**

Since the hp dm3-1010ed has no CD/DVD, we need to boot Ubuntu 9.10 from a USB stick and install it from there. The general procedure is as follows: create a bootable USB stick for Ubuntu 9.10, backing up a partition that needs to be deleted, modify partitions in Windows 7, boot Ubuntu 9.10 from the USB stick and install it using the installer in the largest continuous free space (or whatever partitioning schema you like for your install).

**Step 1: Create a bootable USB-stick**

[LIST]
[*]Download the Ubuntu 9.10 64 bits .iso file from ubuntu.com
[*]Install the program usb-creator using the following command in a terminal (Applications > Accessories > Terminal):

```
sudo apt-get install usb-creator
```

If the Ubuntu version you're running doesn't have the program in its repository, like Ubuntu 8.04, you'll need to enable backports in Synaptic first: Start Synaptic (System > Administration > Synaptic, then Settings > Updates and check the one for hardy-backports).
[*]After installing usb-creator, it can be found in System > Administration > Create a USB startup disk
[*]Plug the USB stick and select the .iso file in the top menu.
[*]Create the bootable USB stick; the amount of reserved space doesn't matter because we're not going to use the USB stick for long
[/LIST]

**Backing up a partition that needs to be deleted:**

First, some background knowledge: one can only have 4 primary partitions on a hard-disk and the hp dm3-1010ed already has 4 primary partitions pre-installed. The four partitions are: SYSTEM, OS, RECOVERY and HP_TOOLS. To see this, boot into Windows 7, open the menu and right click Computer, then Manage. Then go to Disk management to view the disk. The first partition is for booting, the second contains Windows 7, the third is for restoring the machine to factory condition when things go awry and the fourth partitions contains some HP specific tools.

There is however a way around this limitation of 4 primary partitions and that is to create an extended partition. An extended partition is also a primary partition but it can contain other partitions as well, called logical partitions. Since we can't create an extended partition right away (since that would require having 5 primary partitions at once), we need to delete a partition first. The easiest way is to let the Ubuntu installer handle it for us. In any case, we do need to remove a primary partition to enable the installer to create the needed partitions for Ubuntu.

The first three don't seem to be a good choice but the HP_TOOLS partition can go. This partition contains tools that HP has installed, depending on the type of computer. On the dm3-1010ed, it only contains a SystemDiags tool which can be used as a visual interface for system diagnostic when you boot. To see it, start the computer, press Esc while booting and select System Diagnostics. The white/blue interface is provided by this tool and when the partition is removed, it'll still work but it'll simply be a black/white text interface. I haven't checked it thoroughly but some tests may not be available afterwards. Searching online for 'HP EFI Guidelines' also gives a document with more information about this partition.

To back it up:

[LIST]
[*]Plug the USB stick with Ubuntu
[*]Reboot the computer and press Esc while booting
[*]Select boot options
[*]Select the USB stick
[*]Let it boot Ubuntu 9.10 from the USB stick
[*]Go to Places > HP_TOOLS to mount it, then Places > Computer > HP_TOOLS to view the contents. In the Hewlett-Packard directory, you should have a directory called SystemDiags. If there are more, you should search online to see what tools you'd 'lose' when removing this partition. Make a copy of the whole partition and store it somewhere. It may also be possible to restore this functionality by recreating the HP_TOOLS FAT32 partition afterwards but I haven't checked that.
[/LIST]

**Managing partitions in Windows 7:**

We now have a backup of the HP_TOOLS partition and we can now make some changes.

[LIST]
[*]Reboot in Windows 7
[*]Start menu > Right-click Computer, Manage
[*]Go to Disk Management
[*]Here's a panel with all the partitions on your hard-disk
[*]We're going to do two things: shrink the OS partition and delete the HP_TOOLS partition.
[*] Right-click the second partition with Windows 7 and use Shrink Volume. This is going to create free space where we can install Ubuntu 9.10 later on. How much space you want for Windows 7 and how much for Ubuntu 9.10 is up to you.
[*] Right-click the HP_TOOLS partition and delete it.

It should now look like this: [ SYSTEM ][ OS ][ unallocated ][ RECOVERY ][ unallocated ]
[/LIST]

Reboot to let Windows 7 update its configuration files.

**Installing Ubuntu 9.10:**

[LIST]
[*]Reboot into Ubuntu 9.10 using the USB stick.
[*]You could move the RECOVERY partition so that it is behind the OS partition but it's probably safer to leave it where it is, unless you really want the unallocated space at the end (only 100 MB here). If you want to move it, use Applications > Accessories > Terminal, then ```
sudo gparted
``` and move the partition there. If you do, you must restart and boot into Windows 7 to make sure it knows that the partitioning has changed.
[*] You can now use the Install Ubuntu 9.10 option and when asked, install it in the largest continuous free space or specify your own way of partitioning using the advanced option.
[/LIST]

Ubuntu 9.10 should now be installed. Just reboot to check that you get the GRUB boot menu which now shows Ubuntu and Windows 7 as bootable operating systems.

---

### Post by iloutzu on 2010-02-07
Great guide, thank you!

I would like to suggest an alternative to step 1, for those who don't have an Ubuntu computer nearby: download Unetbootin for Windows ([http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")) and use it in Win 7 to create a bootable USB with Karmic. I have recently used it on an Asus ul30a-a2, and it worked very well (you can use it to install a distro from online repositories, or you can just download the .iso and use that option).

---

### Post by vojtagrec on 2010-05-02
Thank you for a great guide! I have to confirm that moving/recreating HP_TOOLS partition works. I created it as a logical partition of a different size. It only has to be proper FAT32 and contain the original file hierarchy (Hewlett-Packard\SystemDiags) and it works. Tested on a brand new Pavilion dm3-1120ec.

---

### Post by TeoLinuX on 2010-05-25
did anyone try successfully what has been illustrated in this guide on the model dm3 1010EL ? (it's a model sold in italy and europe)

is it possible to create a restore disc on a usb key?

---

### Post by supermario87 on 2010-05-30
yes! you need a 8GB key

p.s.
the hp tools partition can be restored with an utility on hp download centre(basically it offers a graphical interface to the bios diagnostic tools, quite unusefull)

---

### Post by blue_bullet on 2010-10-08
Thank you for this guide.  I installed Ubuntu 10.04 64bit as a dual boot with Windows 7 using your instructions.  HP Pavilion dv7-4083cl laptop.  Originally I managed to blow Windows 7 off before I found your guide.  HP mailed me system recovery disks and a new 500 gb hd though I expect the original hd may not have been corrupted.  It had Ubuntu 10.04.1 amd64 and 10.10beta amd64 installed on it.  Just no Windows 7.  

I had to run the HP system recovery disks 3 times before Windows 7 would reinstall on the new hd.  It got a little further along each time I ran the 3 disk set.  I tried 3 times on the original hd and it always stopped at the same place.  With the new hd the recovery process got a little further each time.  Scary.

Per your guide I shrunk the Windows 7 to 227GB and deleted the HP_Tools partition.  Did not try to move the recovery partition at this point. The Disk Usage Analyzer shows I have 202.8 GB total filesystem capacity in Ubuntu 10.04.1.  I am happy. Windows 7 has 227GB, more than it needs, but I expect the M$ developers purposely put the MFT files where they did on purpose.  I am sure they have a technical explanation for having done it.

Grub or Grub2 shows Ubuntu first, then Windows 7, then Windows Vista.  I do not know what the vista bit is about. Bottom line is Ubuntu 10.04 64bit and Windows 7 64bit are living nicely together side by side.  Thank you again.   

I should add that HP support was excellent on this.  They may have known something about the hd as they had paperwork complete to send me a new one even before I had completed the quick and long hd tests on boot up diagnostics on the original hd.

---

### Post by mikyo on 2010-11-28
This was very, very helpful. Thanks so much for posting it.

---

### Post by HeyAZ on 2011-01-01
Question re: HP_TOOLS partition which is being deleted.
Is it possible to save hp_tools to a flash drive, delete this partition, then set up a new partition on Win7 which is logical (not primary) for the hp_tools, same name, formatted FAT32?  Then can also set up logical partitions for ubuntu.
So same primary partitions: System, C (Windows 7), D (Recovery).
Logical partitions as extensions which comprise the 4th primary:
/ 
/swap 
/boot  
hp_tools

Will this work?  Can the hp dv4 laptop still access hp_tools as before?  
Thx.

---

### Post by HeyAZ on 2011-01-01
Question re: HP_TOOLS partition which is being deleted.
Is it possible to save hp_tools to a flash drive, delete this partition, then set up a new partition on Win7 which is logical (not primary) for the hp_tools, same name, formatted FAT32?  Then can also set up logical partitions for ubuntu.
So same primary partitions: System, C (Windows 7), D (Recovery).
Logical partitions as extensions which comprise the 4th primary:
/ 
/swap 
/boot  
hp_tools

Will this work?  Can the hp dv4 laptop still access hp_tools as before?  
Thx.

---

### Post by Euboon2 on 2011-01-03
One way to overcome the fact that the laptop comes formatted with 4 primary partitions (system, Cdrive, Recovery, HP_Tools):

1. Make sure the recovery and hp_tools are intact, or make recovery DVD first.
2. Delete the Cdrive, and replace with extended partition.
3. Create a small NTFS partition in the extended partition to accomodate windows installation. The remaining space can be left for linux installation later.
4. From the startup, choose HP recovery and restore to a minimal image.
5. Reboot and HP will continues to install the system, with several reboots.
6. Install linux.

This procedure  will install windows into the small NTFS partition within the extended partition, while leaving the system partition (master boot record), recovery partition, and HP_Tools partition intact.

It is best to install linux later, since it would overwrite the MBA, and when HP restores the system, it needs to restart several times. But installing linux before restoring windows would mean overwriting the MBR with linux as the default choice during bootup. The windows restoration requires several reboots and one would then need to keep watch in order to select the windows after each reboot.

---

### Post by Robert Carnegie on 2011-01-15
> **Euboon2 said:**
> One way to overcome the fact that the laptop comes formatted with 4 primary partitions (system, Cdrive, Recovery, HP_Tools):

1. Make sure the recovery and hp_tools are intact, or make recovery DVD first.
2. Delete the Cdrive, and replace with extended partition.
3. Create a small NTFS partition in the extended partition to accomodate windows installation. The remaining space can be left for linux installation later.
4. From the startup, choose HP recovery and restore to a minimal image.
5. Reboot and HP will continues to install the system, with several reboots.
6. Install linux.

This procedure  will install windows into the small NTFS partition within the extended partition, while leaving the system partition (master boot record), recovery partition, and HP_Tools partition intact.

Hi - just to check, does that for sure work for Windows (as far as you know)?  I have this situation on a new TouchSmart TM2-1010EA laptop now.

I'm also considering whether I can afford to just delete the partitions that aren't the Windows OS itself.  But they're all more-or-less significant.

---

### Post by Forever Delayed on 2011-01-22
Hi there, first post!

Just got a brand new HP laptop myself and ran into this problem when trying to install Ubuntu 10.10. This guide seems to be the perfect solution, however, explain one thing to an inexperience intermediate: how does one copy a partition and store it somewhere? I tried the most obvious approach (copy and paste) but I am told I cannot do this to a mountable file. Anyone wanna walk me through it? The rest of the process should be no problem whatsoever.

Thanks!

---

### Post by wilee-nilee on 2011-01-22
> **Forever Delayed said:**
> Hi there, first post!

Just got a brand new HP laptop myself and ran into this problem when trying to install Ubuntu 10.10. This guide seems to be the perfect solution, however, explain one thing to an inexperience intermediate: how does one copy a partition and store it somewhere? I tried the most obvious approach (copy and paste) but I am told I cannot do this to a mountable file. Anyone wanna walk me through it? The rest of the process should be no problem whatsoever.

Thanks!

This is a thread filled with misinformation, don't follow it!!!

So start your own thread and run this script with a Live Ubuntu CD. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Your messing with the possibility of bricking the MS without doing the correct process.

---

### Post by Robert Carnegie on 2011-01-22
> **Forever Delayed said:**
> Hi there, first post!

Just got a brand new HP laptop myself and ran into this problem when trying to install Ubuntu 10.10. This guide seems to be the perfect solution, however, explain one thing to an inexperience intermediate: how does one copy a partition and store it somewhere? I tried the most obvious approach (copy and paste) but I am told I cannot do this to a mountable file. Anyone wanna walk me through it? The rest of the process should be no problem whatsoever.

Thanks!
I use partimage, which is provided for Ubuntu but is not on the CD.  If you find the instructions for e.g. downloading and adding it to Ubuntu-on-USB created from the CD intimidating (I sure do), then you can download the bootable SystemRescueCD Linux distro instead, with partimage on the disc.  You can also use ntfsclone (for NTFS) or dd, but that's more complicated, and, in the case of dd, doesn't understand that disk space is unused and doesn't need to be copied.  gzip is reasonably fast good-quality compression of your partition copy - a copy of my 30 GiB Windows partition (I hope) is about 16 GiB.  Also, partimage automatically saves your MBR and partition table.  (Restore isn't compulsory.)  I tell whichever tool I'm using to split the backup copy into 315 MiB segments (this is a separate command except with partimage), which pack nicely later on CD or DVD, and, of course, aren't troubled by the FAT32 file size limit of 4 GiB.

ntfsclone and partimage themselves don't support moving a Windows NTFS boot and/or system partition onto a new address, but they should be - are - able to back up and restore to the initial location in a working state.

In my case I've now found that a replacement or update of the "System Diagnostics" for my model that are the contents of the "HP_TOOLS" partition can be downloaded from HP's support web site and installed from the Windows executable setup program provided onto hard disk -or- onto a USB external disk or "flash RAM" device, if you can find one small enough  :-)  (and that's bootable - some aren't). So I'm going to try killing the HP_TOOLS partition - I'm sceptical of booting Windows from a converted extended partition - and install the downloaded HP tools onto an SD card -or- USB for occasional use.  

But I advise you to back up -all- of the disk partitions, including HP_TOOLS, before deleting -anything-.  And also make the Windows recovery discs -first-, on good quality DVD-R (try TDK Scratch Proof), if you didn't get a full set of discs with your computer, -and- make the separate quickie system maintenance disc or whatever it's called.  Playing with partitions CAN make your disk broadly unrecoverable, and you don't get a new free edition of Windows every six months!  Also...... Windows' own partitioning is weird!

You can also backup -some- partitions using Windows 7 tools - I think HP_TOOLS isn't included, but see above.

Or...... you could leave the partitions alone and use Wubi to install Ubuntu into one big file on the existing C:  (Still make all the backups, tho'!  If you can!)

---


---
title: "HOWTO multi-boot using Windows NTLDR"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by six on 2006-07-04
If you want to try several Linux distros alongside Windows, this method is a good way to achieve it, as it lets you multi-boot using just one simple menu.

Why not just use Grub? Well, firstly Grub typically resides on the MBR, and booting through Windows leaves your MBR "clean" with the default Windows NTLDR boot loader. (Some AV's are reported to not like anything else taking over the MBR).

Secondly, giving each distro their own independent boot loader means [in theory] you should be able to mix and match Grub and Lilo, by re-installing them off the MBR into their own /boot partition.

I can verify that updating the kernel works perfectly. Each distro's /boot partition maintains their own data, with Grub automatically updating the "magic" section of menu.lst

I wanted to try out all four Ubuntu variants; Ubuntu, Kubuntu, Edubuntu and Xubuntu - and also some other distros such as Fedora, openSUSE, Debian, Linspire, Mandriva etc. before selecting the "one Linux to rule them all". 8)

After a great deal of research, reading out-of-date guides and conflicting opinions, I found many articles and messages on various sites and forums saying how to go about multi-booting using the Windows boot loader, but none seemed to stitch everything together in one neat package. So I thought I write a HOWTO for anyone else interested in doing the same thing.

---

Tools you will find useful or need:

Partition Magic (Windows)
Norton Ghost 2003 + GDISK.EXE (Windows)

or free/GPL tools:

Qtparted (Linux)
Partimage (Linux)
fdisk (Linux)
MBR520.ZIP (Windows)

Either set of utilities ideally need to be run off a boot CD, floppies or USB. (It's safer that way.)

You can download a rescue CD with the Qtparted and Partimage utilities from here:

[http://www.sysresccd.org]("http://www.sysresccd.org")

More documentation for Partimage is available here:

[http://www.partimage.org]("http://www.partimage.org")

To create your own boot CD, Bart's way to create bootable CD-Roms (for Windows/Dos) is a good place to begin:

[http://www.nu2.nu/bootcd/]("http://www.nu2.nu/bootcd/")

This page contains everything you'd need to jump straight in:

[http://www.nu2.nu/bootcd/cdromsi/]("http://www.nu2.nu/bootcd/cdromsi/")

Copy your [Norton Ghost rescue floppy] GHOST.EXE and GDISK.EXE programs into the bcd_cdromsi\bcd\cds\cdromsi\files folder, and also the [Partition Magic rescue floppy] PMHELP.DAT, PQMAGIC.EXE, PQMAGIC.OVL, PQMAGIC.PQG, PQPB.RTC and zABOUT.PQG files if you have them. Be aware that you shouldn't exceed 2.88MB, as bcd emulates a "super" floppy.

If you can't get or don't have fdisk (either for DOS or Linux), you could use this free utility:

[http://www.allthatcounts.com/comp/mbr.htm]("http://www.allthatcounts.com/comp/mbr.htm")

Which lets you save and restore your MBR. (Copy the files from the .zip into your cdromsi folder as well).

If you need to update Norton Ghost 2003, you can download these two patches:

[http://pcsystems.princeton.edu/nav/ng2003b789_en.x86]("http://pcsystems.princeton.edu/nav/ng2003b789_en.x86")
[http://pcsystems.princeton.edu/nav/ng2003b793_en.x86]("http://pcsystems.princeton.edu/nav/ng2003b793_en.x86")

Rename them as .zip's, then unzip them. Replace the contents of the 789 folder with the contents of 793. The GDISK.EXE and GHOST.EXE files are dated late 2003, and are the ones to include on your boot CD or floppy. The Readme will tell you how to update your Windows installation of Ghost.


**Step 1 - Planning your partitions**

Plan carefully how you're going to repartition your drive(s). Shrink your Windows partition to leave space after it, with Partition Magic or some other utility.

Then create a logical partition (within an extended partition, within a primary partition) filling the empty space. Make sure you apply the action, then promptly delete the logical partition.

This will let you fill up the empty space with as many separate logical partitions as you need. (It's the easiest and safest way of doing so.)

For example, I wanted to fit a maxium of 13 distro's on my laptop's WD 120GB HD. I planned on allocating 6GB for Windows, 1GB of Linux swap space, and 6GB for each Linux distro. It's a good idea to have a FAT32 partition that you can use to exchange files between Windows and each Linux distro, as well as for backing them up.

Next should come the Linux Swap partition, typically twice the amount of RAM you have (or a maximum of 2GB). Then a /boot and / partition for each distro. Say, approx. 144MB for the /boot partition and 6000MB for the / partition.

One way to do it, is to start assigning the Linux distro partitions from the right, working your way left. After you've added the Swap partition, you're then left with the [previously unknown] amount of space for your common FAT32 partition.

The reason the FAT32 and SWAP partitions should "go first" is because then their device allocation (eg. /dev/hda6) won't change. If you created them last, or to the right, each time you added a distro under them, that device allocation would change - which is not a good idea!

Using up only the two primary partitions (one for Windows, the other for all the logical drives) means you've got two spare for other boot-loaders or unusual installations (such as Damn Small Linux) which insist on having one or more primary partitions available. (You can always shrink the large extended partition to allow room).

For example, here's a breakdown of the partitions I created, allocating 6GB for each of the four Ubuntu distros:

```


 [1] PRI NTFS    6149MB "WINXP"    (hda1)
 [2] EXT LBA
 [3] LOG FAT32 ~33494MB "FAT32"    (hda5)
 [4] LOG SWAP    1024MB "SWAP"     (hda6)
 [5] LOG EXT      149MB "UBU-BOOT" (hda7)
 [6] LOG EXT     6001MB "UBUNTU"   (hda8)
 [7] LOG EXT      149MB "KUB-BOOT" (hda9)
 [8] LOG EXT     6001MB "KUBUNTU"  (hda10)
 [9] LOG EXT      149MB "EDU-BOOT" (hda11)
[10] LOG EXT     6001MB "EDUBUNTU" (hda12)
[11] LOG EXT      149MB "XUB-BOOT" (hda13)
[12] LOG EXT     6001MB "XUBUNTU"  (hda14)
[13] LOG EXT     6149MB {pre-allocated ready for next distro}

+ remaining empty space in logical partition
```

Don't create more than twelve partitions, as the graphical partition editor in the Ubuntu installer won't be able to see them, as it doesn't have a scroll bar.


**Step 2 - Save the Windows boot loader (NTLDR)**

If you don't have GDISK or FDISK, you will need to save the Windows boot loader (NTLDR) residing in the MBR at this point. Use the GETMBR utility to save it to the common FAT32 partition, eg. GETMBR C:\NTLDR (don't use more than five characters for the filename).

If you've already tried installing GRUB or LILO, and don't have the original Window's MBR (or can't use the FIXMBR utility off the XP installation CD), you might be able to restore it with the GENERIC files that come with with MBR520.ZIP package, although I haven't verified this.


**Step 3 - Install the distro**

Boot the Ubuntu live CD, then install it to HD. On the "Install - Prepare disk space" screen, select "Manually edit partition table", skip past the "Prepare partitions" screen, then on the "Prepare mount points" screen, make sure you allocate the correct mount points and partitions for the distro, eg. the first distro's slots would be /dev/hda6 for the swap, /dev/hda7 for /boot and /dev/hda8 for /

Where you see something like /media/hda3, change it to /media/fat32, so you will be able to write to the common FAT32 partition later. Blank all the other mount points and partitions out by scrolling to the top blank entry in each item list, for example:

```

Mount Point    Size   Partition                                 Reformat


/               6Gb   Partition 8 Disc IDE/ATA 1 (Logical) [hda8]   Y


/boot         149Mb   Partition 7 Disc IDE/ATA 1 (Logical) [hda7]   Y
swap            1Gb   Partition 6 Disc IDE/ATA 1 (Logical) [hda6]   Y




/media/fat32   33Gb   Partition 5 Disc IDE/ATA 1 (Logical) [hda5]   Y


```

After the initial installation is complete, click on the System Update icon (which should be flashing or otherwise announcing itself). Apply all the updates, then restart - as the circular blue arrow icon recommends.


**Step 4 - Moving boot loader from MBR to the /boot partition**

At this point, Grub will have installed itself by default into the MBR, so select the [default] latest kernel option and wait for Ubuntu to finish loading.

You then need to edit the /boot/grub/menu.lst file (possibly known as grub.conf on other distros). Open a console, and make a backup first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then use Gnome's GEDIT to open it:

```
sudo gedit /boot/grub/menu.lst
```

Change the timeout value (from 10) to 3 and unhide the hiddenmenu by removing the single # character in front of it. Scroll down to the bottom, until you reach the "## End Default Options ###" section.

Below it, there will be several "paragraphs", typically the top two representing the latest kernel, the next two the previous kernel, and the last one memtest86+

Remove the two previous kernel boot options if you wish. For Kubuntu, Edubuntu and Xubuntu, change the default title name of "Ubuntu" to the correct respective title.

Scroll down right to the bottom, until you see the "### END DEBIAN AUTOMAGIC KERNELS LIST" section. Remove everything after that line, as you won't be using Grub to boot into Windows.

For example, you should be left with something that looks like the following:

```
## ## End Default Options ##

title       Kubuntu, kernel 2.6.15-25-386
root        (hd0,8)
kernel      /vmlinuz-2.6.15-25-386 root=/dev/hda10 ro quiet splash
initrd      /initrd.img-2.6.15-25.386
savedefault
boot

title       Kubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,8)
kernel      /vmlinuz-2.6.15-25-386 root=/dev/hda10 ro single
initrd      /initrd.img-2.6.15-25.386
boot

title       Kubuntu, memtest86+
root        (hd0,8)
kernel      /memtest86+.bin
boot

## END DEBIAN AUTOMAGIC KERNELS LIST ##
```

It's important to leave the start and end of the Automagic Kernels section alone, because then Grub can automatically update the boot options when the kernel is upgraded.

Save the file and return to the console prompt, then type:

```
df
```

to double-check which device allocation your /boot partition is on. Look for /boot in the "Mounted on" column, then scan left to find the /dev/hda{n} identity. Note that it should be one less than the / identity in the menu.lst file, ie. if / is /dev/hda10, then /boot should be /dev/hda9

Issue the command:

```
sudo grub-install /dev/hda9
```

(don't worry about the "bug in xfs_freeze" comment that might be displayed). This has now installed the Grub boot-loader in your /boot partition, so it can safely be removed from the MBR, and replaced with the Windows boot loader again.

We now need to copy the first 512 bytes of the /boot partition, and output them into a file which the Windows boot loader can use to bounce into the correct Linux distro. Use the command:

```
sudo dd if=/dev/hda9 of=/home/{user-id}/Desktop/ubuntu.lnx bs=512 count=1
```

then copy it over to the common FAT32 partition. Or you might be able to create it directly with:

```
sudo dd if=/dev/hda9 of=/media/fat32/ubuntu.lnx bs=512 count=1
```

Close the console, then restart the computer, booting up your rescue CD or floppy.


If you're in a KDE desktop, such as Kubuntu uses, you might need to go about things slightly differently, due to permission controls not letting you edit the menu.lst file directly. Open a console, then type:

```
cd /home/{user-id}/Desktop
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo cp /boot/grub/menu.lst menu.lst
```

Right-click -> Open to edit the menu.lst file on your desktop, then apply the changes as detailed above. Save it to your desktop under a different name, such as menu.lst.new, then copy it back into its original directory with:

```
sudo cp menu.lst.new /boot/grub/menu.lst
```


**Step 5 - Restoring the Windows boot loader (NTLDR)**

After booting to your rescue CD or floppy, restore the Windows boot loader using Norton Ghost's GDISK with:

```
GDISK 1 /MBR
```

or by using the MBR520 package's RESTMBR utility.

Remove the boot CD/floppy, then restart and go back into Windows.


**Step 6 - Copy the distro's boot loader file to C:**

Using Windows Explorer, copy the ubuntu.lnx file from the common FAT32 partition into the root directory of C:


**Step 7 - Editing the BOOT.INI file**

Open a DOS prompt, typically by selecting RUN off the start menu, then entering CMD in the input box.

Change to the root C:\ directory, then set the attributes of the BOOT.INI file by editing it in Notepad with:

```
cd \
attrib -h -s -r BOOT.INI
notepad BOOT.INI
```

Reduce the timeout value (in seconds) from 30 to 10.

Underneath the last "multi(0)disk(0)..." line, add the line:

```
c:\ubuntu.lnx="Ubuntu Linux"
```

For example, after adding several distros your BOOT.INI file could look like this:

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Pro" /noexecute=optin /fastdetect
c:\ubuntu.lnx="Ubuntu Linux"
c:\kubuntu.lnx="Kubuntu Linux"
c:\edubuntu.lnx="Edubuntu Linux"
c:\xubuntu.lnx="Xubuntu Linux"
c:\fedora.lnx="Fedora Linux"
c:\opensuse.lnx="openSUSE Linux"
c:\mandriva.lnx="Mandriva Linux"
c:\debian.lnx="Debian Linux"
c:\gentoo.lnx="Gentoo Linux"
c:\linspire.lnx="Linspire Linux"
```

Note that the filename you use for the .lnx files should follow the standard 8.3 DOS format (ie. don't use more than eight characters). The text inbetween the quotes can be as long as you like, within reason. I found it better not to include the kernel version, preferring to leave that for the [hidden] Grub menu that follows. Something short works best.


When you've finished adding distro's, you should hide the BOOT.INI file again with the command:

```
attrib +h +s +r BOOT.INI
```

After restarting, you should be presented with the Windows boot loader screen, like this:

```
Please select the operating system to start:

Windows XP Pro
Ubuntu Linux
Kubuntu Linux
Edubuntu Linux
Xubuntu Linux
Fedora Linux
openSUSE Linux
Mandriva Linux
Debian Linux
Gentoo Linux
Linspire Linux

Use the up and down arrow keys to move the highlight to your choice. Press ENTER to choose.
```

Select the distro you've just installed, and it's boot loader should start up. By removing the # character in front of the hiddenmenu command (in the menu.lst file), it's menu options won't be displayed. If you want to see them, quickly press the ESC key (you will only have 3 seconds to do this!). You can then boot into recovery mode or run the memtest86+ utility.

The advantage of using the Windows boot loader to control everything, is that in every day use you will only see the one boot menu - which is more elegant than going through two or possibly three (if you have Vista installed as well... but that's a whole other nightmare!)

Verify that your chosen distro boots up as expected, then proceed to install as many other distros as you'd like, in a similar fashion.

Note: if you ever find you can't boot into Windows, you might need to activate the [first] Windows partition. Using Norton Ghost's GDISK.EXE utility, this can easily be done with the command:

```
GDISK /1 /ACT /P:1
```

{END}

---

### Post by quixotic on 2006-10-01
This howto was the closest I have gotten to successfully hand off to Grub from ntldr.

I have a laptop that everytime I boot windows overwrites the MBR and then to switch back to Xubuntu I must do a Grub restore to MBR.  Quite a hassle.  Tried your howto twice.  Both times same result.  This is the current configuration.

HDA1 XP
HDA2 fat32 windows datashare partition
HDA3 /boot
(logical) HDA5 /
(logical) HDA6 /home
(logical) HDA7 swap

First time had both /boot and / patitions logical as in your howto.

I can boot into windows
I can start grub from the menu in boot.ini and choose from the grub menu.lst
BUT
Grub hangs after the following message.

Booting 'xubuntu, kernel 2.6.15-23-386 root (hd0,2)
Filesystem type is ext2fs, partition type 0x83
Kernal /vmlinuz-2.6.15-23-386 roo=/dev/hd5 ro quietsplash
[Linux-bzImage, setup=0x1c00, size=0x15774d]

The cursor just flashes and flashes.
Any ideas??

Thanks

---

### Post by randallsell on 2006-11-06
Well, your instructions work well, up until the point that you need to change the /boot/grub/menu.lst. I don't have super user access, so I can't change it.

So how do I:
1) change my account, so it is granted supervisor rights
or 2) login as su. I don't recall the Ubuntu installer asking me a "master" or super user pw. Is there some default password created by the installer that only Unix savey people know about?

or 3)
Is their a GUI tool that would allow me to modify it, other then gedit? What I mean is, is their an application specifically designed, like MS did, that allows me to modify the grub loader menu? I am happy at this point, to have it default to the "Other Windows 2k/xp login but don't know how to change that.

regards,
-randall

---

### Post by duncanb on 2007-01-26
Thanks for the instructions which worked well for me, except I was able to take a slight shortcut:

In step 3 after setting up the partitions but before doing the install Ubuntu 6.1 (don't know about earlier versions) has a confirmation screen which says Grub will be installed to (hd0). I changed this to point to the grub boot partition (in my case /dev/sda6). When the installation was completed I told it not to reboot immediately, and then created the ubuntu.lnx file while still in the live cd which I then copied onto a USB flash drive. Then I skipped the rest of steps 4 and 5 booted back to Windows and continued from step 6.

---

### Post by Chopperman on 2007-03-07
Sorry about dredging up an older thread. I didnt get a lot of response yesterday :)

My system:
HP dv9010US laptop. 
2 SATA hard drives: first drive Windows XP, second drive Ubuntu Edgy.

Why I want to use windows boot menu:the laptop features booting to DVD or cdmedia that is inserted and then controlled via remote. I want to retain that function. I gather it uses a hidden partition, so maybe that is why it is required and possibly the source of my problem?

What I have done:
deleted my beautiful and carefully crafted Ubuntu install and used alternate cd to install anew.  I then told it to put GRUB on the second hard drive where linux is. 

(HD1,0) SDB1

following various tutorials I used dd to make a bin file to use on the windows disk

Sudo dd if=/dev/sdb1 of=linux.bin bs=512 count=1

I then copied it to the root folder of my windows C:\ drive and added c:\linux.bin "Linux yay!" to the end of the boot.ini

on boot I get the expected menu showing windows and linux. When I select linux, I get GRUB with a flashing underscore prompt and an unresponsive system. This tells me that windows is dutifully handing off for the boot...but that the .bin file is not filling its end of the deal and handing off to GRUB on SDB1. 

I will try it with the different extension noted here, but I dont suppose that makes a difference. 

Any ideas what else I could do? I would rather not use ultimate boot cd to boot off the second drive. that feels...ineligant. 

I am open to thoughts. I am a linux noob, but not new to computers

---

### Post by jag164 on 2007-03-14
I have the exact setup on my 2 hd dv9010us except I use fedora instead of ubuntu.  Anyway, I stumbled upon this thread here so I might as well try to help.

    I had the same issue with GRUB at stage 1.5 as you have.  I kept trying different things until I tried to boot one time and noticed my USB key flashing.   Unplugged it and GRUB booted right up.  Plugged it back in after grub launched the boot process and all is well.   It's either a grub bug or a HP Bios bug.   The key only needs to be out for a brief period.

---

### Post by Coburn on 2007-03-15
One thing--

I had XP on a second disk that I crippled by using GPartEd wrong.   I never even took it off Grub--just left it.  

But today I tried to restart from Dapper and got the error:

"No NTLDR:
Press any key to restart."

What it was, was I had left a floppy in the drive!  :lolflag: 

Took out the floppy, and there was my cheerful Gnome again.

so beware.

---

### Post by Genecks on 2007-03-18
A suggestion: ALWAYS make a backup of your most precious files before ever screwing with the hard drive. I know it was said here, but it seemed more implicit than explicit.

---

### Post by Coburn on 2007-03-22
Like the MBR?

OK, back to topic, guys!

---

### Post by miguev on 2007-04-06
Nearly! :)

After many tries this howto was the best solution I found, it nearly did the job!

This is what I get when I try to boot linux from NTLDR:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\ntoskrnl.exe
Please re-install a copy of the above file.

The line in boot.ini is:
c:\bootsect.dat="Ubuntu"

Got any clue?

Thanks!

---

### Post by Azfar on 2007-04-11
Hi,
    I have the same problem as Chopperman had; I can select Ubuntu from ntldr menu after which it shows GRUB**_** and the cursor keeps blinking indefinitely.

I have the following disk config:
/dev/hda1   Primary Boot WinXP
/dev/hda5   Logical
/dev/hda6
/dev/hda7
/dev/hdc1   / (this is the root, I have not made a boot partition) Primary
/dev/hdc2   swap
/dev/hdd1   /media/fat32

I installed GRUB *sudo grub-install /dev/hdc1*.
In the menu.lst file root was (hd1,0).

Any suggestions?

---

### Post by super-coder on 2007-04-11
I have had this problem too.

I think the wrong data was copied for the bootsect.bin

---

### Post by super-coder on 2007-04-11
I had this problem once.  The situation was as follows:

HDA1 WindowsXP
HDA2 FAT32 (for file transferring between linux and windows)
HDB1 ext3 ( / for PCLinuxOS .93)
HDB2 ext2 ( /boot for PCLinuxOS)

I reinstalled XP and copied my bootsector data ("linux.bin") to the root of win_c.  I then right clicked "My Computer" in XP and edited the boot.ini through startup and advanced options.  

I rebooted my machine and XP loaded fine.  When i tried to boot PCLinuxOS i received the error: 

[INDENT]Windows could not start because the following file is missing or corrupt:
C:\system32\ntoskrnl.exe
Please re-install a copy of the above file.[/INDENT]

The problem was that when I reinstalled XP I did not reformat the FAT32 partition.  Windows Setup must have "renumbered" HDA2 to be HDA1.  I found my "boot.ini" and "ntoskrnl.exe" had been placed on the FAT32 partition.  I placed my "linux.bin" file on the FAT32 partion and Linux booted just fine.

I hope this helps in your situation.

---

### Post by fulanodetal316 on 2007-06-16
I think I am missing something, when I went to create the back-up of the MBR the windows ultility failed repeatedly. Thanks to a rather helpful posting I found that I could get the same results from the LiveCD with this code:
considering that hdd1 is the partition with the master boot record in the front

```
sudo dd if=/dev/hdd1 of=MBR-Backup bs=512 count=1
```

The utility disk was not totally useless, it told me the hex values of the last 2 values in this file would be 55AA if it was actually the MBR. Having done that I continued on until I got to the part about restoring the MBR. Unfortunately the boot cd also failed to perform so I loaded up the LiveCD once more to reverse the process with this code:

```
sudo dd if=MBR-Backup of=/dev/hdd1 bs=512 count=1
```

Unfortunatly, even though GRUB was moved to the boot partition (which I had dutifully created a file from and checked to confirm that it actually had been installed correctly to the partition) it stubbornly continues to boot straight to GRUB and will not allow me to return to windows.

I think that I have missed something, does anyone have any suggestions?

---


---
title: "Installation error and Grub error with 11.10"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by Snader on 2011-10-27
Hi there. Thanks for your interest.

I tried to replace Ubuntu 10.10 with a clean installation of Ubuntu 11.10 on a dual boot machine. Both 32-bit and 64-bit installation CDs for Ubuntu 11.10 crash into a black screen with a white cursor before it should present the "try Ubuntu" and "Install Ubuntu" options.

Using a bootable USB stick I'm able to start and finish the 64-bit installation. However, when booting the PC afterwards, instead of GRUB I get the following error: "error: invalid arch independent ELF magic" with a grub rescue command line. Boot-repair was not able to solve this error.

My system has EFI.

PC Specifications:
Packard Bell iXtreme i6803
Intel i5 2300
MSI R5670-PMD1G/OC
4GB DDR3
1TB HD

Thanks in advance for your help.

---

### Post by Snader on 2011-10-27
GRUB (and therefore Ubuntu and Windows) is working again after replacing the broken Ubuntu 11.10 with a clean installation of Ubuntu 10.10.

I'll keep Ubuntu 10.10 until I find a solution in this topic or on the forums. Or... until Ubuntu 12.10. ;)

---

### Post by MorrisseyJ on 2011-10-29
Hi, 

I had the same problem using a Thinkpad x121e [Intel i3] (which, it seems, also has an EFI) and installing on 64 bit architecture. 

I install 11.10 and everything goes fine. I then reboot. GRUB doesn't come up and instead i get:

> 
error: invalid arch independent ELF magic
grub rescue >

This problem appears to be all over the place. From what i can see you have to install grub-efi to get things to work. 

My question though is how do you do this? When i am running the live USB, how do i get grub-efi to install to the hard drive, and not to the USB. If i have to mount a partition and make it install there, could someone please tell me:

1. How to do this, and 
2. to which partition it should be installed?

Thanks,

---

### Post by raja.genupula on 2011-10-29
Login in to which ubuntu you wanna keep and then open your terminal.

type this 

```
sudo dpkg-reconfigure grub-pc
```
install the grub to whih partition you want . 

All the best.

---

### Post by oldfred on 2011-10-29
I have saved some info & links.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by MorrisseyJ on 2011-11-01
Thanks for the responses. Unfortunately i am not very technical with the GRUB stuff and the partitions. 

I am now on a slow internet connection and i am loath to try and install 11.10 again, have it fail and have to revert back to 11.04. Each install will take about a day, before i start downloading all the programmes i need. 

So, i could use a little hand-holding to make sure i get this right, if that's ok.

In this regard, raja:

You want me to type: 

```
sudo dpkg-reconfigure grub-pc
```At the ```
grub rescue > 
``` prompt?

Then, raja and oldfred; when you say i must > install GRUB the  to the ESP (EFI SYSTEM PARTITION), what do you mean?

Here is a list of my partitions, working from 11.04. I would like to install 11.10 into the same partition as 11.04 is on now.

```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3da24a9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             154        6788    53292032    7  HPFS/NTFS
/dev/sda3           37384       38914    12288000    7  HPFS/NTFS
/dev/sda4            6788       37384   245758977    5  Extended
/dev/sda5            6788       36350   237458432   83  Linux
/dev/sda6           36351       37384     8299520   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-0: 8498 MB, 8498708480 bytes
255 heads, 63 sectors/track, 1033 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb877af28

Disk /dev/dm-0 doesn't contain a valid partition table
```
With this in mind what do i type to install GRUB to the correct partition? and where do i type it: at the 'grub rescue >' prompt, in a terminal on the live USB, or somewhere else?

Finally, can someone explain why the EFI system is giving problems on 11.10 and not on 11.04 - which installs and boots fine. I would have thought this stuff would have been improving in subsequent versions of Ubuntu. I ask not out of criticism of 11.10, but to make sure that it is the EFI which is the problem.

Thanks in advance,

---

### Post by Hakunka-Matata on 2011-11-01
The first three steps in the previous post (# 5), details what is required.
fdisk shows 4 primary partitions exist already on your drive.   (4 is maximum # of primary partitions allowed on MBR drives, right?)
In order to make a ESP (EFI SYSTEM PARTITION), you'll need to delete one of the existing ntfs partitions.  
You'll then have to make a new sda1 partition, of type (EFI SYSTEM PARTITION) as described in post # 5.
Once you have a (EFI SYSTEM PARTITION) and you installing 11.10, the installer will allow you to install grub to sda1, PBR.  By default the installer will choose to install grub to the MBR of sda, not to sda1, so you need to change that in the installer screen.

---

### Post by oldfred on 2011-11-01
Just becuase newer systems are EFI, they also have a BIOS mode for compatibility. 
If booting Windows in UEFI mode you have to have a gpt partition table and an efi partition. You have neither as you have a standard MBR(msdos) partition table and no efi partition. So you have to be booting in BIOS mode.

Then all you have to do is install grub2's boot loader to the MBR. Some BIOS have ways to 'lock' the MBR so check you settings to see if that is an issue.

IF you are at a grub rescue prompt then you may be able to manually  boot. Or you can use one of several repair tools.

Manual boot (# are comments):
#grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
#or
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Sidenote:
It should not take all day to reinstall. I have it down to about an hour but have installed many times and have high speed internet, so I know several short cuts. I install from one hard drive to another, so the actual install is quick, I save a list of installed applications, so reinstalling those is relatively quick and all my data is in other partitions that I just remount via editing fstab which I have automated with scripts.  I do not have the separate /home (which is normally recommended), but install to another 25GB / (root) partition so I can copy settings from my old system if desired.

---

### Post by MorrisseyJ on 2011-11-01
Thanks for all the help. 

I am convinced that i can now do this. That said, i might just have to wait until i am on a faster internet connection. 

Oldfred: that's the problem with installing. I am in Ethiopia at the moment and just trying to pull down the iso looks like taking 2 hours. Installing and updating the new install will take forever. 

Thanks again for the advise. Like i said, i am now convinced that this will work.

---

### Post by Snader on 2011-11-02
Thanks for all the help everybody. And MorriseyJ, thanks for keeping this thread alive. You seem to have asked the right questions to get the information we both needed.

Maybe this evening I will try to install Ubuntu 11.10 and afterwards I will report my findings in this thread.

---

### Post by Snader on 2011-11-02
Three last questions. Is any of the information given to MorisseyJ not applicable to me, because our partition tables are different? My partition table is included in the attachments.

Following from my partition table, I would say that this so called ESP you are talking of is on my sda2. Could any of you confirm that to me? According to post #5, my ESP needs to be on the first partition of the drive. Is there a way to arrange this without erasing my Vista recovery partition?

Again, your help is greatly appreciated!

---

### Post by oldfred on 2011-11-02
It looks like your sda1 is a Vendor recovery or an image of your drive as you purchased system. You should make recovery DVD's from this as when hard drive totally fails you cannot recover it from a broken drive. Also to restore to like new if you want to sell it someday.

Better to have a full backup.
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

But nether a recovery set of DVDs or backup is a repair disk. So you should make a Windows repairCD. Whenever changing systems around you want a current repairCD or Linux liveCD to be able to make fixes. I also have a few other Linux repair ISO  just in case.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Your sda2 is a Windows boot/recovery partition. It boots Windows and has the windows repair tools that you can get to with f8 if system is partially working.

Your sda3 is your main Windows or c:.

You are using BIOS to boot, so you do not need an efi boot partition. That is only required with UEFI boot. Windows in UEFI also creates another boot partition in UEFI mode as well.

Your partition layout looks just fine.

This is why two users with boot issues should be in different threads as the details are almost always different. It gets confusing for everyone on which answer is correct for who.

---

### Post by Snader on 2011-11-04
> **oldfred said:**
> This is why two users with boot issues should be in different threads as the details are almost always different. It gets confusing for everyone on which answer is correct for who.
Thanks for your help and especially for explaining my partition table in detail. I believe that I can put that to good use. However, I am indeed getting a bit confused regarding the solution to my problem.

From post #8 and #12 I conclude that MorriseyJ and I are both using BIOS to boot. Does this mean that I can also solve my problem using the procedure which is suggested in post #8? Could you especially take a close look to the given grub rescue commands for me please?

On a sidenote: Boot-repair was already used by me to no avail. Then, will this manual boot solve my problem? And, is this manual boot a permanent solution or do I need to repeat this procedure every time I boot?

Thanks for your help!

---

### Post by oldfred on 2011-11-04
If you can manually boot, then you reinstall grub to the MBR from inside Ubuntu. That almost always works then.

You can often use Supergrub to boot an otherwise correct Ubuntu install. Boot repair will often restore a broken MBR. And reinstalling grub2's boot loader using a liveCD usually works, but sometimes other fixes are needed and you have to chroot into your system, make fixes & reinstall grub2. So depending on what works you can usually repair, some just give up & reinstall as that is sometimes a cure also. But if you are really booting (often blank screen not grub rescue) and it is a video issue or other boot parameter, reinstall will not fix that. Lots of choices.

Have you posted latest boot info script or from boot repair a new run of boot info script and the link to it? What beside boot repair have you tried and where is it failing?

---

### Post by MorrisseyJ on 2011-11-04
Hi Oldfred,

Thanks for helping us through this. 

Sorry to have crowded in on this thread. I didn't realise these things were so specific. If i have any future boot problems i'll start a dedicated thread. 

j

---

### Post by Snader on 2011-11-05
Unfortunately, I'm stuck again.

Today I gave the installation of Ubuntu 11.10 64-bit another try. The installation again failed to boot using a CD, although there were no errors detected on the image. Therefore, I again installed an image to a USB-drive via the Universal USB Installer and I used that for the installation. After the installation, GRUB fails with the well-known error: "error: invalid arch independent ELF magic". So, nothing new up to here.

Unfortunately, the Super Grub Disk fails:
```
Welcome to GRUB!

error: hd32 cannot get C/H/S values.
Entering rescue mode...
grub rescue>
```

Also, my attempt at a manual boot fails:
```
grub rescue> ls
(hd0)
grub rescue> configfile (hd0)/boot/grub/grub.cfg
Unknown command 'configfile'

```

```
set prefix=(hd0)/boot/grub
set root=(hd0)
linux (hd0)/vmlinuz root=/dev/sda5 ro
Unknown command 'linux'

```

All your help is appreciated!

---

### Post by oldfred on 2011-11-05
Post boot script from liveCD or USB:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

And if you have efi or might have efi post this:

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

---

### Post by Hakunka-Matata on 2011-11-05
You may use the attached **makeresults.sh file **to download, run, generate RESULTS.txt on Desktop, open RESULTS.txt with gedit, and it leaves you there to highlight and copy the text into a fresh reply.
If you want to make it really painless, add these codes while in gedit, 
add [ code] at the very beginning of the file (without the extra space)
add [/ code] at the end of the file, (without the extra space) 

then simply copy the whole thing and paste it into a reply

Run **makeresults.sh **from the Terminal with code:
```
sudo bash makeresults.sh
```from the directory to which you download the script file.

---

### Post by MorrisseyJ on 2011-12-01
I have just managed to find myself on a decent internet connection for a while and so am trying this. 

Not sure if its best to transfer this to a new post given the previous comments of Olffred about the specificity of boot problems, but thought i'd keep it all here until this issue is resolved.

So:

From Post # 8, from Oldfred
> IF you are at a grub rescue prompt then you may be able to manually  boot. Or you can use one of several repair tools.

Manual boot (# are comments):
#grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see  (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
#or
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

At 
> grub rescue>
ls, gives:
> (hd0) (hd0, msdos6) (hd0, msdos5) (hd0, msdos3) (hd0, msdos2) (hd0, msdos1)

I am thus not sure what to do from here as none of this looks like what was mentioned above. If anyone has any ideas that would be great. My access to a decent internet connection is also time bound so i need to get this sorted sooner rather than later - if nothing can be worked out i'll revert to 11.04.

Thanks

---

### Post by oldfred on 2011-12-01
If you know what partition you installed to use that, otherwise search for the one with grub. Use each of the 0,1 thru 0,6 but it is often sda5 that you install to so ls(hd0,5)/boot?

ls (hdX,Y)/boot    
Display the contents of the /boot folder. Example: 
ls (hd0,5)/boot

ls (hdX,Y)/boot/grub    
Display the contents of the /boot/grub folder. Example: ls (hd0,5)/boot/grub

---

### Post by MorrisseyJ on 2011-12-02
Hi Oldfred, thanks for following this up.

I managed to solve this with by booting to the live cd and running the following in the terminal:
> 
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdaI found it on an ask ubuntu page, where someone had the exact same partitions as i did. 

I am not sure if this can be reported somewhere so that it gets dealt with in the LTS release. Any ideas?

---

### Post by oldfred on 2011-12-02
Glad you got it working.

The reinstall command has been changed for grub 1.99, but the older version is supposed to still work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Some also like automated tools.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---


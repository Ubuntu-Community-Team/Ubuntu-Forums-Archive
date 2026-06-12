---
title: "Having issues making a bootable USB for 20.04 LTS"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by bc-uk on 2020-05-29
I have a Win10 machine that I want to use Ubuntu 20.04 LTS on. Using the 20.04 LTS bootable installer running on a USB stick, I was able to install onto a second 256GB USB stick. However, it won't boot, it just boots straight to windows. I  have the USB stick selected to boot first in the boot priority in BIOS settings. My boot priority is set as follows:

 1 - uefi: usb disk 3.0 pmap, partition 1 (236581mb)

  2 - Windows Boot Manager (samsung ssd 960 evo 1tb)


 I tried installing onto the USB stick two ways - one with LVM active, and one without , but neither  will boot. I've also disabled Fast Boot in the BIOS, but still no joy. Anyone have any ideas?

One other side issue - since installing onto the USB, my boot priority menu has the following as an option - 'ubuntu (samsung ssd 960 evo 1tb)'. I only have one SSD installed on my machine, and it shows up twice in the options for boot order - 'Windows Boot Manager (samsung ssd 960 evo 1tb)' and 'ubuntu (samsung ssd 960 evo 1tb)'. I tested, and Windows still works fine. Anyone know why the ubuntu option is there?

---

### Post by sudodus on 2020-05-29
Please describe how you created an Uuntu system the second 256GB USB stick.

- Installed system or a [persistent] live system?
- Which tool/method did you use?
- Can you still boot from the first USB stick?

---

### Post by bc-uk on 2020-05-29
I installed the ubuntu bootable installer onto a 16GB USB stick using rufus. I then booted the installer, selected the "Try Ubuntu" option, then used the installer option that's on the ubuntu desktop. I then went through the installer, using the auto partition option "Erase disk and install ubuntu". I tried this twice - once with LVM, and once without, neither worked. The USB stick I tried installing onto is 256GB. When I view it using the Windows Disk Management application, it shows as having two partitions: 1: 512MB EFI System Partition, 2: 230.54GB Primary Partition. Both partitions report as "healthy".

---

### Post by bc-uk on 2020-05-29
This is the USB stick I used: [https://www.amazon.co.uk/dp/B07RT1WMFB/ref=twister_B07SNQVHWC?_encoding=UTF8&psc=1](https://www.amazon.co.uk/dp/B07RT1WMFB/ref=twister_B07SNQVHWC?_encoding=UTF8&psc=1)

---

### Post by sudodus on 2020-05-29
1. Try by creating a live drive on the 256 GB USB drive with Rufus. If you wish, you can make a persistent live drive. If it boots, you know, that the 256 GB USB drive can be used to boot your computer.

2. When you know this, you can install into this drive according to the following links:

[Stepwise instructions](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

[Full Install to USB - BIOS/UEFI](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers)

---

### Post by ubfan1 on 2020-05-29
Disabling "Fast Boot in the BIOS" just makes it easier to push the  function buttons in time at power-up. The option you want to disable is in the Windows Power options, hidden... advanced,  ... really hidden, but when you find the choice, turn off Quick startup"  (or fast boot or whatever it's called).  that will then allow a normal boot to occur.
  Now, the USB to USB install, unfortunately still has bugs. See 1173457,1396379,1702335.  Basically, the grub boot files get written to device sda instead of your (maybe even selected by you as location for bootloader) USB.  Fix the USB (since it already has an EFI partition) by just copying all the files from the sda EFI to the UEF efi.  Then it should boot by selecting it in the EFI menu (some function key at power-up like maybe f10 or f12).  The real problem is that your machine when it does a real boot, has grub spread from sda to the USB, and grub will fail without the USB present. See the bugs for corrections, add yourself to the "does this affect me" list on the bug(s).  Booting the sda by default, and the USB by device choice from the EFI when present should work for you.

---

### Post by bc-uk on 2020-05-29
> **ubfan1 said:**
> The option you want to disable is in the Windows Power options, hidden... advanced,  ... really hidden, but when you find the choice, turn off Quick startup"  (or fast boot or whatever it's called).  that will then allow a normal boot to occur.

If this was the problem, wouldn't it also prevent the USB ubuntu installer from booting as well?

---

### Post by ubfan1 on 2020-05-29
No, the USB installer is typically first in the boot order.  If a hard disk boot is attempted and Windows is hibernated, a normal boot does not occur, and the hibernated state is restored.

---

### Post by bc-uk on 2020-06-13
> **sudodus said:**
> 1. Try by creating a live drive on the 256 GB USB drive with Rufus. If you wish, you can make a persistent live drive. If it boots, you know, that the 256 GB USB drive can be used to boot your computer.

2. When you know this, you can install into this drive according to the following links:

[Stepwise instructions]("https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312")

[Full Install to USB - BIOS/UEFI]("https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers")

I followed the stepwise guide, and with my SSD detached ubuntu booted fine from my new USB installation. During installation I set it to log me in automatically, and it did so when it booted. I then reattached the SSD, changed the BIOS to boot from the USB first. Ubuntu boots up from the USB as expected, however, it's now displaying a login screen instead showing my name. When I click my name, it asks for a password. When I enter my password it just goes back to the login screen displaying my name. When I enter an incorrect password, the password box shakes and I get an incorrect password prompt. When I enter the correct password it just goes back to the login screen showing my name.

---

### Post by bc-uk on 2020-06-13
I tried setting the SSD to Disabled in the BIOS Boot Options. I did this in case the 'ubuntu (Samsung SSD 960 EVO 1TB)' partition (that was created on the SSD when I first tried to install onto USB) was causing issues. However, it looks like it tried to boot from the USB, some message quickly flashes up (too fast to read), PC resets, then boots into ubuntu, but still can't login.

---

### Post by sudodus on 2020-06-13
This is contrary to my previous experience (from older versions). But I believe what you write.

Something must have changed, that causes confusion. Grub should use UUID to identify the partitions to use, they should be unique, and this should make the selection of partitions correct, so that the internal drive should not disturb the process. Maybe, if you boot in UEFI mode, there is something new, where the device name '/dev/something' is involved instead of the UUID.

(Or, the computer does not really try to boot from the USB drive, even though it looks like that.)

---

### Post by bc-uk on 2020-06-13
Yes, I'm guessing that GRUB on the SSD is what's causing the problem if the USB boots fine and logs me in when the SSD is not connected. Is GRUB on the Win10 partition, or is it on its own partition? Eitherway, do you think deleting GRUB from the SSD will fix my issue? It's only on the SSD because I left the SSD connected when I initially attempted to insall ubuntu onto a second USB stick.

---

### Post by bc-uk on 2020-06-13
Here's a simple guide I found to remove GRUB: [https://gist.github.com/henrytriplette/bc5ec3742896e36503b9a99d0940a4e4](https://gist.github.com/henrytriplette/bc5ec3742896e36503b9a99d0940a4e4)

Does that look correct / safe?

---

### Post by sudodus on 2020-06-13
Grub in the internal drive is in a separate partition (the Ubuntu root partition or the Ubuntu boot partition, if you made it that way, definitely not in a Windows partition. But if you remove it, I am afraid that Windows will not boot. That can be repaired, but it *should* work according to what I described earlier even with grub in the internal drive.

---

### Post by ubfan1 on 2020-06-13
That guide will remove the grub files, but you should first remove the EFI menu entry with efibootmgr.  See the entries with efiboogmgr -v  ,  then remove the grub entry (read the man page for efibootmgr for the options for removal).  Did you try to login with a virtual terminal, your login problem may be gui related.  Check this site and askubuntu for "lgin loop".

---

### Post by sudodus on 2020-06-13
> **bc-uk said:**
> Here's a simple guide I found to remove GRUB: [https://gist.github.com/henrytriplette/bc5ec3742896e36503b9a99d0940a4e4](https://gist.github.com/henrytriplette/bc5ec3742896e36503b9a99d0940a4e4)

Does that look correct / safe?

I don't know, have not tried it, but it looks good to me.

If you have a full backup of the whole Windows system, you can try it. (You should have a full backup anyway, for example by Clonezilla, for several reasons.)

---

### Post by bc-uk on 2020-06-13
Would installing ubuntu onto a second SSD and making my system duel boot be easier at this point? I've already wasted a huge amount of time on this and don't think I want to risk messing up my existing Win10 installation. Having the USB installer create a partition on the SSD when I explicitly indicated that I wanted to install onto a second USB device was already a scare I could have done without. Thank god it doesn't interfere with Win10.

---

### Post by oldfred on 2020-06-13
Ubuntu's Ubiquity installer only installs grub boot loader to first drive seen, usually the Windows drive.
Most suggest unplugging or in UEFI settings temporarily disabling Windows drive, so install drive is then first.

If not disabling drive, you must partition in advance to have an ESP on second drive and do a work around either before install as in bug report or after install by copying files into external drive's ESP from internal drive's ESP.

       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)

---

### Post by C.S.Cameron on 2020-06-13
Sounds like your permissions for home might have got messed up.
If I recall correctly doing a ```
sudo chown -R username username /home/username
``` from a Live USB, fixed things for me.
This should be confirmed before attempting it, I have not tried it in a while.

If that does not work for you, I have had good luck making a Full install USB that works both BIOS and UEFI using the method on this page: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by oldfred on 2020-06-14
C.S.Cameron means you to type your username in not use "username"

But you can have system provide your user name.  If you want all lower level directories change also add the -R parameter. Note, do not run on any other system directly as there are multiple different system owners as well as root for various directories.
man chown
       sudo chown $USER:$USER /home/$USER 

To see name
echo $USER

To see users:
fred@bionic-z97:~$ id
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

---

### Post by C.S.Cameron on 2020-06-15
Thanks oldfred
I see I wrote down "**sudo chown -R username:group directory**"
But I did not write down why I wrote it down.
But I do remember something like that saved me from a bad password login loop.

---

### Post by bc-uk on 2020-06-15
Just to clarify before I try that, do I change all instances of  'username' to my actual username? E.g. if my username was user1, it  would be:

sudo chown -R user1 user1 /home/user1

Is this  going to fix the problem on the SSD or the bootable USB I created? Do I  need the bootable USB to be also plugged in as well as the Live USB I  booted from to load Terminal?

---

### Post by bc-uk on 2020-06-15
Also, can I use the same username I original specified when I originally installed, or do I have to use a different username?

---

### Post by C.S.Cameron on 2020-06-15
If you are still having the password problem I would use the original username for user1 and if you are chowning the USB, I think you need to give it's path to home, if you are working from a second Live USB.
ie

sudo chown -R user1 user1 /media/user1/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/user1

where user1 is the username and xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is the UUID of the USB

Please confirm this before proceeding

---

### Post by bc-uk on 2020-06-15
Yes, I have the Live USB booted and have a terminal open, and have just plugged in the bootable installation I created in the second USB slot. The bootable USB installation has folders home/username on it.

---

### Post by bc-uk on 2020-06-15
OK, I tried it, and got the error: chown: invalid user: 'bc'

'bc' is the username I created when creating the bootable USB. On the bootable USB installation, the following folders exist:

home/bc
media/bc

The one in the media folder has a red checkmark icon on it.

---

### Post by C.S.Cameron on 2020-06-15
So your command was "sudo chown -R bc:bc /media/bc/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc" ?

---

### Post by bc-uk on 2020-06-15
Yes. I tried with and without the colon (examples in posts above yours  don't include the colon) but it reports the same error: chown: invalid  user: 'bc'

---

### Post by bc-uk on 2020-06-15
Just to confirm - the USB UUID is the ID that is shown in the Name field when viewing the Properties for the USB device? That's the UUID I'm using in the chown command.

---

### Post by ubfan1 on 2020-06-16
bc is a username on your installed Ubuntu, not on the live media.  Look at your installed /etc/passwd file and get the numbers after the ': x :'  on the line starting with the bc name.  use those numbers in the chown instead of bc, probably they are 1000:1000 if bc is your first created user.

---

### Post by bc-uk on 2020-06-16
> **ubfan1 said:**
> bc is a username on your installed Ubuntu, not on the live media.
Yes, I'm aware of that.

> **ubfan1 said:**
> Look at your installed /etc/passwd file and get the numbers after the ': x :'  on the line starting with the bc name.  use those numbers in the chown instead of bc, probably they are 1000:1000 if bc is your first created user.
I checked the passwd file and the number for bc are 1000:1000, so I did this:

sudo chown -R 1000:1000 /media/bc/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc

But got the error: chown cannot access '/media/bc/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc': No such file or directory

I'm using the actual UUID for the USB with the installation on it, and not 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'.

---

### Post by C.S.Cameron on 2020-06-16
I think so, if while booted from a live USB, you copy the folder /bc in /home from the Full install USB and paste it in Text Editor, you should get the path:
/media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc

Ahh, The previous path I gave was the path from another Full install USB, not from a Live one. From a Live USB the user ubuntu is in the path. sorry.

sudo chown -R bc:bc /media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc

If that doesn't work probably should PM sudodus or oldfred.

---

### Post by bc-uk on 2020-06-16
> **C.S.Cameron said:**
> I think so, if while booted from a live USB, you copy the folder /bc in /home from the Full install USB and paste it in Text Editor, you should get the path:
/media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc

Ahh, The previous path I gave was the path from another Full install USB, not from a Live one. From a Live USB the user ubuntu is in the path. sorry.

sudo chown -R bc:bc /media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home/bc

If that doesn't work probably should PM sudodus or oldfred.

This worked, insofar as the command was accepted without error. However, when I try rebooting from just the installed USB I'm getting the same behaviour as before - password is accepted (no incorrect password error shown) but it just goes back to the login screen.

---

### Post by C.S.Cameron on 2020-06-16
Seems to be working for me also, at least permissions are changing. does it make a difference if there is a slash after the last bc?

or you type:

sudo chown -R bc:bc /media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home

---

### Post by bc-uk on 2020-06-16
> **C.S.Cameron said:**
> Seems to be working for me also, at least permissions are changing. does it make a difference if there is a slash after the last bc?

or you type:

sudo chown -R bc:bc /media/ubuntu/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home

Tried both those options, but still not able to login.

---

### Post by sudodus on 2020-06-16
Let us go back and start at a more basic point in order to get a better understanding of your problem.

- Please boot into a live drive, not the 'installed system in a USB drive' but the live system in a smaller USB drive.

- When at the desktop (when the live system is running)
. check that the internal SSD drive is fully connected and activated
. connect the problematic 'installed system in a USB drive' 
.start a terminal window, expand it to full screen and run the following commands:
```

sudo parted -ls
sudo fdisk -lu
sudo lsblk -f
sudo lsblk -m

```

- Copy and paste the output of the commands from the terminal window to a reply box here (in this thread).

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

in order to make the output easier for us to read.

---

### Post by bc-uk on 2020-06-16
```
ubuntu@ubuntu:~$ sudo parted -ls
[COLOR=#000000][FONT=Calibri]Model: Samsung Flash Drive FIT (scsi)

Disk /dev/sda: 257GB

Sector size (logical/physical): 512B/512B

Partition Table: msdos

Disk Flags: 



Number  Start  End    Size   Type     File system  Flags

 1      131kB  257GB  257GB  primary





Model: Samsung Flash Drive FIT (scsi)

Disk /dev/sdb: 257GB

Sector size (logical/physical): 512B/512B

Partition Table: msdos

Disk Flags: 



Number  Start  End    Size   Type     File system  Flags

 1      131kB  257GB  257GB  primary





Model: Kingston DataTraveler 3.0 (scsi)

Disk /dev/sdc: 15.5GB

Sector size (logical/physical): 512B/512B

Partition Table: msdos

Disk Flags: 



Number  Start   End     Size    Type     File system  Flags

 1      1049kB  15.5GB  15.5GB  primary  fat32        boot, lba





Model:  USB DISK 3.0 (scsi)

Disk /dev/sdd: 248GB

Sector size (logical/physical): 512B/512B

Partition Table: gpt

Disk Flags: 



Number  Start   End    Size   File system  Name                  Flags

 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp

 2      538MB   248GB  248GB  ext4





Model: Samsung SSD 960 EVO 1TB (nvme)

Disk /dev/nvme0n1: 1000GB

Sector size (logical/physical): 512B/512B

Partition Table: gpt

Disk Flags: 



Number  Start   End     Size    File system  Name                          Flags

 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag

 2      524MB   628MB   104MB   fat32        EFI system partition          boot, esp

 3      628MB   645MB   16.8MB               Microsoft reserved partition  msftres

 4      645MB   1000GB  1000GB  ntfs         Basic data partition          msftdata





ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/loop0: 1.93 GiB, 2049204224 bytes, 4002352 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/loop1: 27.9 MiB, 28405760 bytes, 55480 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/loop3: 240.82 MiB, 252493824 bytes, 493152 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes





Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors

Disk model: Samsung SSD 960 EVO 1TB                 

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: gpt

Disk identifier: 84208044-0960-4CFB-8FE6-3D0FB61EEE8E



Device           Start        End    Sectors   Size Type

/dev/nvme0n1p1    2048    1023999    1021952   499M Windows recovery environment

/dev/nvme0n1p2 1024000    1226751     202752    99M EFI System

/dev/nvme0n1p3 1226752    1259519      32768    16M Microsoft reserved

/dev/nvme0n1p4 1259520 1953523711 1952264192 930.9G Microsoft basic data





Disk /dev/sda: 239.2 GiB, 256641603584 bytes, 501253132 sectors

Disk model: Flash Drive FIT 

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x00000000



Device     Boot Start       End   Sectors  Size Id Type

/dev/sda1         256 501253099 501252844  239G  7 HPFS/NTFS/exFAT





Disk /dev/sdb: 239.2 GiB, 256641603584 bytes, 501253132 sectors

Disk model: Flash Drive FIT 

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x00000000



Device     Boot Start       End   Sectors  Size Id Type

/dev/sdb1         256 501253099 501252844  239G  7 HPFS/NTFS/exFAT





Disk /dev/sdc: 14.42 GiB, 15472047104 bytes, 30218842 sectors

Disk model: DataTraveler 3.0

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x17f72809



Device     Boot Start      End  Sectors  Size Id Type

/dev/sdc1  *     2048 30218841 30216794 14.4G  c W95 FAT32 (LBA)





Disk /dev/sdd: 231.4 GiB, 248074076160 bytes, 484519680 sectors

Disk model: USB DISK 3.0    

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: gpt

Disk identifier: 78A06CDB-3718-4947-8961-F48EE10E36F1



Device       Start       End   Sectors   Size Type

/dev/sdd1     2048   1050623   1048576   512M EFI System

/dev/sdd2  1050624 484517887 483467264 230.5G Linux filesystem

ubuntu@ubuntu:~$ sudo lsblk -f

NAME        FSTYPE   LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINT

loop0       squashfs                                                        0   100% /rofs

loop1       squashfs                                                        0   100% /snap/snapd/7264

loop2       squashfs                                                        0   100% /snap/core18/1705

loop3       squashfs                                                        0   100% /snap/gnome-3-34-1804/24

loop4       squashfs                                                        0   100% /snap/gtk-common-themes/1506

loop5       squashfs                                                        0   100% /snap/snap-store/433

sda                                                                                  

&#9492;&#9472;sda1      exfat    Emu_02      64A5-F009                                           

sdb                                                                                  

&#9492;&#9472;sdb1      exfat    Emu_01      64A5-F009                                           

sdc                                                                                  

&#9492;&#9472;sdc1      vfat     UBUNTU 20_0 EE54-717A                              11.9G    18% /cdrom

sdd                                                                                  

&#9500;&#9472;sdd1      vfat                 DDE0-8FBF                                           

&#9492;&#9472;sdd2      ext4                 c9ca0bdb-8394-4f82-8285-0d9952099b27  205.2G     4% /media/ubuntu/c9ca0bdb-8394-4f82-8285-0d9952099b27

nvme0n1                                                                              

&#9500;&#9472;nvme0n1p1 ntfs     Recovery    4E268DC9268DB28F                                    

&#9500;&#9472;nvme0n1p2 vfat                 9A8E-8CC0                                           

&#9500;&#9472;nvme0n1p3                                                                          

&#9492;&#9472;nvme0n1p4 ntfs                 D8908FF9908FDBFE                                    

ubuntu@ubuntu:~$ sudo lsblk -m

NAME          SIZE OWNER GROUP MODE

loop0         1.9G root  disk  brw-rw----

loop1        27.1M root  disk  brw-rw----

loop2          55M root  disk  brw-rw----

loop3       240.8M root  disk  brw-rw----

loop4        62.1M root  disk  brw-rw----

loop5        49.8M root  disk  brw-rw----

sda           239G root  disk  brw-rw----

&#9492;&#9472;sda1        239G root  disk  brw-rw----

sdb           239G root  disk  brw-rw----

&#9492;&#9472;sdb1        239G root  disk  brw-rw----

sdc          14.4G root  disk  brw-rw----

&#9492;&#9472;sdc1       14.4G root  disk  brw-rw----

sdd           231G root  disk  brw-rw----

&#9500;&#9472;sdd1        512M root  disk  brw-rw----

&#9492;&#9472;sdd2      230.5G root  disk  brw-rw----

nvme0n1     931.5G root  disk  brw-rw----

&#9500;&#9472;nvme0n1p1   499M root  disk  brw-rw----

&#9500;&#9472;nvme0n1p2    99M root  disk  brw-rw----

&#9500;&#9472;nvme0n1p3    16M root  disk  brw-rw----

&#9492;&#9472;nvme0n1p4 930.9G root  disk  brw-rw----

[/FONT][/COLOR]


```

---

### Post by sudodus on 2020-06-16
Am I right that

- the internal SSD is '/dev/nvme0n1' - the NVME drive
- the USB drive with ubuntu installed is '/dev/sdd' - the USB drive

during this test?

Were you able to unplug or completely disconnect the NVME drive before you installed Ubuntu into the USB drive? Or did you 'only' [try to] disable it via the UEFI/BIOS menus?

---

### Post by bc-uk on 2020-06-16
> **sudodus said:**
> Am I right that

- the internal SSD is '/dev/nvme0n1' - the NVME drive
- the USB drive with ubuntu installed is '/dev/sdd' - the USB drive

during this test?
Yes to both.

> **sudodus said:**
> Were you able to unplug or completely disconnect the NVME drive before  you installed Ubuntu into the USB drive? Or did you 'only' [try to]  disable it via the UEFI/BIOS menus?
The very first attempt I  made at a USB > USB install, the SSD was connected and wasn't  disabled in the BIOS, I only changed the boot order so that the Live USB  installer would boot first. during the installer process, I assumed  that when I selected the '/dev/sdd' USB drive as the location where I  wanted to install ubuntu, that that is where it would be installed to.

---

### Post by sudodus on 2020-06-16
> **bc-uk said:**
> Yes to both.

:-)
> 
The very first attempt I  made at a USB > USB install, the SSD was connected and wasn't  disabled in the BIOS, I only changed the boot order so that the Live USB  installer would boot first. during the installer process, I assumed  that when I selected the '/dev/sdd' USB drive as the location where I  wanted to install ubuntu, that that is where it would be installed to.
Yes, and this caused a problem, because in UEFI mode, the *'first drive'* (usually the internal drive) will be selected, and *not* the drive that *you* select.

But what happened the second time, when you installed Ubuntu into the USB drive?

---

### Post by bc-uk on 2020-06-16
> **sudodus said:**
> But what happened the second time, when you installed Ubuntu into the USB drive?
The second attempt at a USB to USB installation, I physically removed the SSD. After the installation process, I tested the new USB installation, and it worked. It logged me in automatically, just as I'd specified in the installation options.

---

### Post by sudodus on 2020-06-16
More questions:

- When you try to boot from the installed system in the USB drive:

. is secure boot set?

. How can you see that it is booting from the USB drive (and not from the internal drive)? In other words, are you sure that you are really booting from the installed system in the USB drive? The problem might be that you are still booting from the internal drive, and it points into the external drive, where you have a new system which does not match what was installed the first time, when you wrote the bootloader into the internal drive).

---

### Post by sudodus on 2020-06-16
In order to be sure that it works with

- an installed system in the USB drive
- in UEFI mode
- with an internal NVME drive

I installed a Xubuntu 20.04 LTS system into an external SSD (connected via a USB to SATA adapter).

And yes, it works like it should. So I suspect that you are not really booting from the external drive, when it fails.

You have to make your computer boot from the external drive, even when the internal NVME drive is connected. And this must be done in your UEFI-BIOS system, either via a hotkey to a temporary menu, or via a modified setting in one of the UEFI-BIOS menus. Maybe [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB) or [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/uefi) can help you.

---

### Post by bc-uk on 2020-06-16
> **sudodus said:**
> More questions:

- When you try to boot from the installed system in the USB drive:

. is secure boot set?
Tried with it enabled and disabled, but same results as before. Also tried with OS Type set to Other OS and Windows UEFI Mode, but still no joy.

> **sudodus said:**
> How can you see that it is booting from the USB drive (and not from the internal drive)? In other words, are you sure that you are really booting from the installed system in the USB drive?
I can't tell where it's booting from. 

In the BIOS (Boot menu), there are two entries for the USB installed ubuntu: 

ubuntu (USB DISK 3.0 PMAP)
UEFI: USB DISK 3.0, Partition 1 (236581MB)

Selecting the first option, it boots straight to the ubuntu login screen. Selecting the second option, it very briefly displays this message:

```

System BootOrder not found. Initializing defaults.
Creating boot entry "Boot0001" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi"

```

Then the PC resets, shows BIOS prompt, then boots into ubuntu login screen.

---

### Post by sudodus on 2020-06-16
- If the computer can still boot from the USB drive (when the internal drive is removed/disconnected), we know that the installed system in the USB drive is good.

- Then you must continue trying to make the computer boot from it (instead of booting from the internal drive, when that drive is connected).

. What computer is it? Please specify brand name and model. It may help us help you find out how to make it boot from the USB drive.

- Have you turned off secure boot? It might help.

---

### Post by C.S.Cameron on 2020-06-17
Apologies for interupting:

When I am trying to keep track of which OS I am booting, on which drives, i change the grub.cfg menuentry title a little bit like:

"menuentry 'Ubuntu hdd1' --class ubuntu..."

"menuentry 'Ubuntu usb2' --class ubuntu..."

"menuentry 'Ubuntu ssd1' --class ubuntu..."

---

### Post by sudodus on 2020-06-17
> **C.S.Cameron said:**
> Apologies for interupting:

When I am trying to keep track of which OS I am booting, on which drives, i change the grub.cfg menuentry title a little bit like:

"menuentry 'Ubuntu hdd1' --class ubuntu..."

"menuentry 'Ubuntu usb2' --class ubuntu..."

"menuentry 'Ubuntu ssd1' --class ubuntu..."

Thanks for sharing a good method :-)

---

### Post by bc-uk on 2020-06-22
> **sudodus said:**
> Thanks for sharing a good method :-)
I haven't had time to carry on with this over the last week. However, I came back to it today, removed my SSD, but the same problem is happening when booting from the USB installation. So that means that attempting to boot fromthe USB installation with the SDD attached somehow modified the USB installation, as the USB installation was booting fine with the SSD detached.

Eitherway, I would consider the installer modifying the boot sector of a drive, when the user specifically indicates not to, to be a very serious bug. It's put me off using ubuntu in future, and outside of work scenarios I will be very reluctant to use it on future projects. Overall, this has been an incredibly frustrating experience that has consumed a huge amount of my time.

---

### Post by dragonfly41 on 2020-06-22
I sense a degree of frustration here in a long thread .. I have skimmed through the thread and I suggest an approach which worked for me. I have read your concern about the risk of screwing up Windows 10 (your post #17).

If you are game for a further throw of the dice, first connect the external USB drive which should have Ubuntu installed.

Next run the LiveUSB (created by Rufus?) and get into Try Ubuntu mode.

At this point my suggestion is to install into your LiveUSB the alternative (third party) boot loader rEFInd.

This is discussed here .. [https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

But to cut the story short, in your Try Ubuntu liveUSB session run ..

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

Now at the point of installing rEFInd you are prompted to choose the EFI partition to receive rEFInd. Do not choose the Windows EFI partition. You want to target your **external Ubuntu USB** and also not your LiveUSB.

In Post #6 you wrote "Fix the USB (since it already has an EFI partition)" and it is that (external) EFI partition (500 MB) you should choose to receive installation of rEFInd alongside other boot loaders. You can in fact have multiple EFI partitions

 In my external USB (in fact an SSD) the EFI partition with rEFInd installed is ..
 
 /boot/efi/EFI
 > Boot
 > Dell
 > refind
 > tools
 > ubuntu

Note that refind just adds a new sub-folder (refind) into /boot (on Ubuntu) and does not interfere with the existing default folders.

When you reboot you should see as a boot option refind_x64.efi

That is the option to choose.

You can further tweak the file refind.conf to force the boot process to look first at external drives before looking at the internal drive for loaders.

---

### Post by bc-uk on 2020-06-22
OK, in one last ditch attempt, I solved the problem. When doing the USB>USB install, there's an option to update ubuntu during installation. By unticking this, the USB installation works, even with the SSD attached. There must be an issue with the latest updates, because even if you opt to install these updates after booting into the USB installation, it will no longer auto-login, and even if you enter your password, it just goes to a blank purple screen and stays there indefinitely.

*edit* I tried this before I saw your post                                                                                      [**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878")

---

### Post by sudodus on 2020-06-22
Thanks for sharing your solution :-)

---

### Post by bc-uk on 2020-06-22
I have a bit more info on this problem. I installed RealVNC Server onto my USB installation. I then installed the latest nvidia driver (440 proprietary,tested), then rebooted. On the PC running ubuntu, it wouldn't let me past the login screen (as per previous pages in this thread). However, surprisingly, I was able to connect via VNC, and the VNC screen was a very low res. Luckily was able to uninstall the driver, and rebooting auto logged me in as it should. So, the problem seems to be the latest nvidia driver (for 1080 Ti).

---

### Post by bc-uk on 2020-06-22
Fixed that issue by changing display manager to lightdm:

    ```
sudo apt-get install lightdm
```

Select the lightdm option, then reboot to fix.

---

### Post by TheFu on 2020-06-22
wow. 52 posts - this is why I&#8217;d use a virtual machine solution rather than multi-boot.

---

### Post by bc-uk on 2020-06-22
I need access to the GPU, and the PC I'm using only has one GPU.

---

### Post by bc-uk on 2020-06-24
Not unsurprisingly, the USB installation will now no longer boot. It just goes straight to a grub command line. Nothing has changed on my system since ubuntu was working a few days ago, although I had been using Win10 all yesterday.

---

### Post by sudodus on 2020-06-24
A **persistent live** Ubuntu system is much easier to install into an external drive compared to an installed system, and I think it is also more resistant against the shenanigans of Windows.

But there are some drawbacks compared to an installed system. You cannot install new kernels and kernel drivers. If this is necessary, you should backup your home directory (to some other drive) and after that create a new persistent live drive with the current daily iso file of the latest LTS version, reinstall the installed program packages and restore the content of the home directory from the backup.

You can use mkusb for this purpose.

If you run standard Ubuntu live, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```

sudo add-apt-repository universe  # only for standard Ubuntu live

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt update
sudo apt install mkusb usb-pack-efi

```

See also [this link](https://help.ubuntu.com/community/mkusb)

---

### Post by bc-uk on 2020-06-24
So I have to start from scratch? I spent a lot of time configuring the USB installation once it seemed to be working a few days ago.

---

### Post by sudodus on 2020-06-24
No, you don't have to, I only offer a persistent live drive as an alternative.

It should also be possible to repair the bootloader of your current Ubuntu system, for example with **Boot Repair**.

See [this link](https://help.ubuntu.com/community/Boot-Repair).

Warning: Avoid writing to your Windows drive. If you are not sure about that, then you should unplug or disconnect your internal drive with Windows.

---

### Post by bc-uk on 2020-06-24
I already have a live drive on another USB, that's how I created the bootable USB installation. So I can just boot back into my live drive and repair grub from that?

---

### Post by bc-uk on 2020-06-24
Also, one thing I did do yesterday in Windows - I updated the Nvidia drivers. Perhaps that has caused the issue?

---

### Post by bc-uk on 2020-06-24
Is there any way I can boot the USB installation from the live drive? I would prefer to do that if there are any risks to the Win10 installation by running Boot-Repair.

---

### Post by sudodus on 2020-06-24
Yes, you can repair the grub bootloader from a live Ubuntu drive.

I think the problem was some more general system update of Windows (updating the nvidia driver or Windows should not affect booting of Ubuntu in another drive).

---

### Post by sudodus on 2020-06-24
If you don't want to use Boot-Repair, you can try to 'do it yourself' according to the tips of the following link,

[help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

It works for classic grub in BIOS mode, but I am not sure that it will help you also for UEFI mode booting.

Edit: Maybe the following link will help in UEFI mode,

[help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bc-uk on 2020-06-24
I ran Boot-Repair from the Live drive. It ran OK, but rebooting doesn't boot the usb installation. Here's the log:

[https://paste.ubuntu.com/p/YD5mvHPx7v](https://paste.ubuntu.com/p/YD5mvHPx7v)

---

### Post by bc-uk on 2020-06-24
Do I need to have the usb installation connected when running Boot-Repair? When I ran it, I didn't have it attached.

---

### Post by sudodus on 2020-06-24
Boot-Repair sees no Ubuntu partition at all except in the live drive /dev/sdc? Where would you expect Ubuntu to be installed (in which drive)?

My guess would be in /dev/sda or /dev/sdb.

In the drive /dev/sda with 257 Gibibytes there seems to be only an exFAT partition, and it occupies the whole drive. Have you overwritten Ubuntu with an exFAT partition?

The situation with /dev/sdb is similar, also only one exFAT partition.

-o-

Let us hope that the drive where you installed Ubuntu was not connected when you created the output from Boot-Repair, and when you connect it, you will see Ubuntu again, and it will work, when booted into.

Edit: We were cross-posting. Well, you cannot repair a drive that is not connected :-P

---

### Post by bc-uk on 2020-06-24
There are two other FAT USB pen drives attached that aren't bootable, they only contain data. Those are both 256GB. The ubuntu installation usb was not attached when I ran Boot-Repair. Should I run Boot-Repair again with the bootable ubuntu usb attached?

---

### Post by bc-uk on 2020-06-24
> **sudodus said:**
> Edit: We were cross-posting. Well, you cannot repair a drive that is not connected :-P
OK, I will try Boot-Repair again with the usb installation attached. I thought the issue was with the grub partition, not the usb installation.

---

### Post by bc-uk on 2020-07-09
Still having issues with this. I have been using the ubuntu USB for the last week or so. However, as soon as I shutdown (then unplug usb) and boot Win10 again, the next time I try to boot from the ubuntu usb I get this:

```
error: file'/boot/grub/i386-pc/normal.mod' not found. 
Entering rescue mode...
```

---

### Post by oldfred on 2020-07-09
Grub installed to internal drive has just a boot loader & it needs the rest of grub in your install. If that install is a removable drive, then grub cannot boot.

That error also often comes from booting in wrong boot mode. If you installed both BIOS & UEFI versions of grub, but only update one, then the other will never work.
If UEFI system, you need to always be booting in UEFI boot mode. 

If external drive you can have it first in boot order & internal second if external not connected. But cannot boot from internal using part of grub on external if not there.

---

### Post by C.S.Cameron on 2020-07-09
> **bc-uk said:**
> Still having issues with this. I have been using the ubuntu USB for the last week or so. However, as soon as I shutdown (then unplug usb) and boot Win10 again, the next time I try to boot from the ubuntu usb I get this:

```
error: file'/boot/grub/i386-pc/normal.mod' not found. 
Entering rescue mode...
```

When I get that error I reinstall grub

```
sudo mount /dev/sdxy /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sdx

```

Where sdxy is my EFI boot partition.

---


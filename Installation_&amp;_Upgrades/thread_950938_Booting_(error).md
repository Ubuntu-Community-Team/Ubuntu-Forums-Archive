---
title: "Booting (error)"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Azrael90 on 2008-10-17
Hi,
I tried to install ubuntu about 3 or 4 times now burned and downloaded everything new each time.
After the install which I do manually (setting the swap partition, ext3 and boot sector to "/").
I am installing on a 260 GB SATA hdd with another windows partition on it and another 300 GB SATA hdd for data storage.

However after the install I just keeps booting Windows with the Windows bootloader. I tried using SGD but it was no good. I tried pretty much everything on that disk.

Someone here who likes to troubleshoot ?

Thanks

---

### Post by Azrael90 on 2008-10-17
forgot to post that if it is helpfull

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x451e1658
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5100    40960048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        5101        7531    19527007+  83  Linux
/dev/sda3            7532        7774     1951897+  82  Linux swap / Solaris
Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3edae12e
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36480   293025568+   7  HPFS/NTFS
```

What does "Partition 1 does not end on cylinder boundary." mean ?

---

### Post by caljohnsmith on 2008-10-17
OK, please post the output of:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump

```
So have you tried setting your BIOS to boot sda first on start up? If so, what happens?

---

### Post by Azrael90 on 2008-10-17
> **caljohnsmith said:**
> 
So have you tried setting your BIOS to boot sda first on start up? If so, what happens?

Sorry but I can set my BIOS to boot a special partition ? only did that with SGD but it did have no effect it just said that "SGD has not done it !:(".

Here are the results:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff01                                   
0000002

```

---

### Post by caljohnsmith on 2008-10-17
According to the output of those commands you posted, it appears you have Grub correctly installed to your sda drive. If you are still getting Windows on start up, you must be booting your sdb drive. You originally said:
[QUOTE=Azrael90]I am installing on a 260 GB SATA hdd with another windows partition on it and another 300 GB SATA hdd for data storage.[/QUOTE]
So you are saying Windows is on sda and your sdb is data storage? Unless your Windows boot files are on sdb, I don't see how Windows could be on sda and not sdb. In order to help clarify some of this, please post:
```
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1

```
Note the "-l" is a lowercase L, not a one.

---

### Post by Azrael90 on 2008-10-17
The results:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sdb1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/sdb1
ubuntu@ubuntu:~$ ls -l /mnt/sda1 /mnt/sdb1
/mnt/sda1:
total 2095178
-rwxrwxrwx 1 root root          0 2008-09-12 17:02 AUTOEXEC.BAT
-rwxrwxrwx 1 root root          0 2008-09-12 17:02 CONFIG.SYS
-rwxrwxrwx 1 root root         86 2008-09-12 19:28 CSB.LOG
drwxrwxrwx 1 root root       4096 2008-09-12 17:05 Dokumente und Einstellungen
drwxrwxrwx 1 root root          0 2008-10-01 12:35 DVDVideoSoft
-rwxrwxrwx 1 root root          0 2008-09-12 17:02 IO.SYS
-rwxrwxrwx 1 root root          0 2008-09-12 17:02 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-09-12 19:18 MSOCache
-rwxrwxrwx 1 root root        219 2008-10-18 01:45 new file
-rwxrwxrwx 1 root root        162 2008-10-18 01:19 new file~
drwxrwxrwx 1 root root          0 2008-09-12 17:44 NVIDIA
-rwxrwxrwx 1 root root 2145386496 2008-10-18 01:27 pagefile.sys
drwxrwxrwx 1 root root      16384 2008-10-01 19:59 Programme
drwxrwxrwx 1 root root          0 2008-10-17 11:41 QUARANTINE
drwxrwxrwx 1 root root          0 2008-09-26 18:22 RECYCLER
-rwxrwxrwx 1 root root        347 2008-09-12 19:27 RHDSetup.log
drwxrwxrwx 1 root root       4096 2008-09-12 17:05 System Volume Information
drwxrwxrwx 1 root root      36864 2008-10-17 22:17 WINDOWS
drwxrwxrwx 1 root root       8192 2008-09-12 19:38 xampp

/mnt/sdb1:
total 6632558
-rwxrwxrwx 2 root root      10888 2008-10-17 09:21 1208550806-Save90.rar
drwxrwxrwx 1 root root       8192 2008-10-17 09:06 Assassin's Creed
-rwxrwxrwx 2 root root    2186435 2008-10-17 09:06 AuctioneerSuite-5.1.3607.zip
-rwxrwxrwx 1 root root       4952 2001-08-18 10:00 bootfont.bin
-rwxrwxrwx 1 root root        210 2008-09-12 18:45 boot.ini
drwxrwxrwx 1 root root          0 2008-09-25 20:21 CAMERA
drwxrwxrwx 1 root root       4096 2008-10-17 17:20 COD4
drwxrwxrwx 1 root root          0 2008-09-29 13:36 I Pod
-rwxrwxrwx 1 root root      33249 2008-09-27 16:51 jcsave.zip
drwxrwxrwx 1 root root       4096 2008-09-26 18:31 Just Cause
-rwxrwxrwx 2 root root      73728 2006-09-25 20:00 JustCause_DT_SkOssInO.exe
-rwxrwxrwx 2 root root     436856 2008-10-17 09:06 MailboxComplete14.zip
drwxrwxrwx 1 root root       8192 2008-10-17 11:41 MT-X
-rwxrwxrwx 2 root root    3037334 2008-10-17 09:09 mt-x_1000_setup.rar
-rwxrwxrwx 1 root root      47564 2004-08-03 20:38 NTDETECT.COM
-rwxrwxrwx 1 root root     251184 2004-08-03 20:59 ntldr
-rwxrwxrwx 1 root root 2147483648 2007-11-06 10:19 pro-cod4.B00
-rwxrwxrwx 1 root root 2147483648 2007-11-06 10:24 pro-cod4.B01
-rwxrwxrwx 1 root root  341147648 2007-11-06 10:25 pro-cod4.B02
-rwxrwxrwx 1 root root 2147483648 2007-11-06 10:15 pro-cod4.B6I
-rwxrwxrwx 1 root root       4966 2007-11-06 10:08 pro-cod4.B6T
drwxrwxrwx 1 root root          0 2008-09-15 15:46 Programme
drwxrwxrwx 1 root root       4096 2008-09-28 01:37 QuestParser
drwxrwxrwx 1 root root          0 2008-09-21 01:45 RECYCLER
-rwxrwxrwx 1 root root    1940992 2008-08-03 22:00 SharePod.exe
-rwxrwxrwx 1 root root        609 2008-10-01 19:11 SharePod.log
-rwxrwxrwx 2 root root       6427 2008-10-01 19:27 SharePodSettings.xml
drwxrwxrwx 1 root root       4096 2008-09-12 17:05 System Volume Information
drwxrwxrwx 1 root root          0 2008-10-01 12:03 urlaub
drwxrwxrwx 1 root root      20480 2008-10-16 22:56 World of Warcraft
drwxrwxrwx 1 root root      12288 2008-09-25 17:52 WoW
drwxrwxrwx 1 root root       4096 2008-10-01 12:05 Wow addons
drwxrwxrwx 1 root root       8192 2008-10-17 13:34 WoW Real
drwxrwxrwx 1 root root          0 2008-09-12 19:32 Wow *HAD TO EDIT*
drwxrwxrwx 1 root root       4096 2008-10-16 22:47 YouTube

```

Is it normal that the boot.ini is on the hdd without the OS ?

---

### Post by caljohnsmith on 2008-10-17
That's interesting, your Windows boot files are indeed on your sdb drive, so it is clear you are booting from your sdb drive at this point. 
[QUOTE=Azrael90]Sorry but I can set my BIOS to boot a special partition ? only did that with SGD but it did have no effect it just said that "SGD has not done it ![/QUOTE]
I'm not sure what you mean by that. The best way to get your set up working would be set your BIOS to boot the sda drive on start up instead of the sdb drive, and then you can move your Windows boot files back to the sda drive. You should be able to press some function key on start up (F10, F12, etc) so that you can access your BIOS and change sda to boot first. If you don't know which function key will take you into BIOS, you could either consult the documentation that came with your computer, or if you just press as many of the function keys as you can on start up that might work. :)

If you absolutely can't boot from your sda drive, there are many other options available to get your setup working, but it will be much, much simpler and ideal if you can just boot your sda drive. Try that and let me know how it goes. :)

---

### Post by Azrael90 on 2008-10-18
I will try that. Sorry but I mixed sda and hda I thought you meant booting a special partition instead of the other hdd.

ofc I know how to enter the BIOS.

I will report back as soon as I am finished.

---

### Post by Azrael90 on 2008-10-18
Okay,
I tried booting from the other drive. It loads GRUB but while loading it throws error 17 at me.

---

### Post by ShinobiTeno on 2008-10-18
> **Azrael90 said:**
> I will try that. Sorry but I mixed sda and hda I thought you meant booting a special partition instead of the other hdd.

ofc I know how to enter the BIOS.

I will report back as soon as I am finished.

Just a side-info i know. Lastest libata driver thats used to access S/Pata disks, marks PATA as SD* as well. They did it, so its easier to migrate to sata. So you might find **old PATA** to become **sda** on Ubuntu, shifting all original sata disks down a letter and **still remaining hda** on knoppix cd,say, 5.0.

---

### Post by Azrael90 on 2008-10-18
> **ShinobiTeno said:**
> Just a side-info i know. Lastest libata driver thats used to access S/Pata disks, marks PATA as SD* as well. They did it, so its easier to migrate to sata. So you might find **old PATA** to become **sda** on Ubuntu, shifting all original sata disks down a letter and **still remaining hda** on knoppix cd,say, 5.0.

Thanks but that is not the case.

Is there a way I can just set the boot.ini to have linux in there as well?

I tried to install grub on the drive again with 
"sudo grub-install /dev/hdg3" and do this "sudo dd if=/dev/hdg3 of=grub.mbr bs=512 count=1" 
but it did not even install.
it says:
```
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


```
So I could not copy it to the boot.ini or include it.

---

### Post by caljohnsmith on 2008-10-18
You could add your Grub boot sector to the Windows boot loader like you suggest, but I would not recommend it as I think we can get your sda drive booting just fine. When you get the Grub error 17, do you get that before you see a Grub menu, or after you get the Grub menu and select Ubuntu? Also, when you start up, does it say "press ESC to see menu" or something like that? If so, try repeatedly pressing ESC on start up and see if that gives you the Grub menu. 

Also, please post:
```
sudo mount /dev/sda2 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by Azrael90 on 2008-10-18
going to post that.

the error occurs while loading grub so menu at all. it just says something like loading grub stage 1.5 and then error 17.

the only thing I see before is the ram counting and my graphic cards spec as well as the screen to enter the BIOS.

---

### Post by Azrael90 on 2008-10-18
```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a1ed6d93-0408-422a-a807-b57127741b7f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a1ed6d93-0408-422a-a807-b57127741b7f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a1ed6d93-0408-422a-a807-b57127741b7f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by caljohnsmith on 2008-10-18
How old is your computer and its BIOS? Your Ubuntu partition starts at about the 40 GB mark but extends to near the end of that 250 GB HD, and some BIOSes can't access anything past either 8 GB or 137 GB, depending on how old the BIOS is. So if your BIOS has one of those limitations, that could be why Grub can't mount the Ubuntu partition (that's what an error 17 is) since the Ubuntu partition could be outside of the range of BIOS. Sometimes you can get a Grub error 17 when the Ubuntu partition's file system is corrupt, and that's why Grub can't mount it; but since your partition mounted fine when you printed the menu.lst, then it's not likely that is the problem, but we should at least eliminate that as a possibility I think. 

So with that in mind, please do the following and let me know if the "fsck" command returns any errors:
```
sudo umount /dev/sda2
sudo fsck -y /dev/sda2
```
If it doesn't return any errors, then try the following to see if it changes Grub's behavior on start up:
```
sudo grub
grub> root (hd0,1)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
If the above commands do not return any errors, then reboot and let me know what happens. :)

---

### Post by Azrael90 on 2008-10-18
looks promising.

```
ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda2
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda2: clean, 108121/1220608 files, 605530/4881751 blocks
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)
root (hd0,1)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
quit

```

after rebooting I get into GRUB console.

looks like this
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```

---

### Post by caljohnsmith on 2008-10-18
Since you got dropped into the Grub command line on start up, I think Grub was able to access its stage2 file successfully but not the menu.lst; it looks more likely that you have the 137 GB BIOS limitation that is giving us the problems. 

I think your best bet would be to use Grub4DOS to boot your Windows and Ubuntu. Grub4DOS is just like Ubuntu's Grub but with more features, and you can put it inside your Windows NTFS partition; so it should be within range of your BIOS. 

Here are the steps to install it:
[LIST=1]
[*]Download the Grub4DOS package to your Ubuntu desktop from [here]("http://download.gna.org/grub4dos/grub4dos-0.4.3.zip").
[*]Open a terminal, and do:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
cd ~/Desktop
unzip grub*.zip
cd grub*
sudo cp glrdr /mnt/sda1/.
sudo cp /mnt/sda2/boot/grub/menu.lst /mnt/sda1/.
sudo dd if=grldr.mbr of=/dev/sda bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sda skip=1 seek=1
```
[/LIST]
NOTE: if any of the above commands return an error, please *do not proceed* with the rest of the commands. Also make sure to copy and paste the dd commands as those can be dangerous if you make even a small typo. 

After that, reboot, and you should hopefully see your Grub menu on start up. You may have to edit your menu.lst to get Windows and Ubuntu booting OK (and also move your Windows boot files back); but see if you can get as far as getting the Grub menu on start up, and we'll work from there. :)

---

### Post by Azrael90 on 2008-10-18
well I seriously doubt the 137 gb thing.
My comp is not very old only a good year so the BIOS is not any older. and since it supports my dual core 6 ghz prozessor I think it should be able to handle the stuff you speak about.

and on a sidenote I had linux running before with ubuntu on this comp. although grub had some problems with it I had to use SGD to boot.
the only thing that changed since then is that I am not using IDE hdd and a raid controller anymore but SATA drives only.

---

### Post by caljohnsmith on 2008-10-18
Have you ever been able to boot off your sda drive, or have you always booted off your sdb drive? If you haven't yet successfully booted your sda drive, the problem could be something as simple as how it is configured in BIOS (LBA, CHS, RAID, AHCI vs. IDE, etc). I would recommend changing your HDD BIOS settings one by one and seeing if it makes any difference booting the drive (and I would write down the original settings so you can revert back if necessary). It would be most ideal to boot from your sda drive, but if you just want to get things working, you could install Grub4DOS to your sdb drive and boot everything from that drive. The disadvantage of that is of course you won't be able to boot any of your OSes if anything happens to sdb.

---

### Post by Azrael90 on 2008-10-18
well I did not know that I was booting from the sdb drive since yesterday. I mean how should I have known that stupid old windows put the files on the wrong hdd ?
What do you think about total fresh install of both systems ?
Could that help ?
I need to reinstall my windows every now and then anyway because it is getting kinda slow.

---

### Post by caljohnsmith on 2008-10-18
> **Azrael90 said:**
> well I did not know that I was booting from the sdb drive since yesterday. I mean how should I have known that stupid old windows put the files on the wrong hdd ?
What do you think about total fresh install of both systems ?
Could that help ?
I need to reinstall my windows every now and then anyway because it is getting kinda slow.
As long as doing a fresh install is an option, I would say go for it. And just to ensure that you don't run into any BIOS limitation issues, I would recommend putting your Ubuntu partition before the Windows partition on the sda drive, or at least make a ~200 MB Ubuntu /boot partition before the Windows partition. Also I would make sure to install Windows to a primary partition and not a logical one, or Windows will definitely put its boot files on some other primary partition. If you can temporarily disconnect your sdb drive, that would be ideal to guarantee Windows behaves and stays on sda. And of course it is always best to install Windows first, then Ubuntu, or Windows will overwrite Grub in the MBR. Let me know how it goes or if you run into problems. :)

---

### Post by Azrael90 on 2008-10-18
> **caljohnsmith said:**
> As long as doing a fresh install is an option, I would say go for it. And just to ensure that you don't run into any BIOS limitation issues, I would recommend putting your Ubuntu partition before the Windows partition on the sda drive, or at least make a ~200 MB Ubuntu /boot partition before the Windows partition. Also I would make sure to install Windows to a primary partition and not a logical one, or Windows will definitely put its boot files on some other primary partition. If you can temporarily disconnect your sdb drive, that would be ideal to guarantee Windows behaves and stays on sda. And of course it is always best to install Windows first, then Ubuntu, or Windows will overwrite Grub in the MBR. Let me know how it goes or if you run into problems. :)

Okay so how do I differ logical and primary partition ?

I planed on leaving some free space for linux while making the windows partition and install is taht okay ?

---

### Post by Azrael90 on 2008-10-18
just noticed something while I wanted to install xp. it listed the 280 gb partition as C: which I guess is wrong. I am copying things on my external hdd and install the new OS and clean everything up

---

### Post by Azrael90 on 2008-10-18
Okay I installed Windows and then Linux on the sdb drive because sda was not working.
Windows is ignoring Linux while booting. Again.

I will go and post fdisk

---

### Post by Azrael90 on 2008-10-18
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x451e1658

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3edae12e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       12453    48829567+  83  Linux
/dev/sdb3           12454       12696     1951897+  82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2008-10-18
OK, try the following:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Reboot, and let me know what happens.

---

### Post by Azrael90 on 2008-10-18
I am writing from my laptop now. cannot boot.

Grub loaded up on booting just fine and I get the right menu with ubuntu,memtest,recovery and windows but when I chose one of those options it says Error 22 : No such partition

---

### Post by caljohnsmith on 2008-10-18
OK, go ahead a reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,1)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to:
```
#groot=(hd0,1)
```
Also, the correct Windows entry should be:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by Azrael90 on 2008-10-18
Thanks it worked just the way you said. I booted some times to see if everything is saved and both OS are working and they really are !

Thank you for your time and effort.
I just love the fact that I can run compiz again. XP just sucks but I just need to play some games once in a while.

Greetings

Azrael90

---

### Post by caljohnsmith on 2008-10-18
That's great news it's all finally working. Cheers and have fun. :)

---

### Post by Azrael90 on 2008-10-18
well there is kinda one problem

when booting windows it says something like "starting up...." but keeps like that forever so I cannot get into windows

I know I said it worked before but I only went this far and rebooted because I thought it would work if this shows up and would only need some time.

---

### Post by caljohnsmith on 2008-10-18
So after you installed Windows and Ubuntu to sdb, you were able to boot all the way into Windows before you installed Grub, is that true?

Go ahead and boot your Windows Install CD, go to the "recovery console", and do:
```
fixboot
chkdsk /r
```
Make sure you run chkdsk as many times as it takes until it reports no errors. Then try booting Windows again and let me know exactly what happens.

---

### Post by Azrael90 on 2008-10-19
did that and it recovered some things. did again and no errors were found.

I still only get the "Starting up ..." when trying to boot windows. Linux works fine.

---

### Post by caljohnsmith on 2008-10-19
OK, next would be to rebuild the Windows boot sector so it will hopefully have the correct partition/file system parameters:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens.

---

### Post by Azrael90 on 2008-10-20
I did the testdisk thing just like you said and it did not give any errors and said that the boot sectors are ok and identical.
So I left out the write thing as you said.
But I am still getting stuck on the starting up screen.

---

### Post by caljohnsmith on 2008-10-20
> **Azrael90 said:**
> 
I know I said it worked before but I only went this far and rebooted because I thought it would work if this shows up and would only need some time.
I think that restarting Windows right when it was booting up may be what is causing your problems; you could try doing a "Windows Repair" from your Win Install CD. To do that, you have to choose the "install Windows" at the first menu and then after that you will be given an option to repair Windows rather than reinstall it.

---

### Post by Azrael90 on 2008-10-20
> **caljohnsmith said:**
> I think that restarting Windows right when it was booting up may be what is causing your problems; you could try doing a "Windows Repair" from your Win Install CD. To do that, you have to choose the "install Windows" at the first menu and then after that you will be given an option to repair Windows rather than reinstall it.

won't that kill grub ?

---

### Post by caljohnsmith on 2008-10-20
I have Windows XP Home Edition, and when I did a "Windows Repair" once, it fortunately didn't overwrite Grub in the MBR. But I read once where someone claimed that for a Windows XP Professional Edition, doing a Windows repair did overwrite Grub. Either way it doesn't matter, because if Grub gets overwritten, it will take only a few minutes to follow the steps in post #26 to reinstall Grub to the MBR.

---

### Post by Azrael90 on 2008-10-20
okay now some strange this are happening. tried to boot from the cd and make the repair butit just set checking harware and then nothing. I currently searching another copy of my winxp disk and try again.

---

### Post by Azrael90 on 2008-10-23
the cd is fine. gotta be something else wrong there.

---


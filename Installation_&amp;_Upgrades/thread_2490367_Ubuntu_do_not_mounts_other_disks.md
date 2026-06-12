---
title: "Ubuntu do not mounts other disks"
date: 2023-08-31
forum: Installation &amp; Upgrades
---

### Post by gillesdc on 2023-08-31
Hi everyone,

Last week I tried to install Orthanc on my laptop on Ubuntu and I follow a tutorial (I can't find it again, I'm searching for it...) that told me to add a line in the sources.list file. These informations are not really  precise I'm sorry, but I don't think they are needed to help me. If they do, I'll try to find them.

The fact is that when I updated with this modification, a message appeared to tell me that it will modify the grub and I accepted it. 
Since then, my windows partition is not working (it's a dual boot) and ubuntu do not mount (altough they're visible using fdisk command or gparted) any disk (neither the windows partition or external usb flash). The others disks appears at first but when I click them, they disappear quickly with the error message "disk disconect without reply". I tried tomount them manually but it didn't work (maybe I did it wrong, I'm not an expert).

Do anyone have an idea to how I could reset the grub to its normal function? I have removed the additional line from the sources.list and update several times everything but it didn't change... 
Also I don't have acces to another pc right now so I can't make any bootable usb...

The rest seems to work quite well (apart for orthanc lol, very bad tutorial).

Thank you so much for your help,
Gilles

---

### Post by Rubi1200 on 2023-09-01
If you are able to boot into your Ubuntu install please do the following:

Open a terminal with Ctrl+Alt+T and run these commands, separately, and copy/paste the output to post here on the forum. 

When replying use Go Advanced and then wrap the text with # tags so we can read and interpret the output.

```
cat /etc/default/grub
```

```
cat /etc/apt/sources.list
```

```
cat etc/fstab
```

Also, ```
sudo fdisk -l
``` would be helpful.

---

### Post by yancek on 2023-09-01
I'm not familiar with the software you are referring to.  Doing an online search turned up the site at the link below.  Is that the software you are trying to use?  If you click on the Explore tab under Resources on the right, it gives a lot of information on installing/using.

[https://www.orthanc-server.com/](https://www.orthanc-server.com/)

It's a very good idea to make not of any changes to GRub in any situation.  I don't know why it would need to make a change but posting the information requested above is going to be your first step to solving this problem.

---

### Post by gillesdc on 2023-09-01
Thank you so much for your help!

Here are the outputs of the commands: 

For 
```
[COLOR=#000000][FONT=&amp]cat /etc/default/grub[/FONT][/COLOR]
```
It returns 
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host 
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
#GRUB_DISABLE_OS_PROBER=false


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

For ```
[COLOR=#000000][FONT=&amp]cat /etc/apt/sources.list[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]It returns
[/FONT][/COLOR]```
# deb cdrom:[Ubuntu 21.10 _Impish Indri_ - Release amd64 (20211012)]/ impish main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://be.archive.ubuntu.com/ubuntu/ jammy main restricted
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ jammy universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish universe
deb http://be.archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ jammy multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish multiverse
deb http://be.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse




deb http://security.ubuntu.com/ubuntu jammy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu impish-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu impish-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu impish-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.


```[COLOR=#000000][FONT=&amp]

For
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]cat etc/fstab[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]It returns
[/FONT][/COLOR]```
cat: etc/fstab: No such file or folder

```

[COLOR=#000000][FONT=&amp]For
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]sudo fdisk -l[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000][FONT=&amp]It return
[/FONT][/COLOR]```
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 118.23 MiB, 123973632 bytes, 242136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 105.82 MiB, 110964736 bytes, 216728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 55.66 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 63.45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 63.46 MiB, 66547712 bytes, 129976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 73.9 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 66.56 MiB, 69795840 bytes, 136320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: PC SN530 NVMe WDC 256GB                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C3FC4FF6-0835-4153-A0CC-3B25C6F0FE2F


Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    309247    307200   150M EFI System
/dev/nvme0n1p2    309248    571391    262144   128M Microsoft reserved
/dev/nvme0n1p3    571392 195229695 194658304  92.8G Microsoft basic data
/dev/nvme0n1p4 498087936 500115455   2027520   990M Windows recovery environment
/dev/nvme0n1p5 195229696 498087117 302857422 144.4G Linux filesystem


Partition table entries are not in disk order.




Disk /dev/loop11: 237.21 MiB, 248733696 bytes, 485808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 349.69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 236.85 MiB, 248352768 bytes, 485064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 73.88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop8: 55.66 MiB, 58368000 bytes, 114000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop17: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop19: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop20: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop18: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop21: 436.3 MiB, 457498624 bytes, 893552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop22: 37.09 MiB, 38891520 bytes, 75960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop23: 260.71 MiB, 273375232 bytes, 533936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop24: 448.68 MiB, 470474752 bytes, 918896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop27: 252.63 MiB, 264900608 bytes, 517384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop26: 289.78 MiB, 303853568 bytes, 593464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop25: 450.15 MiB, 472018944 bytes, 921912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop28: 448.68 MiB, 470474752 bytes, 918896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop29: 448.92 MiB, 470728704 bytes, 919392 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop30: 253.77 MiB, 266092544 bytes, 519712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop31: 244.57 MiB, 256450560 bytes, 500880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop32: 68.14 MiB, 71450624 bytes, 139552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop34: 17.85 MiB, 18714624 bytes, 36552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop35: 234.6 MiB, 245997568 bytes, 480464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop36: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop33: 78.39 MiB, 82202624 bytes, 160552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop38: 42.64 MiB, 44707840 bytes, 87320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop37: 76.27 MiB, 79970304 bytes, 156192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop39: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes
```[COLOR=#000000][FONT=&amp]

Also, thank you yancek for the informations! I'll look at it carefully to install the software once this issue is solved.
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by Rubi1200 on 2023-09-01
Oops, sorry my bad.

Please let us see this:

```
cat /etc/fstab
```

And can you please also show us this:

```
cat /etc/apt/sources.list.d
```

---

### Post by gillesdc on 2023-09-01
For ```
[COLOR=#000000][FONT=&amp]cat /etc/fstab[/FONT][/COLOR]
```It returns:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=9e33c686-6bfa-4678-b797-22f3dc67e9f3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=B8FE-0FA8  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
```

For ```
[COLOR=#000000][FONT=&amp]cat /etc/apt/sources.list.d[/FONT][/COLOR]
```
It returns:```
cat: /etc/apt/sources.list.d: Is a directory
```

---

### Post by yancek on 2023-09-01
The only entries in fstab are correct for the / (filesystem) and EFI partitions.  There is no need to have an entry in the /etc/fstab file for exernal drives UNLESS they are permanently connected.

Check your /boot/efi/EFI directory to see if there is a Microsoft directory there with its boot files.  Use the following command:

```
sudo mount /dev/nvme0n1p1 /mnt   
```

If the files are there unmount the EFI partition with the commad:

```
sudo umount /mnt
```

Then go to your /boot/grub directory and look in grub.cfg to see if there is an entry for windows.  It it is an EFI entry it should be similar to the one below:

chainloader /EFI/Microsoft/Boot/bootmgfw.efi

Above that line in the windows boot entry you should see a search line with the UUID of the EFI partition nvme0n1p1, in your case.  Make sure it is correct.

---

### Post by gillesdc on 2023-09-01
Thank you for your answer.

There is a Microsoft directory with a boot directory in it, in [COLOR=#000000]/boot/efi/EFI. 

[/COLOR]```
menuentry 'Windows Boot Manager (on /dev/nvme0n1p1)' --class windows --class os $menuentry_id_option 'osprober-efi-B8FE-0FA8' {    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root B8FE-0FA8
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```[COLOR=#000000]
That's what I found in [/COLOR][COLOR=#000000]grub.cfg, that's seems correct to me.[/COLOR]

---

### Post by yancek on 2023-09-01
Yes, it seems correct as that is the UUID for the EFI partition you posted earlier.  While you were in the EFI directory, did you check under Microsoft/Boot to see if the file bootmgfw.efi was there?  I expect it will be.  I'm not sure what the software you used could have changed or if it is coincidental.  If you haven't solved this try running boot repair.  You can get it at the site at the link below.  Use the 2nd option explained on the and when you start it, select the Create BootInfo Summary option and post the link you get when it finishes here.  Make sure you do NOT try to make any repairs as it might create more problems.  Posting here will provide members with experience on the subject to review it and hopefully help you to resolve it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2023-09-01
> **gillesdc said:**
>  Do anyone have an idea to how I could reset the grub to its normal function? 
I assume that you still cannot boot into Windows - is that correct?

I noticed the following line in your /etc/default/grub
```
#GRUB_DISABLE_OS_PROBER=false
```
If you remove the # and then update-grub, your Windows OS should be added to the grub menu.

---

### Post by MAFoElffen on 2023-09-02
Instead of 
```

cat /etc/apt/sources.list.d

```
Please do
```

grep . /etc/sources.list.d/*

```That will print out all the optional repo's that have been added to your system.

It you do
```

history > $HOME/Documents/history.text

```
That will send the history of the last 1000 commands (the default history HISTSIZE, unless set to something else in $HOME/.profile) that you have run from that computer by that user...

---

### Post by gillesdc on 2023-09-06
Sorry for my late response.

@**yancek** There is a [COLOR=#000000] bootmgfw.efi in Microsoft/Boot. I tried to install boot repairs but the terminal is "[/COLOR]Unable to locate package boot-repair".[COLOR=#000000]

@[/COLOR][[COLOR=#000000]tea for one[/COLOR]]("https://ubuntuforums.org/member.php?u=585392")[COLOR=#000000] Yeah I still cann't boot on Windows (or in fact I can but it shows me a bluescreen telling me that the partition is corrupted). So it is already visible on the grub menu. My biggest problem is not really that I can't access to windows (I will just reinstall it that's not a big worry) but that I can't unmount any drive from linux. So I can't get my windows data back or use a flash (which I need every day at work so it's really annoying). 

[/COLOR][COLOR=#000000]@[/COLOR][MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547") Here is the results for the first command:[COLOR=#000000]

[/COLOR]```
grep: /etc/sources.list.d/*: No such file or directory
```[COLOR=#000000]

For the second one, here is the command I used to install orthanc : 

[/COLOR]```
 228  $ sudo apt update  229  sudo apt update
  230  sudo apt install orthanc
  231  sudo apt install orthanc-dicomweb
  232  sudo apt install orthanc-gdcm
  233  sudo apt install orthanc-imagej
  234  sudo apt install orthanc-mysql
  235  sudo apt install orthanc-postgresql
  236  sudo apt install orthanc-python
  237  sudo apt install orthanc-webviewer
  238  sudo apt install orthanc-wsi
  239  sudo service orthanc start
  240  orthanc

  241  sudo service orthanc stop
```

[COLOR=#000000]I think I'll just reinstall the entire operating system to have a new clean one, but if I could copy my data on an hard disk before, it would save me a lot of time.

Thank you so much for your help, appreciate it!
[/COLOR]

---


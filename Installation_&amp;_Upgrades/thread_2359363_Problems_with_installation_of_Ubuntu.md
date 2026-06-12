---
title: "Problems with installation of Ubuntu"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by euan85 on 2017-04-23
First time user of ubuntu and i try to install i keep get getting these messages in the process ...  The creation of swap space in partition #1 of SCSI3 (0,0,0) (sda) failed.

Ive tried reading threads but getting really confused as to different ways of trying to install. Any help would be greatly appreciated.

```
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1002884         4   1002880   1% /dev
tmpfs             203696      6444    197252   4% /run
/dev/sda2      480192508 471183132   9009376  99% /cdrom
/dev/loop0       1462784   1462784         0 100% /rofs
aufs             1018468    537828    480640  53% /
tmpfs            1018468      2592   1015876   1% /dev/shm
tmpfs               5120         8      5112   1% /run/lock
tmpfs            1018468         0   1018468   0% /sys/fs/cgroup
tmpfs            1018468      2104   1016364   1% /tmp
tmpfs             203696       140    203556   1% /run/user/999
```

---

### Post by RobGoss on 2017-04-23
Hello and welcome to the forum, What version of Ubuntu are you trying to install?

It's a good practice to provide the machine **specs** in order to trouble shoot your issues

---

### Post by euan85 on 2017-04-23
hello and thanks bud, ubuntu 16.04 lts. ok my machine specs are :
 memory 1.9 GiB
processor Intel celeron (R) CPU E3300 @ 250 Ghz x2
Graphics Intel g33
OS 64 bit
Disk 1.0 Gb

thanks for your help

---

### Post by RobGoss on 2017-04-23
> Disk 1.0 Gb

Am I seeing this correctly, is that how much disk space you have on that drive?

How does the live desktop run when you boot it?

---

### Post by euan85 on 2017-04-23
Yeah i just typed what i seen is this incorrect or not enough memory, im using ubuntu atm but think its demo version because i cant seem add updates like chrome, adobe flash etc, i get so far in installation then it informs me i cant create partition space once i complete installation, i dont know if i have the complete download on my stick which is is 512mb is this mb the reason i cant do additional updates ?

---

### Post by RobGoss on 2017-04-23
> ubuntu atm but think its demo version because i cant seem add updates like chrome, adobe flash etc

I have no clue what Ubuntu ATM is I've never used it so I cannot help you with it, if you are using any kind of live demo you cannot install any programs on that demo

I'm a bit confused, you stated you only have **1.0 Gb** disk space on that drive 

Your post is confusing because you don't mention what version of Ubuntu you are using

How did you create the USB or DVD, to install Ubuntu on your machine

Do you currently have Ubuntu installed on your machine and can it boot to the desktop

Please give in detail what you've done to install Ubuntu step by step, post**#3 **shows you have **1.9 GB** of memory I don't know were the **512-MB** comes from please clarify

Here are a few good guides that will help if you need assistance

How to install Ubuntu:  [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Creating partitions: [https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)

---

### Post by euan85 on 2017-04-23
I am on the ubuntu desktop at the moment (atm) this is what i am using but i cannot install updates etc, i presume i am using the demo version because i canoot install updates like chrome like i said but they are not installing so i am curious as to what i am mean to do now, the usb i used to boot 512mb and the 1.0gb is what it says on the specs

---

### Post by RobGoss on 2017-04-23
Please run the following commands and post the results using the code tags, if you need more information on how to use code tags see here [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

```
lsb_release -a 
``` 

```
 lspci
```

---

### Post by euan85 on 2017-04-23
```
ubuntu@ubuntu:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
```

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
03:02.0 Ethernet controller: Qualcomm Atheros AR2417 Wireless Network Adapter [AR5007G 802.11bg] (rev 01)
```

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9498cb71

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1           2048  16386047  16384000  7.8G 27 Hidden NTFS WinRE
/dev/sda2  *    16386048 976771071 960385024  458G 83 Linux

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1002884         4   1002880   1% /dev
tmpfs             203696      8964    194732   5% /run
/dev/sda2      480192508 471183132   9009376  99% /cdrom
/dev/loop0       1462784   1462784         0 100% /rofs
aufs             1018468    266184    752284  27% /
tmpfs            1018468     20168    998300   2% /dev/shm
tmpfs               5120         8      5112   1% /run/lock
tmpfs            1018468         0   1018468   0% /sys/fs/cgroup
tmpfs            1018468       324   1018144   1% /tmp
tmpfs             203696        96    203600   1% /run/user/999
```

---

### Post by ian-weisser on 2017-04-23
> **euan85 said:**
> **aufs**             1018468    266184    752284  27% /
aufs for the root filesystem.
That usually means you are booting from your LiveUSB, not the installed system.

Try booting from your installed system.

---

### Post by Autodave on 2017-04-23
Did you install this onto your hard drive or are you running it from a DVD disk or USB thumb drive?

---


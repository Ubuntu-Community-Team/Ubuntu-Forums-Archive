---
title: "Grub problem - WinXP + Hardy Heron"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by stesosaso on 2008-04-27
First of all I would like to precise that I am french. Knowing that i hope you will appologise my non perfect english language and spelling.

The origin of my problem : A month ago I installed Gusty Gibbon on my machine (A7N8X-X - Athlon Xp 2200+ - 3Gb RAM - Geforce 6200 - 2x Samsung Syncmaster 206BW) where Windows XP Pro is already installed on Hd0,0. Installation made without any problem, Grub running

On 24th, I donloaded Hardy Heron DVD via torrent.

I have choosen to replace Gusty Gibbon by deleting the partitions where it was installed (ie hd0,2 ; hd0,3). The mater disk of the master mother board IDE bus contains on it's first partition Win XP pro, on the second partition was the swap, on the third was /.

with the partitionning tool of the live DVD I've deleted the partitions belonging to Ubuntu 7.10. and then run the install of Hardy Heron. I prefered starting an installation from scratch because I have "played" to mutch with Gusty Gibbon and it became instable.

Once installed the installation process asks to reboot in order to run the installed OS
I am rebboting, grub starts and displays the following error : **error 1[B]7**
[/B]Starting back on the live DVD of Hardy Heron I found some solution on different forums. I have choosen to use the following solution :

Using the fixmbr command of the original WinXp Pro CD by choosing repair in the installation process of XP.
This done, Win XP Pro does boot witout any problem.
Then I used smartfdisk in order to remove the installed Hardy Heron partitions.

Then I started again the live DVD 8.04 in order to install and create manually the partitions of Hardy Heron with it's partitionning tool as follow :

swap : 3Gb
/  20Gb
/home  about 80Gb

After installation done the process asks again for reboot.
After rebbot i got the following error message : error loading operating system.

back again on the live DVD searching the forums, I've found a solution that consists of using the fixboot command of the original Win Xp CD by choosing the repair process.
this done, I reboot and still got the same error message : error loading operating system...

At that point my thoughts are : he trys to boot on the wrong hard disk...

back on the live DVD, found the supergrub tool and run on this tool the **grub=>MBR=>Linux auto** command. This done the grub menu is restored and I ask for booting on the Hardy Heron install.
Grub returns following error message :  "**no such partition**" 

Back on the live DVD I run following command in the terminal :

**sudo fdisk -l**

result : 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/sda: 122.9 Go, 122942324736 octets
255 heads, 63 sectors/track, 14946 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xd5109537

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS

Disque /dev/sdb: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x74630db1

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1       13054   104856223+   7  HPFS/NTFS
/dev/sdb2           13055       30401   139339777+   f  W95 Etendu (LBA)
/dev/sdb5           13055       30401   139339746    7  HPFS/NTFS

Disque /dev/sdc: 163.9 Go, 163928604672 octets
255 heads, 63 sectors/track, 19929 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xf040f040

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1   *           1        6387    51303546    7  HPFS/NTFS
/dev/sdc2            6388        6752     2931862+  82  Linux swap / Solaris
/dev/sdc3            6753       19929   105844252+   5  Extended
/dev/sdc5            6753       10399    29294496   83  Linux
/dev/sdc6           10400       19929    76549693+  83  Linux

Disque /dev/sdd: 122.9 Go, 122942324736 octets
255 heads, 63 sectors/track, 14946 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x515a9f1d

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdd1               1        7649    61440561    7  HPFS/NTFS
/dev/sdd2            7650       14946    58613152+   f  W95 Etendu (LBA)
/dev/sdd5            7650       14946    58613121    7  HPFS/NTFS
ubuntu@ubuntu:~$
```and then a [B]
sudo grub --batch
grub> find /boot/grub/stage1[/B]
result :```
ubuntu@ubuntu:~$ sudo grub --batch
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,4)
grub>
```and also here's the content of my menu.lst

```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd2,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professionnel
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```My thougths are that grub trys to acces hd2 as the boot disk and this is wrong hd0 is the boot disk. partitions numering is OK in all files just the disk adress isn't thr right one.

As I am not really familiar with the use of the terminal, could you please explain me :
1..- what schould I do in order to get the right disk requested for boot?
2.- how can I gain access to the menu.lst file on my Hardy heron install (using the text editor I get "you don't have the rights to write..."

For the french speaking people here's the link to the french forum post :
[http://forum.ubuntu-fr.org/viewtopic.php?id=211771](http://forum.ubuntu-fr.org/viewtopic.php?id=211771)

Thanks in advance for your help and advise. 
As sayed, I am not familiar with the terminal, so please be detailed in the things I should do in order to repair the mess I have done on my computer.

but my convictions are : Ubuntu is for me **THE** OS !

---

### Post by Herman on 2008-04-27
:) Hello stesosaso,
One good way to solve this kind of problem is to press your 'c' key from your GRUB menu to get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
When you have the grub> prompt you can type commands after it and make GRUB do all the work for you, looking around to see where your other GRUB files are.
Here are the commands I would use,
```
find /vmlinuz
```That command will search your computer and tell you what partition it finds a symlink to a Linux kernel in.
You can use that partition number for the next command.
```
root (hdx,y)
```Where" x is the hard disk number and y is the partition number you have from the earlier command.
```
find /sbin/init
```The answer this will return is telling you what partition is your / (root) partition for Ubuntu, you need to know that but GRUB will give it to you in GRUB's (hdx,y) type of notation and you will need to convert that to Linux notation like: /dev/sdx,y)
Here is a link to a table for converting in case you're not sure how to do that, [Quick Guide to GRUB's Numbering System.]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

Okay, you place that /dev/sdx,y type number after 'root=' in the next command,
```
kernel /vmlinuz root=/dev/sdx,y
```Where: /dev/sdx,y or /dev/hdx,y is your Ubuntu / (root) partition in Linux's numbering system.

The rest is simple,
```
initrd /initrd.img
``````
boot
```That should boot Ubuntu for you.
Remember the hard disk number you needed to use and edit your /boot/grub/menu.lst file with that partition number when you have Ubuntu booted up.

If that doesn't work then maybe you need to run a file system check instead, if the file system is a little mixed up that can cause GRUB error 17 too.

Good Luck,
Regards, Herman :)

---

### Post by stesosaso on 2008-04-27
Thank you very mutch Herman for your help.

One thing is strange to me, maybe you have the answer :

I have tried you grub command  **find /vmlinuz**.
here is what it finds :
```
grub> find /vmlinuz
find /vmlinuz
 (hd2,4)
grub>
```That is not right for me because the partition where Ubuntu Hardy Heron is installed is the 4th partition of the master disk on the primary motherboard IDE bus. Therfore the answer schould be (hd0,4).

doing I am right in thinking this way ?
How can I fix that if my thougths were right ?

many thanks in advance for youy help and advise

---

### Post by Herman on 2008-04-27
Well you are correct, but there is a problem with computers and their different BIOSes and the way the BIOS tells GRUB which hard disks are which. 
This doesn't happen when there are only SATA disks in the computer or only PATA (IDE) disks, but when there are a mixture, the problem often occurs.

 It seems as if the majority of computers in the world have BIOSes that give GRUB the information that all SCSI or SATA disks are listed first, before the IDE or PATA disks, and other times it is the PATA disks that the BIOS sets first.
Probably it's more complicated than that, but I don't have an understanding of the exact details, and most people would find it boring if I did know exactly.
Anyway, it's a difficult problem for GRUB, because they can't make GRUB work perfectly for all the computers in the world. If they switch it to the other way, there will be even more people with hard disk numbering confusion.

There can also be confusion of IDE drives are not plugged in and jumpered correctly, and if people switch their hard drive sequences around in thier BIOS as well, (and then forget they did that).

It's normally just easier to type the 'wrong' numbers into GRUB's /boot/grub/menu.lst so GRUB will be happy, as long as your computer boots okay.

If there is only two hard drives in the computer, a good solution is to switch the hard drive order in the BIOS, and that way it is not necessary to edit any files. 
If there are more than two hard disks, then it's easier to edit the /boot/grub/menu.lst file.

Regards, Herman :)

EDIT: I looked back and I can see that your /boot/grub/menu.lst already had (hd2,4) for Ubuntu.
In that case maybe you just need a file system check.

Here is my favorite command to be run from a Live CD for a file system check, that might fix it,
```
sudo e2fsck -C0 -p -v -f  /dev/sdc5
```

---

### Post by stesosaso on 2008-04-27
Thanks Herman,

Here's the result of : **sudo e2fsck -C0 -p -v -f  /dev/sdc5**
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f  /dev/sdc5
                                                                               
  110934 inodes used (6.05%)
     136 non-contiguous inodes (0.1%)
         # of inodes with ind/dind/tind blocks: 4975/27/0
  624295 blocks used (8.52%)
       0 bad blocks
       1 large file

   83077 regular files
   11607 directories
      69 character device files
      26 block device files
       2 fifos
       3 links
   16144 symbolic links (15158 fast symbolic links)
       0 sockets
--------
  110928 files
ubuntu@ubuntu:~$
```I am not skilled enough to get any info from that command...

All I can tell you is that under Gusty Gibbon my hard drives were recognized as follow :

master disk on master IDE bus hda and the slave as hdb
disk on the master IDE bus of my additional controller wrer recognized as SCSI disk and therfore as sda and sdb

Now sice I am running Hardy Heron all disk are marked as SCSI and those from the additional controller are marked as sda and sdb and those on the mother board master ide bus as sdc and sdd...

Looks like hardy does not recognize them in the same way...

I made a small table giving a correspondance between dos and ubuntu namming of the hard drives :

```

               DOS             fdisk
IDE MB         d(0)p(1)        sdc1
IDE MB         d(0)p(2)        sdc2 sdc5 sdc6     =>has been repartitionned between the dos and fdisk readings (there are the swap, / et /home)
IDE MB         d(1)p(1)        sdd1
IDE MB         d(1)p(2)        sdd2
IDE Ctrl       d(2)p(1)        sda1 
IDE Ctrl       d(3)p(1)        sdb1
IDE Ctrl       d(3)p(2)        sdb5

Where IDE MB is the Mother board IDE BUS and IDE Ctrl is the master bus of my secondary controller board

```in that table I have only noticed the primary and logical partition declaration.

Have I to tell Hardy heron what is really right in the numbering of my HD ?
If yes, How can I achive that ?
if not where has hardy the correspondance table in order to verify it's intergrity ?

---

### Post by stesosaso on 2008-04-27
One other thing that looks strange to me is that the command **sudo fdisk -l** returns me two boot partitions (amorce in french) the first on **sda1** and the second on **sdc1**.

**sda1** is not right the **sdc** disk is the **hd0** and therfore **sdc1** and **sdc5** schould be marked as boot no?

I also looked at the BIOS (Phoenix - award BIOS CMOS  rev 1010 on my ASUS A7N8X-X motherBoard)
The hard disk declared as disk to boot on is HD-0 (HD-1, HD-2 and HD-3 are not declared as such)

Could it be possible that due to all my mistakes a part of Grub could have been installed on the **sda** (hd3) disk?

---

### Post by Herman on 2008-04-27
The good new is your file system check was successful, so  if you still can't boot then it doesn't seem as if the file system in the problem.

So, you have all IDE hard disks?
Maybe you have some problem with the way they are plugged in an jumpered?
But if they were okay under Gutsy and you haven't changed anything and the problem just came up now I'm not sure. 
Have you recently changed or replaced any drives? Even the CD/DVD drive probably has jumpers.

Apart from that I will need to think for a while, I'll be back later on.

Regards, Herman

---

### Post by stesosaso on 2008-04-27
Yes Herman, I have all IDE disks 

In details 

Motherboard Master IDE Bus 2 disks
Motherboard Secondary bus 2 DVD burners
Additional IDE controller board master Bus : 2 disks
Additional IDE controller board secondary bus : nothng

I have, under Gusty Gibbon replaced one of the DVD drives, the slave one by a news slave one (I have controlled the jumpers) without any problem. in the mean time I have also replaced the old 512 Mb Ram with 3 brand new 1 Gb Ram borads (those are for sure compatible with the mother board as it is well known that the Asus A7N8X-X is very sensible about the ram quality. I have installed 3x Corsair Value select 1Gb DDR-SDRAM PC 3200 CL3-VS1GB400C3).

Don't wory about the time, I am vorking with computer before windows was even available, discovered windows 1.0, all DOS versions, Apple IIe, and since the last 20 years all the Windows versions with diffrent PCs 8086, 80186, 80283, 80386, dx 33 dx400, Pentium 75, 100, 133, PII, PIII, AMD athon XP, PIV, and now Mac Book Pro.
Since the launch of Vista I am totally upset with that OS, takes that much power for nothing, maybe just forcing you to upgrade the hardware...

So last month, beeing blocked at home because of my back blocked due to a slipped disc on the spinal column (hope that this is the right translation of "hernie discale" in french) I have decided to give a try to linux, found very good comments about Ubuntu around the WEB, and choose to install Gusty Gibbon with grub as a multiboot on my old Athlon Xp 2200+.
I vas amayzed by how simple I could get involved into it, how simple and logical all that is.
I have played allot with it, with it's software etc... Now I am convinced that this is the OS I will teach my kids on. I love the all free approach, low level ressources needed to get all done with lot of fun and even some times more possibilities as with the expensive Vista. I have played that much with Gusty Gibbon that it became instable, so last 24th I decided to format all the linux part and install Hardy Heron from scratch.

So all that to say that time is not a problem, I just wanna understand clearlly what's happening, and not just copying command lines, great people on the diffrents forums could give me as a solution to my actual problem. 

Again I thank you very much for your help and advises, hopping just that my english is not that bad, and relates my real thoughts  :)

---

### Post by stesosaso on 2008-04-27
Herman, after reading your comments and advises i have made following changes :

1. I removed the secondary IDE controller leaving the IDE buses on my machine as follows :
Primary MB IDE bus : 
master = (hd0) partitioned as follows :

1.- primary partition with Win XP Pro installed  (NTFS)
2.- primary partition : SWAP
3.- extended partition
4.- logical drive : /  (ext3)
5.- logical drive : /home  (ext3)

Slave disk = (hd1) partitioned as follows :

1.- primary partition (NTFS) : data
2.- extended partition
3.- logical drive : (NTFS) data

Secondary MB IDE bus :

master : DVD drive
Slave : DVD drive

here some infos from my Hardy Heron :

```
saks@saks-ubuntu-hh:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 0650DEFC50DEF183 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 1434E86334E848F6 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 4f23f857-5e51-47ce-80e3-1174474fc016 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 8955d0a0-ea4d-4e85-a062-10273e8efd8b -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 9014F99014F97994 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-28 01:44 c30b27a7-8b8e-4abb-abf6-111d7e0036f9 -> ../../sda2
saks@saks-ubuntu-hh:~$ 

``````
saks@saks-ubuntu-hh:~$ sudo fdisk -l
[sudo] password for saks: 

Disque /dev/sda: 163.9 Go, 163928604672 octets
255 heads, 63 sectors/track, 19929 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0xf040f040

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        6387    51303546    7  HPFS/NTFS
/dev/sda2            6388        6752     2931862+  82  Linux swap / Solaris
/dev/sda3            6753       19929   105844252+   5  Extended
/dev/sda5            6753       10399    29294496   83  Linux
/dev/sda6           10400       19929    76549693+  83  Linux

Disque /dev/sdb: 122.9 Go, 122942324736 octets
255 heads, 63 sectors/track, 14946 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x515a9f1d

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       14946    58613152+   f  W95 Etendu (LBA)
/dev/sdb5            7650       14946    58613121    7  HPFS/NTFS
saks@saks-ubuntu-hh:~$ 
```and my menu.lst :

```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd2,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professionnel
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```I am running now on the installed Hardy heron and no more on the live DVD.
I could do that with Supergrub by changing on the fly root (hd2,4) into  root (hd0,4).
after that change made, grub could boot on the right disk, before the chage, grub's error message was like "no such disk".

Now, shouldn't I make the following change in my menu.lst ?
(changes are highlighted in bold text)

> ## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd**0**,4)          **=>****0 instead of**** 2**
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd**0**,4)          **=>0 ****instead of**** 2**
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=8955d0a0-ea4d-4e85-a062-10273e8efd8b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd**0**,4)          **=>0 ****instead of**** 2**
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professionnel
root        (hd**0**,0)          **=>0 instead of 2**
savedefault
makeactive
**#**map        (hd0) (hd2)                   **=>add # at the beginning of the line (convert into comment)**
**#**map        (hd2) (hd0)                   **=>****add # at the beginning of the line ****(convert into comment)**
chainloader    +1if that is right, what kind of tool should I use regarding my limited competencies in terminal mode and the access level needed to be able to make those changes?

Again thanks for your appreciated help and advise

EDIT : problem solved !

I used following terminal command in order to make the changes I have highlighted above :
```

gksudo gedit /boot/grub/menu.lst

```

I saved the changes, rebooted the computer and anything went right.
I reconnected the secondary IDE controller, rebooted the computer and still anything is OK all drives are accessible and running.

Many thank for your help **Herman**. As a friend of me likes to say "Solidarity and share are the secrets of LINUX"

---

### Post by Herman on 2008-04-28
:) Well done, stesosaso, congratulations, you were able to solve your problem yourself! :)

Thanks for sharing what you needed to do to solve it, that will probably help someone else with the same problem some day.  You have taught me some interesting new ideas.

By the way, your English is very good, I can understand you better, I feel, than many people whose only language in English. :)

Regards, Herman :)

---


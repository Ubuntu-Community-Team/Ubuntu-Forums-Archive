---
title: "Grub Loading Failure"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by LarCrow on 2009-12-08
After trying ubuntu 9.10 on an old workhorse 386 (directly from the CD) I then installed it and the process went OK until I attempted to boot from the harddrive.  It got to the place where it said " GRUB Loading" and the screen went blank and it was all over.  

In all 3 attempts were made devoting the entire harddrive to ubuntu.   From some of the posts I've read it seems that ubuntu is probably intact but this GRUB loader is missing.   How can I fix this?

---

### Post by sikander3786 on 2009-12-08
Are you dual booting?

I assume if the the GRUB Loading... text shows up, the problem should not be with GRUB.

Anyhow you can restore GRUB by following the instructions below.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LarCrow on 2009-12-08
Thanks for the feedback.  It's not dual boot.  I tried the procedure you referenced by using terminal to enter "sudo grub" and I got back "sudo: grub: command not found".  If I type in grub by itself it says grub is not installed and that I can install it by typing "sudo apt -get install grub" and when I do it comes back with sudo: apt: command not found.

---

### Post by raygj on 2009-12-08
> **LarCrow said:**
> Thanks for the feedback.  It's not dual boot.  I tried the procedure you referenced by using terminal to enter "sudo grub" and I got back "sudo: grub: command not found".  If I type in grub by itself it says grub is not installed and that I can install it by typing "sudo apt -get install grub" and when I do it comes back with sudo: apt: command not found.
typing "sudo apt -get install grub" is wrong.
typing "sudo apt-get install grub" is the correct way to install grub ver1.
typing "sudo apt-get install grub-pc" is the  way to install grub2.
Note if you are not dual booting ,ubuntu with mswindows,then the default action of grub is to not show a boot selection screen menu.IT jumps straight into ubuntu.the installer on "new install" automatically installs grub2.
because 'it says grub is not installed and that I can install it by typing "sudo apt-get install grub"' you seem to be logged into  ubuntu.
try typing "startx" to bring up the "GDI(graphical desktop interface)"

---

### Post by LarCrow on 2009-12-09
Thanks, when I correctly typed "sudo apt-get install grub" I got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? 

I said yes and 

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub 0.97-29ubuntu59 [407kB]
Fetched 407kB in 2s (189kB/s)                       
Preconfiguring packages ...
(Reading database ... 120318 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package grub.
(Reading database ... 120136 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu59) ..

At that point I typed "startx"

ubuntu@ubuntu:~$ startx

X: user not authorized to run the X server, aborting.
ubuntu@ubuntu:~$ 

So I'm totally confused as to how to proceed

---

### Post by darkod on 2009-12-09
> **LarCrow said:**
> Thanks, when I correctly typed "sudo apt-get install grub" I got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? 

I said yes and 

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub 0.97-29ubuntu59 [407kB]
Fetched 407kB in 2s (189kB/s)                       
Preconfiguring packages ...
(Reading database ... 120318 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package grub.
(Reading database ... 120136 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu59) ..

At that point I typed "startx"

ubuntu@ubuntu:~$ startx

X: user not authorized to run the X server, aborting.
ubuntu@ubuntu:~$ 

So I'm totally confused as to how to proceed

With this you just replaced grub2 with grub1. But that should still work. The initial problem doesn't seem to be grub. Now when you reboot after this, what happens?

---

### Post by LarCrow on 2009-12-10
> **darkod said:**
> With this you just replaced grub2 with grub1. But that should still work. The initial problem doesn't seem to be grub. Now when you reboot after this, what happens?

The same thing I got previously when it starts to boot from the harddrive it says " GRUB Loading" and the screen goes blank and it's all over with no further action of the harddrive..

---

### Post by rajesh88 on 2009-12-10
hello, 
i have followed the instruction mentioned in below link.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
but still i am facing the same problem! Why i am seeing so many genric versions on boot screen? Is this problem with GRUB or wubi? Is there any permanent fix for this? I have been using ubuntu from past six months(wubi 9.04 and 9.10). I never face this kind of problem. Please help me out. Thanks in advance

---

### Post by darkod on 2009-12-10
> **rajesh88 said:**
> hello, 
i have followed the instruction mentioned in below link.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
but still i am facing the same problem! Why i am seeing so many genric versions on boot screen? Is this problem with GRUB or wubi? Is there any permanent fix for this? I have been using ubuntu from past six months(wubi 9.04 and 9.10). I never face this kind of problem. Please help me out. Thanks in advance

First of all, you are jumping into someone elses thread which has nothing to do with your problem.
Second, you didn't even explain if you have a problem. After an update with a new kernel, old kernels are not removed automatically in ubuntu. That is not a problem. If you want to remove them from the list, google removing old kernel versions. But you should keep at least one older kernel, that's recommended.

---

### Post by presence1960 on 2009-12-10
> **LarCrow said:**
> The same thing I got previously when it starts to boot from the harddrive it says " GRUB Loading" and the screen goes blank and it's all over with no further action of the harddrive..

Let's not speculate as to what your setup & boot process looks like. We need more concrete info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2009-12-10
> **darkod said:**
> First of all, you are jumping into someone elses thread which has nothing to do with your problem.
Second, you didn't even explain if you have a problem. After an update with a new kernel, old kernels are not removed automatically in ubuntu. That is not a problem. If you want to remove them from the list, google removing old kernel versions. But you should keep at least one older kernel, that's recommended.

+1 

start your own thread please. It is difficult to help more than one person on the same thread with even the same problem, let alone a totally different issue. it is not fair to the OP or to you or to those trying to help both of you. Darko definitely has more patience than I do.

---

### Post by darkod on 2009-12-10
> **LarCrow said:**
> The same thing I got previously when it starts to boot from the harddrive it says " GRUB Loading" and the screen goes blank and it's all over with no further action of the harddrive..

Can you select the entry in the grub menu which says recovery mode? If you can, it will execute some commands and load a menu to select something like "root with networking" and then open a command prompt for you. The recovery mode doesn't load desktop GUI.
Try it just to see if it will boot.
If it loads the command prompt you can do:
sudo reboot

to restart with the LiveCD so that you can post back what happened.

---

### Post by LarCrow on 2009-12-10
> **presence1960 said:**
> Let's not speculate as to what your setup & boot process looks like. We need more concrete info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.
I don't undersand what you mean by "use the link in my signature to download the Boot Info Script to the desktop".    I did boot from the CD and ran " 
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
 but it came back with
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by darkod on 2009-12-10
> **LarCrow said:**
> I don't undersand what you mean by "use the link in my signature to download the Boot Info Script to the desktop".    I did boot from the CD and ran " 
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
 but it came back with
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$

Click the link Boot Info Script in his signature (or mine). It will download a script, probably in Places-Downloads. Move it to desktop and execute that command. It will create a file results.txt. From there do as he said, not to repeat it now. :)

---

### Post by presence1960 on 2009-12-10
> **darkod said:**
> Click the link Boot Info Script in his signature (or mine). It will download a script, probably in Places-Downloads. Move it to desktop and execute that command. It will create a file results.txt. From there do as he said, not to repeat it now. :)

Thanks darko

---

### Post by LarCrow on 2009-12-10
I did the best I could and this is how it all came out.  I hope it helps.


#!/bin/bash
#to use this script:
#
#     sudo bash boot_info_script041.sh
#or
#     su -
#     bash boot_info_script_041.sh
#
#date 12/7/09
#
#author  meierfra. 
# with  contributions from caljohnsmith
# (both members of ubuntuforums.org)
# and Gert Hulselmans
#
#version 0.40
#hosted at: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
# 
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#         For NTFS and Fat, examines the Boot Parameter Block for errors.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays the partition table
#   Displays "blkid -c /dev/null"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script.
#    When run from /bin, /sbin, /usr/bin, or other system folder the file
#    "RESULTS.txt" is written to the home dir of the user which runs this script.

###### check whether user is root
if [ $(whoami) != "root" ];
then 
   echo  Please use \"sudo\" or become \"root\" to run this script. >&2;
   exit 1;
fi;  

########  List of folders which might contained files used for chainloading
Boot_Codes_Dir="
    /
    /NST/
    "
#################  List of folders whose content will be displayed
################# Since all the important files in these folder are alreadt displayed
################# it doesn't seem necessary to display the contents of these folders.
#Boot_Dir="
#   /Boot
#    /boot
#    /BOOT
#    /boot/grub
#    /grub
#    /ubuntu/disks
#    /ubuntu/disks/boot/
#    /ubuntu/disks/boot/grub
#    /ubuntu/disks/install/boot
#    /ubuntu/disks/boot/grub
#    /NST
#    "


##############  List of files whose names will be displayed (if they exists)
Boot_Prog="
     /bootmgr /BOOTMGR
     /boot/bcd /BOOT/bcd /Boot/bcd  /boot/BCD /BOOT/BCD  /Boot/BCD
     /Windows/System32/winload.exe /WINDOWS/system32/winload.exe /WINDOWS/SYSTEM32/winload.exe /windows/system32/winload.exe
     /Windows/System32/Winload.exe /WINDOWS/system32/Winload.exe /WINDOWS/SYSTEM32/Winload.exe /windows/system32/Winload.exe
     /grldr /GRLDR
     /ntldr /NTLDR
     /NTDETECT.COM    /ntdetect.com
     /NTBOOTDD.SYS    /ntbootdd.sys
     /wubildr.mbr    /ubuntu/winboot/wubildr.mbr
     /ubuntu/disks/root.disk
     /ubuntu/disks/
     /ubunut/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
     "

############### List of files whose contents will be displayed.
Boot_Files="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    boot/kernel*.img
    "


#######  Directory containing the script.

Dir=$(cd "$(dirname "$0")";pwd);

# Set $Dir to the home folder of the current user if the script is in one of the
# system folders
# This allows placement of the script in /bin, /sbin, /usr/bin, ...
# while still having a normal location to write the output file.
for systemdir in /bin /boot /cdrom /dev /etc /lib /lost+found /opt /proc /sbin /selinux /srv /sys /usr /var; do
    if [ $(expr "$Dir" : $systemdir) -ne 0 ]; then
    Dir="$HOME"
    break
    fi
done

########  To avoid overwriting existing files, look for a non-existing file 
########  RESULT.txt RESULTS1.txt  RESULTS2.txt ... 

LogFile="${Dir}/RESULTS"
while ( [ -e "${LogFile}${j}.txt" ] )
    do  
      ((j++))
      wait;
    done
LogFile="${LogFile}${j}.txt"  #### The RESULTS file.

######  Redirect stdout to RESULT File
exec 6>&1   
exec > "$LogFile"

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
while (! mkdir ${Folder}${i} 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=${Folder}${i}

cd $Folder
Wubi=$Folder/Wubi
mkdir Wubi                      # Folder to mount Wubi installs.
Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.
PartitionTable=$Folder/PT       #  File to store the Partition   Table
FakeHardDrives=$Folder/FakeHD   # File to list devices which seem to have  no corresponding drive.
exec 2>$Error_Log               #Redirect all standard error to the file Error_Log

All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.

####Arrays to hold informttion about Partitions: name, starting sector, ending sector, size in sector, Partition Type, Filesystem typ, UUID, Kind( Logical, Primary Extended), Hardrive, boot flag

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray


#####Arrays to hold information about the hardrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart DEnd HDUUID;

PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hard drive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,
           


##### A function which converts to two digit hexcode of a partition type 
# The follwing list is taken from sfdisk -T  and 
#  [http://www.win.tue.nl/~aeb/partitions/partition_types-1.html]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-1.html")
#  work in progress
function HexToSystem () {
local type=$1 system
case $type in 
0) system="Empty";;
1) system="FAT12";;
2) system="XENIX root";;
3) system="XENIX usr";;
4) system="FAT16 <32M";;
5) system="Extended";;
6) system="FAT16";;
7) system="HPFS/NTFS";;
8) system="AIX";;
9) system="AIX bootable";;
a) system="OS/2 Boot Manager";;
b) system="W95 FAT32";;
c) system="W95 FAT32 (LBA)";;
e) system="W95 FAT16 (LBA)";;
f) system="W95 Ext d (LBA)";;
10) system="OPUS";;
11) system="Hidden FAT12";;
12) system="Compaq diagnostics";;
14) system="Hidden FAT16 <32M";;
16) system="Hidden FAT16";;
17) system="Hidden HPFS/NTFS";;
18) system="AST SmartSleep";;
1b) system="Hidden W95 FAT32";;
1c) system="Hidden W95 FAT32 (LBA)";;
1e) system="Hidden W95 FAT16 (LBA)";;
24) system="NEC DOS";;
27) system="Hidden HPFS/NTFS";;
32) system="NOS";;
35) system="JFS on OS2";;
38) system="Theos";;
39) system="Plan 9";;
3a) system="Theos";;
3b) system="Theos Extended";;
3c) system="PartitionMagic recovery";;
40) system="Venix 80286";;
41) system="PPC PReP Boot";;
42) system="SFS";;
45) system="Boot-US boot manager";;
4d) system="QNX4.x";;
4e) system="QNX4.x 2nd part";;
4f) system="QNX4.x 3rd part";;
50) system="OnTrack DM";;
51) system="OnTrack DM6 Aux1";;
52) system="CP/M";;
53) system="OnTrack DM6 Aux3";;
54) system="OnTrackDM6";;
55) system="EZ-Drive";;
56) system="Golden Bow";;
5c) system="Priam Edisk";;
61) system="SpeedStor";;
63) system="GNU HURD or SysV";;
64) system="Novell Netware 286";;
65) system="Novell Netware 386";;
70) system="DiskSecure Multi-Boot";;
75) system="PC/IX";;
80) system="Old Minix";;
81) system="Minix / old Linux";;
82) system="Linux swap / Solaris";;
83) system="Linux";;
84) system="OS/2 hidden C: drive";;
85) system="Linux extended";;
86) system="NTFS volume set";;
87) system="NTFS volume set";;
88) system="Linux plaintext";;
8e) system="Linux LVM";;
93) system="Amoeba/Accidently Hidden Linux";;
94) system="Amoeba BBT";;
9f) system="BSD/OS";;
a0) system="IBM Thinkpad hibernation";;
a5) system="FreeBSD";;
a6) system="OpenBSD";;
a7) system="NeXTSTEP";;
a8) system="Darwin UFS";;
a9) system="NetBSD";;
ab) system="Darwin boot";;
af) system="HFS";;
b0) sytem="Boot Star";;
b1 | b2 | b3 | b4 | b6) system="SpeedStor";; 
b7) system="BSDI fs";;
b8) system="BSDI swap";;
bb) system="Boot Wizard hidden";;
bc) system="Acronis BackUp";;
be) system="Solaris boot";;
bf) system="Solaris";;
c0) system="CTOS";;
c1) system="DRDOS/sec (FAT-12)";;
c2) system="Hidden Linux/PowerBoot";;
c3) system="Hidden Linux Swap /PowerBoot";;
c4) system="DRDOS/sec (FAT-16 < 32M)";;
c6) system="DRDOS/sec (FAT-16)";;
c7) system="Syrinx";;
cb) system="DR-DOS  FAT32 (CHS)";;
cc) system="DR-DOS  FAT32 (LBA)";;
cd) system="CTOS Memdump?";;
ce) system="DR-DOS FAT16X (LBA)";;
cf) system=" DR-DOS EXT DOS (LBA)";;
d0) system=" REAL/32 secure big partition";;
da) system="Non-FS data";;
db) system="CP/M / CTOS / ...";;
dd) sysetm="Dell Media Direct";;
de) system="Dell Utility";;
df) system="BootIt";;
e1) system="DOS access";;
e3) system="DOS R/O";;
e4) system="SpeedStor";;
eb) system="BeOS fs";;
ee) system="GPT";;
ef) system="EFI (FAT-12/16/32)";;
f0) system="Linux/PA-RISC boot";;
f1) system="SpeedStor";;
f4) system="SpeedStor";;
f2) system="DOS secondary";;
fb) system="VMware VMFS";;
fc) system="VMware VMKCORE";;
fd) system="Linux raid autodetect";;
fe) system="LANstep";;
ff) system="BBT";;
 *) system="Unknown";;
esac;
echo $system;
}

##### Function to convert GPT's Partition Type.
function UUIDToSystem() {
local type=$1 system
case $type in
    00000000000000000000000000000000)  system="Empty";;
    41ee4d02e733d3119d690008c781f39f)  system="MBR partition scheme";;
    28732ac11ff8d211ba4b00a0c93ec93b)  system="System/Boot Partition";;
    a2a0d0ebe5b9334487c068b6b72699c7)  system="Linux (usually)";; 
    6dfd5706aba4c44384e50933c84b4f4f)  system="Linux Swap";;
    16e3c9e35c0bb84d817df92df00215ae)  system="Microsoft Windows";;
    79d3d6e607f5c244a23c238f2a3df928)  system="LVM";;
    005346480000aa11aa1100306543ecac)  system="HFS+";;
                                   *)  system="-";
                                       echo Unknown GPT Partiton Type>>$Unknown_MBR;
                                       echo  $type >>$Unknown_MBR;;   
esac;
echo $system;
   }

##### Function which insert a comma every  third digits of a number
function InsertComma () {
echo $1 |sed -e :a -e 's/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/;ta'
}

##### Function to read 4 bytes starting at $1 of device $2 and convert to decimal.
function Read4Bytes () {
echo $(hexdump -v -s  $1  -n 4 -e '4 "%u"'  $2);
}

##### Function to read 8 bytes starting at $1 of device $2 and convert to decimal.
function Read8Bytes () {
local start=$1 device=$2;
local first4 second4;
first4=$(hexdump -v -s  $start  -n 4 -e '4 "%u"'  $device);
second4=$(hexdump -v -s  $((start+4))  -n 4 -e '4 "%u"'  $device);
echo $((second4*1073741824+first4));
}

## Reads and display the  a partition table of an extended partitons    ###########
#############  and check it for errors                       #####################
#  This function can be applied iteratively  to read the extended partiton table           
# Variable 1:  HI of hard drive 
# Variable 2:  Start Sector of the extended Partition,
# Variable 3:  Number of partitions in table (4 for regular PT, 2 for logical
# Variable 4:  File for storing the partitions table.
# Variable 5:  Format to use for displaying the partition table.  
# Variable 6:  PI of the primary extended partition containing the extended partition.
#              ""  for hard drive
# Variable 7:  Last Linux Index assigned (the number in sdXY).

ReadPT (){
local HI=$1 StartEx=$2   N=$3 PT_file=$4 format=$5  EPI=$6 Base_Sector  
local   LinuxIndex=$7  boot  size   start end type drive system;
local i=0  boot_hex label limit MBRSig
drive=${HDName[$HI]};
limit=${HDSize[$HI]};
$(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
MBRSig=$(hexdump -v -s 510  -n 2 -e '"%x"'  $Tmp_Log);
[[ "$MBRSig" != "aa55" ]]  && echo  Invalid MBR Signature found >> $PT_file;
if [[ $StartX -lt $limit ]];
then  # set Base_Sector to 0 for HardDrive, and to the start
      # sector  of primary extented partition otherwise
    [[ "$EPI" = "" ]] && Base_Sector=0 || Base_Sector=${StartArray[$EPI]}
    for (( i=0; i < N; i++ ));
    do
    $(dd if=$drive skip=$StartEx of=$Tmp_Log count=1 2>>$Trash);
        boot_hex=$(hexdump -v -s  $((446+16*i))  -n  1 -e '"%02x"'  $Tmp_Log)
    case $boot_hex  in
        00) boot=" ";;
        80) boot="* ";;
        *) boot="?";;
    esac;
    start=$(hexdump -v -s  $((454+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
    size=$(hexdump -v -s  $((458+16*i))  -n 4 -e '4 "%u"'  $Tmp_Log);
    type=$(hexdump -v  -s  $((450+16*i))  -n 1 -e '4 "%x"' $Tmp_Log);
    if  [[ $size != 0 ]];
    then
        if  [[ ( "$type" = "5" || "$type" = "f" )  && $Base_Sector != 0 ]];
        then
        start=$((start+Base_Sector))  #start sector of an extended partition is 
                # relative to the start sector of an primary extended partition.
        ReadPT $HI $start  2  $PT_file "$format"  $EPI $LinuxIndex;
        else  
        ((PI++))  
        if  [[ "$type" = "5" || "$type" = "f" ]];
        then
                    KindArray[$PI]="E";
        else
            start=$((start+StartEx)); #Start sector of a logical partition is
            # relative to the start sector of directly assocated  extented partition.
            [[ $Base_Sector = 0 ]] && KindArray[$PI]="P" || KindArray[$PI]="L";
        fi;
        LinuxIndex=$((LinuxIndex+1));
        end=$((start+size-1));
        [[ "${HDPT[$HI]}"  = "BootIt"  ]] && label="${NamesArray[$EPI]}""_" || label=$drive;
        system=$(HexToSystem $type)

        printf "$format" "$label$LinuxIndex" "$boot" $(InsertComma $start) "$(InsertComma $end)"  "$(InsertComma $size)"  "$type" "$system" >> $PT_file;
        NamesArray[$PI]="$label"$LinuxIndex;
        StartArray[$PI]=$start;
        EndArray[$PI]=$end;
        TypeArray[$PI]=$type;
        SystemArray[$PI]="$system";
        SizeArray[$PI]=$size;
        BootArray[$PI]="$boot";
        DriveArray[$PI]=$HI;
        ParentArray[$PI]=$EPI;

        if [[ "$type" = "5" || "$type" = "f" ]];
        then
                ReadPT $HI $start  2  $PT_file "$format"  $PI 4;
        fi;
        fi;
       
    elif [[ $Base_Sector != 0  &&  $i = 0  ]];
    then
        echo "Empty Partition">>$PT_file;
    else 
        LinuxIndex=$((LinuxIndex+1));
    fi;
    done;
else
    echo "EBR refers to a  location outside the Hard drive" >>$PT_file;
fi;  
}
############### Read partition table of type GPT (GUID, EFI)##########################
######  Variable 1:  HI of hard drive
######  Variable 2:  File to store the PartitionTable
function ReadEFI() {
    local HI=$1 drive file=$2 Size N=0 i=0  format Label PRStart Start End  Type Size System;
    drive="${HDName[$HI]}";
    format='%-10s %14s%14s%14s %s\n';
    printf "$format"  Partition Start End Size  System >> $file;
    HDStart[$HI]=$(Read8Bytes  552   $drive);
      HDEnd[$HI]=$(Read8Bytes  560   $drive);
     HDUUID[$HI]=$(hexdump -v -s 568   -n 16 -e '/1 "%02x"'  $drive); 
         PRStart=$(Read8Bytes  584    $drive);
               N=$(Read4Bytes  592   $drive);
          PRStart=$((PRStart*512));
          PRSize=$(Read4Bytes 596    $drive);
    for (( i = 0; i< N; i++ ))
    do
        Type=$(hexdump -v -s $((PRStart+PRSize*i))  -n 16 -e '/1 "%02x"'  $drive);
    if [ "$Type" != "00000000000000000000000000000000" ];
    then
        ((PI++))
         
    Start=$(Read8Bytes $((PRStart+32+PRSize*i))   $drive);
      End=$(Read8Bytes $((PRStart+40+PRSize*i))   $drive);
        Size=$((End-Start+1));
        System=$(UUIDToSystem $Type);
        Label=$drive$((i+1));
        printf "$format"  "$Label"  "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)"  "$System"  >>$file;
        NamesArray[$PI]=$Label;
        StartArray[$PI]=$Start;
        TypeArray[$PI]=$Type;
        SizeArray[$PI]=$Size;
        SystemArray[$PI]=$System;
        EndArray[$PI]=$End;
        DriveArray[$PI]=$HI;
        KindArray[$PI]="P";
        ParentArray[$PI]=""; 
     fi;        
     done;
}

############### Read the Master Partition Table of  BootIt NG##########################
######  Variable 1:  HI of hard drive
######   Variable 2:  File to store the MPT.
function ReadEMBR() {
    local HI=$1 drive MPT_file=$2 Size N=0 i=0  BINGIndex  Label   Start End  Type BINGUnknown format Size System;
    drive="${HDName[$HI]}";
    format='%-18s %4s%14s%14s%14s %3s %-15s %3s %2s\n';
    printf "$format"  Partition Boot Start End Size Id System  Ind "?">> $MPT_file; 
    N=$(hexdump -v -s 534  -n 1 -e  '"%u"' $drive); 
    while [[ $i -lt "$N" ]]
    do
        ((PI++))
        BINGUnknown=$(hexdump -v -s  $((541+28*i))  -n 1 -e '"%x"'  $drive)
    Start=$(hexdump -v -s  $((542+28*i))  -n 4 -e '4 "%u"'  $drive);
      End=$(hexdump -v -s  $((546+28*i))  -n 4 -e '4 "%u"'  $drive);
    BINGIndex=$(hexdump -v -s  $((550+28*i))  -n 1 -e '"%u"'  $drive);
    Type=$(hexdump -v -s  $((551+28*i))  -n 1 -e '"%x"'  $drive);
        Size=$((End-Start+1));
    Label=$(hexdump -v -s  $((552+28*i))  -n 15 -e '"%_u"'  $drive| sed -e  s/nul[^$]*//);
        System=$(HexToSystem $Type);
        printf "$format"  "$Label" "-" "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)" "$Type" "$System"  "$BINGIndex" "$BINGUnknown">>$MPT_file;
           NamesArray[$PI]=$Label
           StartArray[$PI]=$Start;
           TypeArray[$PI]=$Type;
           SizeArray[$PI]=$Size;
           SystemArray[$PI]=$System;
           EndArray[$PI]=$End;
           DriveArray[$PI]=$HI;
  
           
            if [[ $Type = "f" || $Type = "5" ]];
        then
                 KindArray[$PI]="E";
                 ParentArray[$PI]=$PI;
         ReadPT $HI  $Start  2  $MPT_file "$format"  $PI  4 ;  
            else
                KindArray[$PI]="P";
                ParentArray[$PI]="";
        fi;
         ((i++));
           done;
}

#################   Check partition table for errors  ################################
###  
###  This function checks whether any two partitions  overlap.
###  and the logical partitions are inside the extended parition.
###  Variable 1:        PI of First partition to consider
###  Variable 2:        PI of Last Partition to consider
###  Variable 3:        File for the error messages.
###  Variable 4:        HI of containing hard drive
 CheckPT () {
    local  first=$1 last=$2 file=$3;  hi=$4;
    local  Si Ei Sj Ej Ki  Kj i j k cyl track head cyl_bound sec_bound
    cyl=${HDCylinder[$hi]};
    track=${HDTrack[$hi]};
    head=${HDHead[$hi]};
    cyl_bound=$((cyl*track*head));
    sec_bound=${HDSize[$hi]};
    for (( i=$first; i <= last; i++ ));
    do
         Si=${StartArray[$i]};
         Ei=${EndArray[$i]};
         Ki=${KindArray[$i]};
         Ni=${NamesArray[$i]};
         if [[ "$Ei" -gt "$sec_bound"  ]];
     then
         echo $Ni  ends after the last sector of ${HDName[$hi]}>>$file;
         elif  [[ "$Ei" -gt "$cyl_bound"  ]]
     then
         echo $Ni ends after the last cylinder of ${HDName[$hi]}>>$Trash;
         fi;
         if [[ $Ki = "L" ]];
     then
         k=${ParentArray[$i]};
            Sk=${StartArray[$k]};
            Ek=${EndArray[$k]};
            Nk=${NamesArray[$k]};
            [[ $Si -le $Sk || $Ei -gt $Ek ]] &&  echo  the logical partition  $Ni is not contained in the extended partition  $Nk>>$file;
         fi;
         for (( j = i+1; j <= last; j++ ));
     do 
            Sj=${StartArray[$j]};
            Ej=${EndArray[$j]};
            Kj=${KindArray[$j]};
            Nj=${NamesArray[$j]};
            [[ !( ( $Ki = "L" && $Kj = "E"  )  || ( $Ki = "E" && $Kj = "L"  ) ) && ( ( $Si -lt $Sj &&   $Sj  -lt $Ei )  || ($Sj  -lt $Si && $Si -lt $Ej ) )]] && echo   $Ni overlaps with   $Nj >>$file;
          done;
    done
}

#############################################################################################
##########  Determine the embeded location of stage 2  in a stage 1 file,
##########  look  for the stage 2 and, if found, determine the
#########$  the location and the path of the embedded menu.lst

stage2_loc (){
  local stage1=$1 hi;
  offset=$(hexdump -v -s 68 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s 64 -n 1 -e '"%d"' $stage1);
  pa="T"
  Grub_Version="";
  for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
     tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [[ "$tmp" = 3be5652 || "$tmp" =  bf5e5652  ]];  ###  If stage2 files was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 10  -n 1 -e '"%d"' $Tmp_Log);
              stage2_hdd=$hdd;
              Grub_String=$(hexdump -v -s 18 -n 94 -e '"%_u"' $Tmp_Log);
              Grub_Version=$(echo $Grub_String|sed -e  s/nul[^$]*//);
              BL=$BL$Grub_Version;
              menu=$(echo $Grub_String |sed -e  s/[^\/]*// -e s/nul[^$]*//);
              menu=${menu%% *};
         fi;
     fi;
 done;
 dr=$((dr-127))
 Stage2_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Stage2_Msg=$(echo $Stage2_Msg of the same hard drive) 
 else
      Stage2_Msg=$(echo $Stage2_Msg on boot drive \#$dr)
 fi;
 Stage2_Msg=$(echo $Stage2_Msg for the stage2 file);
                    
 if [ "$pa" = "T"  ]   #### no stage 2 file found.
 then
      Stage2_Msg=$(echo $Stage2_Msg, but no stage2 files can be found at this location.); 
 else
     pa=$((pa+1))
     Stage2_Msg=$(echo $Stage2_Msg.  A stage2 file is at  this location on $stage2_hdd.  Stage2 looks on )                       
     if [ "$pa" = 256 ];
     then
         Stage2_Msg=$(echo $Stage2_Msg the same partition) 
     else
         Stage2_Msg=$(echo $Stage2_Msg  partition \#$pa )
     fi;
     Stage2_Msg=$(echo $Stage2_Msg for  $menu.)
  fi;
}
#######################################################################################

#############################################################################################
##########  Determine the embeded location of core.img  for a Grub2 stage1 file,
##########  look  for the core.img and,  the path of the Grub Folder.
#############################################################################

core_loc (){
  local stage1=$1  grub2_version=$2  hi offset_loc dr_loc dir_loc;
  case $grub2_version in
  1.96) offset_loc=68;  dr_loc=76; dir_loc=32;;
  1.97) offset_loc=92;  dr_loc=91; dir_loc=28;;
  esac;
  offset=$(hexdump -v -s $offset_loc -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -v -s $dr_loc -n 1 -e '"%d"' $stage1);
  pa="T"
    for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
     tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
         if [ "$tmp" = 1bbe5652 ];  ###  If conf.img  file was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump -v  -s 20  -n 1 -e '"%d"' $Tmp_Log);
              core_hdd=$hdd;
          Grub_String=$(hexdump -v -s $dir_loc -n 64 -e '"%_u"' $Tmp_Log);
              Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
         fi;
     fi;
 done;
 Core_Msg=$(echo  looks at sector $offset of the same hard drive for core.img) 

 if [ "$pa" = "T"  ]   #### core.img  found.
 then
     Core_Msg=$(echo $Core_Msg, but core.img can not be found at this location.); 
 else
     pa=$((pa+1))
     Core_Msg=$(echo $Core_Msg,  core.img is  at this location on $core_hdd and looks  )                       
     if [ "$pa" = 255 ];
     then
         Core_Msg=$(echo $Core_Msg for $Core_Dir.) 
     else
         Core_Msg=$(echo $Core_Msg on  partition \#$pa  for  $Core_Dir.)
     fi;
  
  fi;
}
#######################################################################################


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
        name_file="$1$2:"; name_file_length=${#name_file}
        equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
        for length in $(seq $equal_signs_line_length); do
              equal_signs_line='='$equal_signs_line
        done;
                echo >> $Log1;
        echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1;
                echo >> $Log1;
                }



echo '============================= Boot Info Summary: =============================='; echo

#####   Search  for  hard drives which don't exists   or have a  corrupt partition table
#####   All hard drives which a valid partition table are stored   in $Hard_Drives
for drive in  $All_Hard_Drives;
do
        size=$(fdisk -s $drive 2>>$Trash);        
        if [ 0 -lt $size 2>>$Trash ];
    then
            size=$((2*size));
            Hard_Drives=$Hard_Drives" "$drive;
            HDName[$HI]=$drive;
            HDSize[$HI]=$size;
            geometry=$(fdisk  -lu $drive 2>>$Trash | grep "head");
            HDHead[$HI]=$(echo $geometry | awk '{print $1}');
            HDTrack[$HI]=$(echo $geometry | awk '{print $3}');
            HDCylinder[$HI]=$(echo $geometry | awk '{print $5}');
 ###Look at the first 4 bytes of the second sector to identify type of partition table;
            case $(hexdump -v -s 512 -n 4 -e '"%_u"' $drive) in
            "EMBR")  HDPT[$HI]="BootIt";;
            "EFI ")  HDPT[$HI]="EFI";;
                 *)  HDPT[$HI]="MSDos";;
            esac; 
            HI=$((HI+1));
            
        else
            echo -n "$(basename $drive) " >>$FakeHardDrives;
    fi;
done;
############ Identify the MBR of each  hard drive.
echo "Identifying MBRs..." >&6;
for hi in ${!HDName[@]};
  do 
    drive="${HDName[$hi]}";
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in   ####Look at the first two bytes of the hard drive  to identify the boot code installed in the MBR
 
################################ If Grub is in the MBR   #########################

    eb48) offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub is installed without stage1.5 files 
          then
                  stage2_loc $drive;
                  Message=$(echo $Message and  $Stage2_Msg)
           else                         ### if grub is installed with stage1.5 files
                  Grub_String=$(hexdump -v -s 1042 -n 94 -e '"%_u"' $drive);
                  Grub_Version=${Grub_String%%nul*};
                  tmp='/'${Grub_String#*/};
                  tmp=${tmp%%nul*};
                  stage=$(echo $tmp| awk '{print $1}');
                  menu=$(echo $tmp| awk '{print $2}');
                  [[ "$menu" = "" ]] || stage=$(echo $stage and $menu);
                  part_info=$((1045 + ${#Grub_Version}));
              pa=$(hexdump -v -s $part_info  -n 1 -e '"%d"' $drive);
                  part_info=$((part_info+1));
                  dr=$(hexdump -v -s $part_info -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
          pa=$((pa+1));
          if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $stage.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $stage.)
              fi;
        fi;
              BL="Grub "$Grub_Version;;
###############################  If Grub 1.96 is in the MBR   #####################################

        eb4c ) BL="Grub 1.96";
              offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
              if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without  Core. 
          then
                  core_loc $drive 1.96;
                  Message=$(echo $Message and  $Core_Msg)
           else                      ### if Grub2  is installed with Core
                  Grub_String=$(hexdump -v -s 1056 -n 64 -e '"%_u"' $drive);
                  Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
              pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' $drive);
                  dr=$(hexdump -v -s 77  -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
          pa=$((pa+1));
          if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $Core_Dir.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $Core_Dir.)
              fi;
        fi;;

################### If  Grub 1.97 in the MBR###################################
        eb63 ) BL="Grub 1.97"
             offset=$(hexdump -v -s 92 -n 4 -e '"%u"' $drive);### 0x5c contains the offset of the core 
             if  [ "$offset" != 1 ];   ###if  Grub2 is  installed without embeded  Core. 
         then
                 core_loc $drive 1.97;
                  Message=$(echo $Message and  $Core_Msg)
          else                      ### if Grub2  is installed with Core
                  Grub_String=$(hexdump -v -s 1052 -n 64 -e '"%_u"' $drive);
                  Core_Dir=$(echo  $Grub_String | sed s/nul[^$]*//);
              pa=$(hexdump -v -s 1044  -n 1 -e '"%d"' $drive);
                  dr=$(hexdump -v -s 77  -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
          pa=$((pa+1));
          if [ $pa = 255 ];
                  then
                      Message=$(echo $Message and looks  for $Core_Dir.)
                  else
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $Core_Dir.)
                  
                  fi;
        fi;;
##############################################################################################
     ebe) BL=ThinkPad;;
    31c0) BL="Acer 3";;
    33c0) BL=Windows;;
    33ff) BL='HP/Gateway';;
    b800) BL=PloP;;
    ea1e) BL="Truecrypt Boot Loader";; 
    eb04) BL=Solaris;;
    eb5e) case $(hexdump -v -n  3 -e '/1 "%x"' $drive) in   ####Look at the first three bytes of the hard drive to identify the boot code installed in the MBR
        eb5e00) BL=fbinst;;
        eb5e80) BL=Grub4Dos;;
          esac;;
    fa31) case $(hexdump -v -n  3 -e '/1 "%x"' $drive) in   ####Look at the first tree bytes of the hard drive to identify the boot code installed in the MBR
        fa31c0) BL=Syslinux;;
        fa31c9) BL="Master Boot LoaDeR";;   
          esac;;

    fa33) BL="No boot loader";; 
    fab8) BL="No boot loader";;   
    fabe) BL="No boot loader?";;
    faeb) BL=Lilo;; 
    fc31) BL=Testdisk;;
    fc33) BL=GAG;;
    fceb) BL="BootIT NG";;
              #PT_Kind="BootIT";
              #PT_Location=$hi;;
          00) BL="No boot loader";;
       *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -v -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
        HDMBR[$hi]=$BL;
    done
    echo;
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive..." >&6;
    FirstPartition[$HI]=$((PI+1));
    FP=$PI;
    PTType=${HDPT[$HI]};
    HDPT[$HI]="MSDos";
    echo "Drive: $(basename $drive ) ___________________ _____________________________________________________" >>$PartitionTable;
    fdisk  -lu $drive 2>>$Trash |sed '/omitting/ d'|sed '6,$ d' >>$PartitionTable;
    echo >>$PartitionTable;
    printf "$PTFormat" "Partition" "Boot" "Start" "End"  "Size"  "Id" "System">>$PartitionTable;
    echo >>$PartitionTable;
    ReadPT $HI 0  4 $PartitionTable "$PTFormat" "" 0;
    echo >>$PartitionTable;
    LastPartition[$HI]=$PI;
    LP=$PI;
    CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI;
    echo >>$PartitionTable;
    HDPT[$HI]=$PTType;
    case $PTType in
      BootIt) FirstPartition[$HI]=$((PI+1));
               echo -n  BootIT NG Partition Table detected>>$PartitionTable;
              [[ "${HDMBR[$HI]}" = "BootIT NG" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable;
              echo>>$PartitionTable;
              ReadEMBR  $HI $PartitionTable;
          echo >>$PartitionTable;
              if [ "${HDMBR[$HI]}" = "BootIT NG" ];
          then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI; 
          else
                   FirstPartition[$HI]=$FP;
              fi;;
         EFI) FirstPartition[$HI]=$((PI+1));
              EFIee=$(hexdump -v -s 450 -n 1 -e '"%x"' $drive);
              echo -n  GUID Partition Table detected>>$PartitionTable;
              [[ "$EFIee" = "ee" ]] && echo . >>$PartitionTable || echo ,but does not seem to be used. >>$PartitionTable ;
              echo >>$PartitionTable;
              ReadEFI  $HI $PartitionTable;
              echo >>$PartitionTable;
              if [ "$EFIee" = "ee" ];
          then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI;
          else
                   FirstPartition[$HI]=$FP;
              fi;;
      esac;    
done;

for hi in ${!HDName[@]};  ############Loop through all Hard Drives
 do
 drive=${HDName[$hi]}
for (( pi = FirstPartition[$hi]; pi <= LastPartition[$hi]; pi++ ));  ## And then loop through                                                                      ###the partitions  on that drive
do
      BSI="";
      BFI="";    
      part_type=${TypeArray[$pi]};  #### Type of the partition according to fdisk
      start=${StartArray[$pi]};
      size=${SizeArray[$pi]};
      end=${EndArray[$pi]};
      kind=${KindArray[$pi]};
      if [[ "${HDPT[$hi]}" = "BootIt" ]];
      then
          name="${NamesArray[$pi]}";
          mountname=$(basename $drive)$pi;
          part=$(losetup -f --show  -o $((start*512)) $drive);
         #### --sizelimit $((size*512))    --sizelimit seems to be a recently added option for losetup.  Failed on Hardy 
      else
          part=${NamesArray[$pi]};
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda8)
          mountname=$name;      
      fi;
       echo "Searching $name for information... " >&6;
       type=$(blkid -c /dev/null -s TYPE $part 2>$Tmp_Log);  ##### type of file system according to blkid
       type=${type#*=\"};
       type=${type%\"*};
       FileArray[$pi]=$type;
       # part_number=${part:8} 

      echo $name: _________________________________________________________________________; echo
      mkdir "$mountname"    ####  Directory where the partition will be mounted.
      if [[ "${KindArray[$pi]}" = "E"  &&  "$type" = "" ]] ;  #### Check for extended partion.
         then
     type="Extended Partition";
     cat $Tmp_Log>>$Trash;  ### Don't display  the error message from blkid for extended partition
     else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;  ### Display the File System Type

     
          Bytes8081=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)   #### Use bytes 0x80,81 to idendtify Boot sectors
          case    $Bytes8081    in
   fa33|8ec0|8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
        55aa) BST="Windows Vista";;
            e9d8) BST="Windows Vista";;
            55cd) BST="Fat32";;
             10f) BST="HP Recovery";;
            3a5e) BST="Recovery:Fat 32";;
            89e)  BST="MSDOS5.0: Fat 16";;
            bd0)  BST="MSWIN4.1: Fat 32";;
            6f6e) BST="-";;  #MSWIN4.1: Fat 32"
            7cc6) BST="MSWIN4.1: Fat 32";;
            745)  BST="Vista:  Fat 32";;
            19d)  BST="BSD4.4: Fat32";;
 b60 | 211 | e00) BST="Dell Utility: Fat16";; 
            8ed0) BST="DEll Recovery: Fat32";;
            4445) BST="DEll Restore: Fat32";; 
            6974) BST="BootIt: Fat16";;
            6f65) BST="BootIt: Fat16";;
            7cc6) BST=Win_98;;
            734)  BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
        7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
     ####### if Grub, Grub 2 or Lilo  is  in the boot sector,  ########
     ####### investigate the embedded information              ########
            48b4) BST="Grub 1.96";    
                  core_loc $part 1.96;
                  BSI=$(echo $BSI Grub 1.96 is installed in the boot sector of $name  and $Core_Msg);;
            7c3c) BST="Grub 1.97";    
                  core_loc $part 1.97;
                  BSI=$(echo $BSI Grub 1.97 is installed in the boot sector of $name  and $Core_Msg);;
     aa75 | 5272) BST=Grub;
                  stage2_loc $part;
                  BSI=$(echo $BSI Grub $Grub_Version is installed in the boot sector of $name  and $Stage2_Msg);;


     #############  If Lilo look for map file  ##############################################

          8053) BST=LILO;
                   offset=$(hexdump -v -s 32 -n 4 -e '"%u"' $part);  ### 0x20-23 contains the offset
                                                                    #####  of  /boot/map         
                   BSI=$(echo $BSI" "LILO  is installed in boot sector of $part and looks at sector $offset of $drive for the \"map\"  file,); 
                   if [ $offset -lt  $size ];   ### check whether offset
                                                                    #### is on the had drive.
                   then
                     tmp=$(dd if=$drive skip=$offset count=1 2>>$Trash | hexdump -v -s 508  -n 4 -e '"%_p"');                     
                         if [[ "$tmp" = "LILO" ]];
             then
                 BSI=$(echo $BSI" "and the \"map\" file was found at this location.);
                     else
                             BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                         fi;
                    else
                        BSI=$(echo $BSI" "but the \"map\" file was not found at this location.);
                    fi;;
     #########################################################################################

              00)   sig2=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];    #### If the first two bytes are zero, the boot sector does not contain any boot loader.
              then
                      BST="-";
              else           ###### Otherwise, display the boot sector, so we that we might identify it and add it to the list of known boot sectors.
              BST="Unknown"
                      echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump  -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $name" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;
######################   Display the boot sector type.
           echo "    Boot sector type:  "$BST  

####################### Investigate the Boot Parameter Block of an NTFS partition.

           if [[ "$type" = "ntfs" ]]
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%u"' $part);
           BPB_Part_Size=$(hexdump -v -s 40 -n 4 -e '"%u"' $part)
           Comp_Size=$(( (BPB_Part_Size - size)/256 ))
           SectorsPerCluster=$(hexdump -v -s 13 -n 1 -e '"%d"' $part);
           MFT_Cluster=$(hexdump -v -s 48 -n 4 -e '"%d"' $part);
           MFT_Sector=$(( MFT_Cluster * SectorsPerCluster ));
         #  Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
         #  Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
         #  if [[ "$Heads" != 255  || "$Track" != 63 ]]
     #  then
         #     BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)
     #  fi;           
           if [[ "$MFT_Sector" -lt "$size" ]];
           then
               MFT_FILE=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
             # MFT_MFT=$( dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -v -e '4/1 "%x"' | grep "432404d046054")
               
       else 
               MFT_FILE="";
              # MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -v -s 56 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
  
         #  MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash |hexdump -v -e '4/1 "%x"' | grep "432404d046054")
           else 
               MFT_Mirr_FILE="";
            #   MFT_Mirr_MFT="";
           fi;
           if [[ "$offset" = "$start"  && "$MFT_FILE" = "FILE"  && "$MFT_Mirr_FILE" = "FILE"  && "$Comp_Size" = "0"  ]];
        then
           BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
           else
        if [[ "$offset" != "$start" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" && "$offset" != "2048"  && "offset" != "0" ||  "$kind" != "L" ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                 fi;
            fi;
            if  [[ "$MFT_FILE" != "FILE"  ]]; 
        then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $name >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE" ]];
         then
         BSI=$(echo $BSI" "The info in the boot sector on  the starting sector of the MFT Mirror  is wrong.);
             fi;

             if  [[ "$Comp_Size" != "0"  ]];
             then  
                   BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $size sectors.);
             fi;
           fi;
          fi;

######################## Investigate the Boot Parameter Block (BPB)of some Fat partitions
 #####  Identifies Fat Bootsectors which are used for booting.

##  if [[ "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"  || "$Bytes8081" =  "7405" || "$Bytes8081" = "6974" || "$Bytes8081" = "bd0" ||  "$Bytes8081" =  "89e"  ]] ;

        if [[ "$type" = "vfat" ]];
           then
           offset=$(hexdump -v -s 28 -n 4 -e '"%d\n"' $part); #### Starting sector the partition  according to BPP
           BPB_Part_Size=$(hexdump -v -s 32 -n 4 -e '"%d"' $part); ### Partition Size in sectors accoring to BPB 
           Comp_Size=$(( (BPB_Part_Size - size)/256 )) ### This number will be unequal to zero  if the two partions size  differ by more than 255 sectors.  
           #Track=$(hexdump -v -s 24 -n 2 -e '"%u"' $part)''  ### Number of sectors per track.
           #Heads=$(hexdump -v -s 26 -n 2 -e '"%u"' $part)''  ### Number of heads
           #if [[ "$Heads" != 255  || "$Track" != 63 ]] ###  Checks for an usual geometry. 
       #then
           #   BSI=$(echo $BSI" "Geometry: $Heads Heads and $Track sectors per Track.)  ### Report unusal geometry
       #fi;     
           if [[ "$offset" = "$start" && "$Comp_Size" = "0"  ]];  ### Check whether Partitons starting sector  and  the Partition Size of BPB and fdisk agree. 
        then
           BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);  ##If they agreee
        else      ######   if they  don't agree
            if [[ "$offset" != "$start" ]]   ###  if partition starting sector disagree 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)   ### display the starting sector accoding to BPB
                if [[ "$offset" != "63" && "$offset" != "2048" ||  "$kind" != "L" ]]  ### check whether partition is logcial partition and starting sector is a 63.
                then  ### if not, display starting sector according to fdisk.
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $start.);
                fi; ### If not, don't display.  (This is quite common occurence, and only matters if one tries to boot Windows from a logical partition. So I decided not to display a warning message in this case. 
            fi;  
#### If Partition sizes from BPB and FDISK differ by more than 255 sector, display both sizes.       
            if [[ "$Comp_Size" != "0"  ]];
            then    
        BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors.)
                if [[ "$BPB_Part_Size" != 0 ]];
                then 
                BSI=$(echo "$BSI"." " But according to the info  from the partition table , it has  $size sectors.);
                fi;  ## Don't display warning message in the common case BPB_Part_Size=0. 
            fi; 
              
            fi;   #### End of BPB Error if then else 
          fi;   ###### End of Investigation of the BPB of vfat partitions. 
################################################################################################
      #####  Display boot sector info
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'

      ####Exclude Partitions which contain no information,     #########
      ##### or which we (currently) don't know how to  accces. #########  
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] ; 
      then     
 
         CheckMount=$(mount| grep "$part " |sed '2,$ d');
         CheckMount=${CheckMount% type*};
         CheckMount=${CheckMount#* on };   
          ### Check wether partition is already mounted
         [[ "$CheckMount" != "" ]]  &&  mountname=$CheckMount;  #### if yes,use existing mount point.
         if  [ "$CheckMount" != "" ] || mount -t "$type" $part "$mountname" 2>$Mount_Error  || ( [ "$type" = ntfs ] && ntfs-3g  $part "$mountname" 2>>$Mount_Error  ) ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""

        grep -q "W.i.n.d.o.w.s. .V.i.s.t.a"  $mountname/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>$Trash && OS="Windows Vista";

       grep -q "W.i.n.d.o.w.s. .7" $mountname/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>$Trash && OS="Windows 7";

       [ -e "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -e "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -e "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP";

       [ -e "$mountname/etc/issue" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue);

        [ -e "$mountname/etc/slackware-version" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/slackware-version);

        
  
    

##OS=$(cat /etc/lsb-release | grep "DISTRIB_DESCRIPTION"|awk -F = '{print $2}')
     
 ####################################  search for  the files in $Bootfiles   ########################
###################################### and if found, display there contained ########################
       BootFiles=""    
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then
                 titlebar_gen "$name" $file;    ##generates a titlebar above each file/dir listed
                 cat "$mountname"$file >> $Log1;  ### if not a symlink, display content.
              fi;
       fi;
       done;
################# Search for Wubi   and if found display fstab  ###################################

if [ -f "$mountname""/ubuntu/disks/root.disk" ];
      then          
          if mount -o loop  "$mountname""/ubuntu/disks/root.disk"  $Wubi;
      then
              titlebar_gen "$name"  Wubi;
              echo -n "Operating System: " >>$Log1;
              [ -e "$Wubi/etc/lsb-release" ] && cat $Wubi/etc/lsb-release | grep "DISTRIB_DESCRIPTION"|awk -F = '{print $2}' >>$Log1
          if [ -f "$Wubi/etc/fstab" ];
          then
                  echo >>$Log1;
          cat "$Wubi/etc/fstab" >> $Log1;
              else
                 echo "/etc/fstab was not found" >> $Log1;
              fi;
           umount "$Wubi" || umount -l "$Wubi"; 
       else
             titlebar_gen "$name" " Wubi";
             echo /ubuntu/disk/root.disk was found, but could not be mounted >> $Log1;
           fi;
         
       fi;            
             
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found disply where names.           ###############

       for file in $Boot_Prog;   
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
       fi;
       done;


################### Search for the directories related to Booting ########################
##################, if found display the list of files             #######################

#       for file in $Boot_Dir;  #directories in that directory.
#       do
#          if [ -d "$mountname"$file ];
#          then
#          BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file    ##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> $Log1 ; 
#             
#      fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might conatin boot_code files
       do
       if [ -d "$mountname"$file ];   ##### if such directory exits
       then  
           for loader in $( ls  "$mountname"$file );  ##### look at the content of that directory 
           do
                  if [ -f "$mountname$file$loader" ];  ####  it its a file
          then             
                      sig=$(hexdump -v -s 257 -n 8  -e '8/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "BootPart" ]    ##### Bootpart code has "BootPart" written at0x101
              then
                          offset=$(hexdump -v -s 241 -n 4 -e '"%d"' "$mountname"$file$loader);
                              dr=$(hexdump -v -s 111 -n 1 -e '"%d"' "$mountname"$file$loader);
                  dr=$((dr -127))
               BFI=$(echo $BFI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
              fi;
              sig=$(hexdump -v -s 383 -n 4  -e '4/1 "%_p"' "$mountname"$file$loader);
                      if [ "$sig"  = "GRUB" ];   ##### Grub and Grub1.96  have "Grub" written at 0x17f
                      then
                          sig2=$(hexdump -v -n  2 -e '/1 "%x"' "$mountname"$file$loader);
                          if [[ "$sig2" = "eb48" ]] ### distinguish Grub and Grub 2 by the
                                                    ##### first two bytes.
                          then
                               stage2_loc  "$mountname"$file$loader;
                               BFI=$(echo $BFI" "Grub $Grub_Version in the file  $file$loader $Stage2_Msg);
                          else 
                               core_loc  "$mountname"$file$loader 1.96;
                               BFI=$(echo $BFI" "Grub 1.96  in the file  $file$loader $Core_Msg); 
                          fi;    
                      fi;
                      sig=$(hexdump -v -s 392 -n 4  -e '4/1 "%_p"' "$mountname"$file$loader);#### Grub1.97 has "Grub" writtem at 0x188
                      if [ "$sig"  = "GRUB" ];   ##### Grub 1.97  have "Grub" written at 0x188
                      then  
                          core_loc  "$mountname"$file$loader 1.97;
                          BFI=$(echo $BFI" "Grub 1.97  in the file  $file$loader $Core_Msg); 
                      fi;
                      
           fi;
            done; ## End of loop through the files in a particular  Boot_Code_Directory
            fi;
        done   ## End of the loop through the Boot_Code_Directories.

######### Determine the end point of all files in the GrubError18_Files list
    
     echo >$Tmp_Log;
     counter=0;
     cd "$mountname";
     for file in $(ls $GrubError18_Files 2>>$Trash);
     do
     if [[ -f $file ]]
     then 
     BlockSize=$(filefrag -v $file| grep "Blocksize" |awk '{print $6}');
     LastBlock=$(filefrag -v $file| grep "Last block"  |awk '{print $3}');
     EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
     printf "%6sGB: %-s\n" $EndGB "$file" >>$Tmp_Log;
         ((counter++)); 
     fi;
     done;
     cd $Folder;
     if [ $counter != 0 ];
     then
      titlebar_gen "$name"  ": Location of files loaded by Grub";
          cat $Tmp_Log>>$Log1;
     fi;
     echo >$Tmp_Log;

      if [[ $BFI != "" ]];
      then
          echo -n "    Boot file info:     "
          echo $BFI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      fi;
      echo "    Operating System:  "$OS | fold -s -w 55 | sed -e '2~1s/.*/                       &/'     
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
        if [ "$CheckMount" = "" ];  ## if partition was mounted by the script
        then
            umount "$mountname" || umount -l "$mountname";          
        fi;
     else     ############### if partition failed to mount  
       echo "    Mounting failed:";  
     cat $Mount_Error; 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo;
     [[ "${HDPT[$hi]}" = "BootIt" ]] && losetup -d $part;
     done;  ### end of partition loop
     done;  ### end of hard drive loop



echo '=========================== Drive/Partition Info: ============================='; echo
 
[ -e $PartitionTable ] && cat $PartitionTable || echo no valid partition table found ;

echo "blkid -c /dev/null: ____________________________________________________________";
echo; blkid -c /dev/null
echo;
echo '=============================== "mount" output: ===============================';
echo;
mount;
echo;

#################   Write the content of Log1 to the RESULTS file
[ -e $Log1 ] && cat $Log1; 

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs/Boot Sectors/etc =======================";
 echo;
 cat $Unknown_MBR;
 echo;
fi;

if [ -e $FakeHardDrives ];
then 
 echo "=======Devices which don't seem to have a corresponding hard drive==============";
 echo;
 cat $FakeHardDrives;
 echo;
fi;
  

#####################  Write the Error Log to the RESULT file
if [ -s $Error_Log ];
then
    echo "=============================== StdErr Messages: ===============================";
    echo;
    cat $Error_Log;
fi;

#####   Make the  user the owner of Result file
chown $(basename ~) "$LogFile";   

#######  Reset the Standard Output to the Terminal 
exec 1>&-;
exec 1>&6;
exec 6>&-;

echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit

ot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

---

### Post by LarCrow on 2009-12-10
Apparently I violated some forum rules so I had to leave out the Reports.txt which now follows:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders, total 26564832 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000681ef

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,334,504    25,334,442  83 Linux
/dev/sda2          25,334,505    26,555,444     1,220,940   5 Extended
/dev/sda5          25,334,568    26,555,444     1,220,877  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e" TYPE="ext4" 
/dev/sda5: UUID="a1358735-46ac-4c39-9291-06b85a8e09ed" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e3c85e5f-c2ab-46d5-befb-b12c47ca6e6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a1358735-46ac-4c39-9291-06b85a8e09ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

---

### Post by darkod on 2009-12-10
I can't notice any particular problem. Maybe presence can.

Just to make sure, it doesn't harm reinstalling grub2. While booted with the cd in terminal do:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Take the cd out, reboot and check if grub2 from the hdd is working.

---

### Post by LarCrow on 2009-12-10
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
ubuntu@ubuntu:~$ 

This seemed to run OK so now I'll boot from the HDD

---

### Post by LarCrow on 2009-12-10
Same problem when trying to boot from HDD, Boot Loading and then blank screen

---

### Post by presence1960 on 2009-12-10
> **LarCrow said:**
> Same problem when trying to boot from HDD, Boot Loading and then blank screen

the info in the script output looks good to me. BTW what are your machine's specs: CPU, RAM video card?

---

### Post by LarCrow on 2009-12-12
This is an old 386 with 384 MB RAM an a 450 Mhz processor.  I don't know what the video board is.

Since my last post and the fact that we didn't seem to have solved the problem I decided to try version 8.04.  I downloaded and installed it and it came up right away with no problems.    Other than having to wait for 136 updates to finish it went well and seems to work OK.  It doesn't have some of the polish and improvements of 9.10 but it works.

Maybe at some point the solution to my 9.10 problem will surface.  In the meantime I can get familar with the program and it's terminology.

Thanks to all.
Merry Christmas

---

### Post by presence1960 on 2009-12-12
> **LarCrow said:**
> This is an old 386 with 384 MB RAM an a 450 Mhz processor.  I don't know what the video board is.

Since my last post and the fact that we didn't seem to have solved the problem I decided to try version 8.04.  I downloaded and installed it and it came up right away with no problems.    Other than having to wait for 136 updates to finish it went well and seems to work OK.  It doesn't have some of the polish and improvements of 9.10 but it works.

Maybe at some point the solution to my 9.10 problem will surface.  In the meantime I can get familar with the program and it's terminology.

Thanks to all.
Merry Christmas

with those specs the alternate text based installer may be a better option for you. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---


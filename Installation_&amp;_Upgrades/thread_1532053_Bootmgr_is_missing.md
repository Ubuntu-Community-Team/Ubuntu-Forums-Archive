---
title: "Bootmgr is missing"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by ererr10 on 2010-07-15
I installed 10.04, and now i cant get back to windows. I have Ubuntu on one hard drive and windows on the other one. When i try to boot up, unless i go to the boot menu and select the hard drive with Ubuntu on it i get the message boot-mgr is missing, press Ctr - Alt - Del to restart. 

Thanks

---

### Post by lindsay7 on 2010-07-15
Try this first,  boot into Ubuntu and type this in the terminal

sudo update-grub


If that does not fix it the do this,

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9595316](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9595316)

---

### Post by ererr10 on 2010-07-16
nope, still same. Ive seen other threads with the same problem and howthey fix it, but im not sure how to do it if the hard drives are different because i have to edit the grub and i dont want to mess it up

---

### Post by wilee-nilee on 2010-07-16
Download and run the bootscript in my signature, and post the txt in codetags as described.

---

### Post by HenneBaby02 on 2010-07-16
> **ererr10 said:**
> I installed 10.04, and now i cant get back to windows. I have **Ubuntu on one hard drive and windows on the other one**. When i try to boot up, unless i go to the boot menu and select the hard drive with Ubuntu on it i get the message boot-mgr is missing, press Ctr - Alt - Del to restart. 

Thanks Now im not sure how to fix this problem keeping ur Os's where they are but the text i put in bold is more or likely your issue, having them on seperate hard drives... May i suggest Plop Boot Manager, u can do a hard install so it shows up when you boot but i burnt mine to a CD which makes it easy boot anything (floppy usb (if your BIOS doesn't support USB booting like mine) hard drives and cd roms) give it a try if noone else posts a better solution.


hope that helps

---

### Post by Tresmius on 2010-07-17
.

---

### Post by ererr10 on 2010-07-18
brock@Brock-mine:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000865ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3040    24413184   83  Linux
/dev/sda2            3040       30402   219783169    5  Extended
/dev/sda5            3040       15198    97654784   83  Linux
/dev/sda6           15198       16413     9764864   82  Linux swap / Solaris
/dev/sda7           16413       30402   112361472    b  W95 FAT32

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312566784    7  HPFS/NTFS
 
Sorry, i was out of town for a couple days.

---

### Post by oldfred on 2010-07-18
Please see post #4 if you want some help.

---

### Post by ererr10 on 2010-07-19
i cant get it to run, it says command not found

---

### Post by confused57 on 2010-07-19
> **ererr10 said:**
> i cant get it to run, it says command not found
Move the downloaded bootinfo script to your Desktop, then you can just copy & paste the command into a terminal:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by celldweller1591 on 2010-07-19
> Download and run the bootscript in my signature, and post the txt in codetags as described.
This one is helpful! thanks !!

---

### Post by ererr10 on 2010-07-20
Oh, thanks, i should have noticed the /Desktop. anyways, heres the code

```

#!/bin/bash
VERSION=0.55
DATE="February 15th, 2010"
#to use this script:
#
#     sudo bash boot_info_script055.sh
#or
#     su -
#     bash boot_info_script055.sh
#
#
### last-modified 
#
#author  Ulrich Meierfrankenfeld (aka meierfra.) 
# with  contributions from caljohnsmith
# (both members of ubuntuforums.org)
# and Gert Hulselmans
#
#hosted at: http://sourceforge.net/projects/bootinfoscript/
# 
#The birth of the boot info script:
#   http://ubuntuforums.org/showthread.php?t=837791
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
#   Displays  boot configuration files.
#   Is able to search LVM partitions if  the LVM2 package is install
#      ("apt-get install lvm2"  in debian based  distros)
#   Is able to search Linux Software Raid partitions (MD Raids) if
#       the "mdadm" package is installed.
#   If dmraid is installed, searches all raid drives, detected by dmraid.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script. But  when run from /bin, /sbin, /usr/bin,
#    or  other system folder the file "RESULTS.txt" is written to the
#    home directory of the user who runs this script.


###### Display version and date of the script when asked:
# ./boot_info_script -v
# ./boot_info_script -V
# ./boot_info_script --version 
if [ x"$1" = x'-v' ] || [ x"$1" = x'-V' ] || [ x"$1" = x'--version' ] ;
then 
    echo "boot_info_script version $VERSION"
    echo "Dated , $DATE"
    exit 0
fi 


###### Check if all necessary programs are available

Programs="
    awk
    basename
    blkid
    cat
    dd
    dirname
    expr
    fdisk
    filefrag
    fold
    grep
    hexdump
    losetup
    ls
    mkdir
    mount
    pwd
    rm
    sed
    sort
    umount
    wc
    whoami"

Check_Prog=1;

for Program in $Programs ; do

    if ! type $Program > /dev/null 2>&1 ; then
    echo \"$Program\" could not be found. >&2
    Check_Prog=0;
    fi
done

if [ $Check_Prog -eq 0 ];
then
   echo "Please install the  missing program(s) and run boot_info_script again." >&2
   exit 1;
fi;




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
################# Since all the important files in these folder are already displayed
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
Boot_Prog_Normal="
     /bootmgr /BOOTMGR
     /boot/bcd /BOOT/bcd /Boot/bcd  /boot/BCD /BOOT/BCD  /Boot/BCD
     /Windows/System32/winload.exe /WINDOWS/system32/winload.exe /WINDOWS/SYSTEM32/winload.exe /windows/system32/winload.exe
     /Windows/System32/Winload.exe /WINDOWS/system32/Winload.exe /WINDOWS/SYSTEM32/Winload.exe /windows/system32/Winload.exe
     /grldr /GRLDR
     /ntldr /NTLDR
     /NTDETECT.COM    /ntdetect.com
     /NTBOOTDD.SYS    /ntbootdd.sys
     /wubildr.mbr    /ubuntu/winboot/wubildr.mbr
     /wubildr    /ubuntu/winboot/wubildr
     /ubuntu/disks/root.disk
     /ubuntu/disks/home.disk
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
     /IO.SYS /io.sys
     /MSDOS.SYS /msdos.sys 
     /COMMAND.COM /command.com
     "
Boot_Prog_Fat="
      /bootmgr
     /boot/bcd
     /Windows/System32/winload.exe
     /grldr
     /ntldr 
     /NTDETECT.COM 
     /NTBOOTDD.SYS
     /wubildr.mbr 
     /wubildr  
     /ubuntu/winboot/wubildr
     /ubuntu/winboot/wubildr.mbr
     /ubuntu/disks/root.disk
     /ubuntu/disks/home.disk
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU
     /IO.SYS 
     /MSDOS.SYS
     /COMMAND.COM
     "



############### List of files whose contents will be displayed.
Boot_Files_Normal="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  /BOOT.INI
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

Boot_Files_Fat="
    /boot/grub/menu.lst /grub/menu.lst  /NST/menu.lst    /menu.lst
    /grub.cfg    /grub/grub.cfg    /boot/grub/grub.cfg
    /ubuntu/disks/boot/grub/menu.lst /ubuntu/disks/install/boot/grub/menu.lst /ubuntu/winboot/menu.lst
    /boot/grub/grub.conf    /grub/grub.conf    /grub.conf
    /boot.ini  
    /etc/fstab
    /etc/lilo.conf  /lilo.conf
    "

############### List of files whose end point (in GB) will be displayed.
GrubError18_Files="
    boot/grub/menu.lst    grub/menu.lst    menu.lst /NST/menu.lst
    ubuntu/disks/boot/grub/menu.lst
    boot/grub/grub.conf    grub/grub.conf    grub.conf
    grub.cfg    grub/grub.cfg    boot/grub/grub.cfg
    core.img    grub/core.img   boot/grub/core.img
    boot/grub/stage2    grub/stage2    stage2
    boot/vmlinuz*  vmlinuz*    ubuntu/disks/boot/vmlinuz*
    boot/initrd*  initrd*    ubuntu/disks/boot/initrd*
    boot/kernel*.img
    initramfs* boot/initramfs*
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
       if [ "j" = "" ]; then j=0; fi;
       j=$((j+1));
      wait;
    done
LogFile="${LogFile}${j}.txt"  #### The RESULTS file.

######  Redirect stdout to RESULT File
#exec 6>&1   
#exec > "$LogFile"

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
i=0;
while (! mkdir ${Folder}${i} 2>/dev/null)
    do  
      i=$((i+1));
      wait;
    done
Folder=${Folder}${i}

cd $Folder
Log=$Folder/Log                 #File to record the summary.
Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #     these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.
PartitionTable=$Folder/PT       # File to store the Partition   Table
FakeHardDrives=$Folder/FakeHD   # File to list devices which seem to have  no corresponding drive.
BLKID=$Folder/BLKID             # File to store the output of blkid
exec 2>$Error_Log               #Redirect all standard error to the file Error_Log

All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.


if type dmraid >>$Trash 2>>$Trash;
then
  InActiveDMRaid=$(dmraid -si -c);
  if  [ "$InActiveDMRaid" = "no raid disks" ];
  then 
      InActiveDMRaid="";
  fi;
  if  [ "$InActiveDMRaid" != "" ];
  then
      dmraid -ay $InActiveDMRaid >>$Trash;
  fi;
  if [ "$(dmraid -sa -c)" != "no raid disks" ];
  then
       All_DMRaid=$(dmraid -sa -c|awk '{print "/dev/mapper/"$0}');
       All_Hard_Drives=${All_Hard_Drives}" "${All_DMRaid};
  fi;   
fi;

####Arrays to hold information about Partitions: name, starting sector, ending sector, size in sector, Partition Type, Filesystem typ, UUID, Kind(Logical, Primary, Extended), HardDrive, boot flag,  parent (for logical partitions), label, system(the partition id according the partition table), the device associate to the partition.

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray DeviceArray  


#####Arrays to hold information about the harddrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart HDEnd HDUUID;

####Array for Hard drives formated as Filesystem 
declare -a FilesystemDrives;


PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hard drive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,


####  fdisk -s seems to malfunction sometimes. So use sfdisk -s if available
function fdisks (){
if type sfdisk >>$Trash 2>>$Trash
then
   sfdisk -s "$1" 2>>$Trash;
else
   fdisk -s "$1" 2>>$Trash;
fi;
}
   


#####  A function which checks whether a file is on a mounted partition 
MountPoints=$(mount | grep -e ^/dev |awk '{print $3}' |grep -v  ^/$); ##list of mountpoints for devices
 
function FileNotMounted (){
local File=$1 curmp=$2;      
for mp in $MountPoints; 
do 
 if [ $(expr match "$File" "$mp""/" ) -ne 0 ] && [ "$mp" != "$curmp" ]
 then 
   return 1; 
 fi;
done;
return 0;
}

##### A function which converts the  two digit hexcode of a partition type 
# The following list is taken from sfdisk -T  and 
#  http://www.win.tue.nl/~aeb/partitions/partition_types-1.html
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
dd) system="Dell Media Direct";;
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
####  ABCDEFGH-IJKL-MNOP-QRST-UVWXYZabcdef is stored as
####  GHEFCDAB-KLIJ-OPMN-QRST-UVWXYZabcdef (without the dashes)
function UUIDToSystem() {
local type=$1 system
case $type in
    00000000000000000000000000000000)  system="Empty";;
    41ee4d02e733d3119d690008c781f39f)  system="MBR partition scheme";;
    28732ac11ff8d211ba4b00a0c93ec93b)  system="System/Boot Partition";;
    a2a0d0ebe5b9334487c068b6b72699c7)  system="Linux or Data";; 
    6dfd5706aba4c44384e50933c84b4f4f)  system="Linux Swap";;
    16e3c9e35c0bb84d817df92df00215ae)  system="Microsoft Windows";;
    79d3d6e607f5c244a23c238f2a3df928)  system="LVM";;
    005346480000aa11aa1100306543ecac)  system="HFS+";;
    4861682149646f6e744e656564454649)  system="Bios Boot Partition";;
                                   *)  system="-";
                                       echo Unknown GPT Partiton Type>>$Unknown_MBR;
                                       echo  $type >>$Unknown_MBR;;   
esac;
echo $system;
   }

##### Function which insert a comma every  third digit of a number
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

#### Functions to pretty print blkid output ######
BlkidFormat='%-16s %-38s %-10s %-30s\n'
BlkidTag (){
echo $(blkid -c /dev/null -s $2 -o value $1 2>>$Trash)
}

PrintBlkid (){
local part=$1;
if  [  "$(blkid -c /dev/null $part  2>$Tmp_Log)"  != "" ];
then
printf "$BlkidFormat" "$part"  "$(BlkidTag $part UUID)"  "$(BlkidTag  $part TYPE)" "$(BlkidTag $part LABEL)">>$BLKID;
else blkid  -p "$part"  2>&1 |grep "$part" >>$BLKID; #blkid -p is not avaible all all systems. This contructs makes sure the "usage" message is not displayed, but catches the "ambivalent" error.
fi;
}


## Reads and display the  a partition table of an extended partitons    ###########
#############  and check the partition  check for errors         #####################
#  This function can be applied iteratively  to read the extended partiton table           
# Variable 1:  HI of hard drive 
# Variable 2:  Start Sector of the extended Partition,
# Variable 3:  Number of partitions in table (4 for regular PT, 2 for logical
# Variable 4:  File for storing the partitions table.
# Variable 5:  Format to use for displaying the partition table.  
# Variable 6:  PI of the primary extended partition containing the extended partition.
#              ( equals ""  for hard drive)
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
      # sector  of primary extended partition otherwise
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
               if [[  $i = 0 ]];
                   then
                      echo "Extended  partition  linking to another extended partition" >>$PT_file;
                   fi;
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
        [[ "${HDPT[$HI]}"  = "BootIt"  ]] &&  label="${NamesArray[$EPI]}""_" || label=$drive;
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
                ( [[ "$EPI" = "" ]] || [[ ${DeviceArray[$EPI]} != "" ]] ) && DeviceArray[$PI]=$drive$LinuxIndex; 

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
        DeviceArray[$PI]=$Label;
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
    local HI=$1 drive MPT_file=$2 Size N=0 i=0  BINGIndex  Label   Start End  Type BINGUnknown format Size System StoredPI FirstPI=FirstPartition[$1] LastPI=$PI New;
    drive="${HDName[$HI]}";
    format='%-18s %4s%14s%14s%14s %3s %-15s %3s %2s\n';
    printf "$format"  Partition Boot Start End Size Id System  Ind "?">> $MPT_file; 
    N=$(hexdump -v -s 534  -n 1 -e  '"%u"' $drive); 
    while [[ $i -lt "$N" ]]
    do
        New=1;
        BINGUnknown=$(hexdump -v -s  $((541+28*i))  -n 1 -e '"%x"'  $drive)
    Start=$(hexdump -v -s  $((542+28*i))  -n 4 -e '4 "%u"'  $drive);
      End=$(hexdump -v -s  $((546+28*i))  -n 4 -e '4 "%u"'  $drive);
    BINGIndex=$(hexdump -v -s  $((550+28*i))  -n 1 -e '"%u"'  $drive);
    Type=$(hexdump -v -s  $((551+28*i))  -n 1 -e '"%x"'  $drive);
        Size=$((End-Start+1));
    Label=$(hexdump -v -s  $((552+28*i))  -n 15 -e '"%_u"'  $drive| sed -e  s/nul[^$]*//);
        System=$(HexToSystem $Type);
        printf "$format"  "$Label" "-" "$(InsertComma $Start)" "$(InsertComma $End)" "$(InsertComma $Size)" "$Type" "$System"  "$BINGIndex" "$BINGUnknown">>$MPT_file;
         StoredPI=$PI;
         for ((j = FirstPI; j<=LastPI; j++ ));
           do
              if (( ${StartArray[$j]} == $Start ));
          then 
                    PI=$j;
                    New=0; 
                    break;
              fi;
           done;
         
         if (( $New  == 1 ));
         then
           ((PI++));
           StoredPI=$PI;
           StartArray[$PI]=$Start;
           TypeArray[$PI]=$Type;
           SizeArray[$PI]=$Size;
           SystemArray[$PI]=$System;
           EndArray[$PI]=$End;
           DriveArray[$PI]=$HI;
         fi;
         NamesArray[$PI]=$Label;
  
         if [[ $Type = "f" || $Type = "5" ]];
        then
                 KindArray[$PI]="E";
                 ParentArray[$PI]=$PI;
         ReadPT $HI  $Start  2  $MPT_file "$format"  $PI  4 ;  
            else
                KindArray[$PI]="P";
                ParentArray[$PI]="";
        fi;
          PI=$StoredPI;
         ((i++));
           done;
}

#################   Check partition table for errors  ################################
###  
###  This function checks whether any two partitions  overlap
###  and the logical partitions are inside the extended partition.
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
##########  Determine the embeded location of core.img  for a Grub2 boot.img file,
##########  look  for the core.img and,  the path of the Grub Folder.
#############################################################################

core_loc (){
  local stage1=$1  grub2_version=$2  hi offset_loc dr_loc dir_loc;
  case $grub2_version in
  1.96) offset_loc=68;  dr_loc=76; dir_loc=32;;
  1.97) offset_loc=92;  dr_loc=91; dir_loc=28;;
  esac;
  offset=$(hexdump -v -s $offset_loc -n 4 -e '4 "%u"' "$stage1" 2>>$Trash);
  dr=$(hexdump -v -s $dr_loc -n 1 -e '"%d"' "$stage1");
  pa="T"
    for hi in ${!HDName[@]};
  do
     hdd=${HDName[$hi]};
     if [ $offset -lt  ${HDSize[hi]}  ];
     then
     tmp=$(dd if="$hdd" skip=$offset count=1 2>>$Trash | hexdump -v    -n 4 -e '"%x"');
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

 if [ "$pa" = "T"  ]   
 then  #### core.img not  found.
     Core_Msg=$(echo $Core_Msg, but core.img can not be found at this location.); 
 else  #### core.img  found.            
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

###############  Get_Partition_Info search a partition for information relevant for booting.
####Variables:
####  log         $1  local version of RESULT.txt####  log1        $2  local version of log1
####  part        $3  device for the partition
####  name        $4  descriptive name for the partition
####  mountname   $5  path where  partition will be mounted.
###   kind        $6  kind of the partition
###   start       $7  starting sector of the partition
###   end         $8  ending sector of the partition
###   system      $9  system of the partition
###   pi          $10  pi of the partition, (equal to "" if not a regular partition. 
Get_Partition_Info(){
local Log="$1" Log1="$2" part="$3" name="$4" mountname="$5"  kind="$6"  start="$7"  end="$8" system="$9" pi="${10}";
local size=$((end-start)) BST=""  BSI=""  BFI=""  OS="" BootFiles="";


       echo "Searching $name for information... ";
       PrintBlkid $part;
       type=$(BlkidTag $part TYPE);  ##### type of file system according to blkid

       [[ "$system" == "Bios Boot Partition" ]] && type="Bios Boot Partition"
       [[ $pi != "" ]] && FileArray[$pi]=$type;
      echo "$name: _________________________________________________________________________" >>"$Log"; echo>> "$Log"
      mkdir -p "$mountname"    ####  Directory where the partition will be mounted.
      if [[ "$kind" = "E"  &&  "$type" = "" ]] ;  #### Check for extended partion.
         then
     type="Extended Partition";
     cat $Tmp_Log>>$Trash;  ### Don't display  the error message from blkid for extended partition
     else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type>>"$Log";  ### Display the File System Type

     
          Bytes8081=$(hexdump -v -s 128 -n  2 -e '/1 "%x"'  $part)   #### Use bytes 0x80,81 to idendtify Boot sectors
          case    $Bytes8081    in
             10f) BST="HP Recovery";;
             19d)  BST="BSD4.4: Fat32";;
             211) BST="Dell Utility: Fat16";;
             734)  BST=Dos_1.0;;
             745)  BST="Vista:  Fat 32";;
             89e)  BST="MSDOS5.0: Fat 16";;
             8cd) BST="Windows XP";;
             488) BST="Grub 2's core.img";;
             b60) BST="Dell Utility: Fat16";; 
             bd0) BST="MSWIN4.1: Fat 32";;
             e00) BST="Dell Utility: Fat16";;
            2d5e) BST=Dos_1.1;;
            3a5e) BST="Recovery:Fat 32";;
            4445) BST="DEll Restore: Fat32";; 
        55aa) BST="Windows Vista/7";;
            55cd) BST="Fat32";;
            6616) BST=Fat16;;
            696e) BST=Fat16;;
            6974) BST="BootIt: Fat16";;
            6f65) BST="BootIt: Fat16";;
            6f74) BST=Fat32;; 
            6f6e) BST="-";;  #MSWIN4.1: Fat 32"
            7815) BST=Fat32;;
         7cc6) BST="MSWIN4.1: Fat 32";;
          # 7cc6) BST=Win_98;;
            8a56) BST="Acronis SZ: Fat32";;
            8ec0) BST="Windows XP";;
            8ed0) BST="DEll Recovery: Fat32";;
            b6d1) BST="Windows XP: Fat32";;
            e2f7) BST="Fat32, Non Bootable";;
            e9d8) BST="Windows Vista/7";;
            fa33) BST="Windows XP";;
               ####### if Grub, Grub 2 or Lilo  is  in the boot sector,  ########
               ####### investigate the embedded information              ########
            48b4) BST="Grub 1.96";    
                  core_loc $part 1.96;
                  BSI=$(echo $BSI Grub 1.96 is installed in the boot sector of $name  and $Core_Msg);;
            7c3c) BST="Grub 2";    
                  core_loc $part 1.97;
                  BSI=$(echo $BSI Grub 2 is installed in the boot sector of $name  and $Core_Msg);;
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
              else   ###### Otherwise, display the boot sector, so we that we might identify it and add it to the list of known boot sectors.
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
           echo "    Boot sector type:  "$BST>>"$Log" 

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
       else 
               MFT_FILE="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -v -s 56 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$size" ]];
           then
                MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -v    -n 4 -e '"%_u"');
  
           else 
               MFT_Mirr_FILE="";
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
      echo -n "    Boot sector info:  ">>"$Log"
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"

      ####Exclude Partitions which contain no information,     #########
      ##### or which we (currently) don't know how to  accces. #########  
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] && [ "$system" != "Bios Boot Partition" ] ; 
      then     
 
         CheckMount=$(mount| grep "$part " |sed '2,$ d');
         CheckMount=${CheckMount% type*};
         CheckMount=${CheckMount#* on };   
          ### Check whether partition is already mounted
         if  [ "$CheckMount" != "" ] ;
         then 
             if  [ "$CheckMount" = "/" ];
             then mountname="";
             else
                mountname=$CheckMount;  #### if yes,use existing mount point.
             fi;
         fi;
         if  [ "$CheckMount" != "" ] || mount -r  -t "$type" $part "$mountname" 2>>$Mount_Error  || ( [ "$type" = ntfs ] &&  ntfs-3g -o ro  $part "$mountname" 2>>$Mount_Error )   ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""

        grep -q "W.i.n.d.o.w.s. .V.i.s.t.a"  "$mountname"/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows Vista";

       grep -q "W.i.n.d.o.w.s. .7" "$mountname"/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows 7";
       for  WinOS in  "MS-DOS"  "MS-DOS 6.22" "MS-DOS 6.21" "MS-DOS 6.0" "MS-DOS 5.0" "MS-DOS 4.01" "MS-DOS 3.3" "Windows 98" "Windows 95"; do grep -q "$WinOS" "$mountname"/{IO.SYS,io.sys} 2>>$Trash && OS="$WinOS"; done;
        

       [ -s "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -s "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -s "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -s "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP";

       [ -s "$mountname/etc/issue" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue);

        [ -s "$mountname/etc/slackware-version" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/slackware-version);


####################################  search for  the files in $Bootfiles   ########################
#################################### and if found, display there contained ########################
       BootFiles="" 
       if [ "$type" = "vfat" ];
       then
           Boot_Files=$Boot_Files_Fat;
       else
           Boot_Files=$Boot_Files_Normal;  
       fi;
       
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ] && [ -s "$mountname"$file ] && FileNotMounted "$mountname"$file "$mountname"
           then
               BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then                            ### if not a symlink, display content.
                 titlebar_gen "$name" $file; ##generates a titlebar above each file/dir listed      
                 cat "$mountname"$file  >> "$Log1"; 
              fi;
       fi;
       done;
################# Search for Wubi partitions  ###################################
if [ -f "$mountname""/ubuntu/disks/root.disk" ];
      then          
          Wubi=$(losetup -a|awk '$3 ~ "(/host/ubuntu/disks/root.disk)"{print $1; exit}'|sed s/.$//)
                    #check whether Wubi already has a loop device.
          if [[ "$Wubi" = "" ]];
          then
              Wubi=$(losetup -f --show  "$mountname""/ubuntu/disks/root.disk" );
              WubiDev=0;
          else
              WubiDev=1;
          fi;
          if [ "$Wubi" != "" ];
          then
              Get_Partition_Info "$Log"x "$Log1"x "$Wubi" "$name""/Wubi" "Wubi/""$mountname" "Wubi" 0 0 "Wubi" "";
          [[ $WubiDev = 0 ]] && losetup -d "$Wubi";  #delete Wubu loop device, if created by BIS
          else 
             echo "Found Wubi on $name. But could not create a loop device">>$Error_Log;
          fi;      
        fi;            
                    
                      
             
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found displays their names.           ###############
        if [ "$type" = "vfat" ];
       then
           Boot_Prog=$Boot_Prog_Fat;
       else
           Boot_Prog=$Boot_Prog_Normal;  
       fi;

       for file in $Boot_Prog;   
       do
           if [ -f "$mountname"$file ] && [ -s "$mountname"$file ]  && FileNotMounted "$mountname"$file "$mountname";
              then 
              BootFiles=$(echo $BootFiles"  "$file);          
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
#              ls -la  "$mountname"$file >> "$Log1" ; 
#             
#      fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might contain boot_code files
       do
       if [ -d "$mountname"$file ] && FileNotMounted "$mountname"$file "$mountname";   ##### if such directory exist
       then  
           for loader in $( ls  "$mountname"$file );  ##### look at the content of that directory 
           do
                  if [ -f "$mountname$file$loader" ] && [ -s "$mountname$file$loader" ];  ####  it its a file
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
                      if [ "$sig"  = "GRUB" ];   ##### Grub 2  have "Grub" written at 0x188
                      then  
                          core_loc  "$mountname"$file$loader 1.97;
                          BFI=$(echo $BFI" "Grub 2  in the file  $file$loader $Core_Msg); 
                      fi;
                      
           fi;
            done; ## End of loop through the files in a particular  Boot_Code_Directory
            fi;
        done   ## End of the loop through the Boot_Code_Directories.

######### Determine the end point of all files in the GrubError18_Files list
    
     echo >$Tmp_Log;
     counter=0;
     cd "$mountname"/;
     for file in $(ls $GrubError18_Files 2>>$Trash);
     do
     if [[ -f $file ]] && [[ -s $file ]] && FileNotMounted "$mountname""/"$file "$mountname"
     then
         EndGB="??";
         BlockSize=$(filefrag -v $file| grep "Blocksize" |awk '{print $6}');
         if [ "$BlockSize" != "" ];
         then
             LastBlock=$(filefrag -v "$file"| grep "Last block"  |awk '{print $3}');
             if [ "$LastBlock" != "" ];
             then
                   EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
         fi;  
         fi; 
         BlockSize=$(filefrag -v "$file"| grep "blocksize" |awk '{print $NF}'| sed 's/)//');
         if [ "$BlockSize" != "" ];
         then
             LastBlock=$(filefrag -v "$file" | grep 'eof'  |awk '{print $3}');
             if [ "$LastBlock" != "" ];
             then
             EndGB=$(echo $(((BlockSize*LastBlock + 512*start)/100000000 ))|sed 's/\(.\)$/\.\1/')
         fi;  
         fi; 
         printf "%6sGB: %-s\n" $EndGB "$file" >>$Tmp_Log;
         ((counter++));
     fi;
     done;
     cd $Folder;
     if [ $counter != 0 ];
     then
      titlebar_gen "$name"  ": Location of files loaded by Grub";
          cat $Tmp_Log>>"$Log1";
     fi;
     echo >$Tmp_Log;

      if [[ $BFI != "" ]];
      then
          echo -n "    Boot file info:     ">>"$Log"
          echo $BFI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"
      fi;
      echo "    Operating System:  "$OS | fold -s -w 55 | sed -e '2~1s/.*/                       &/'>>"$Log"    
      echo -n "    Boot files/dirs:   ">>"$Log"
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'>>"$Log"
     
        if [ "$CheckMount" = "" ];  ## if partition was mounted by the script
        then
            umount "$mountname" || umount -l "$mountname";          
        fi;
     else     ############### if partition failed to mount  
       echo "    Mounting failed:">>"$Log";  
       cat $Mount_Error>>"$Log"; 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo>>"$Log";
     if [[ -e "$Log"x ]];
     then cat "$Log"x>>"$Log";
          rm "$Log"x;
     fi;
     if [[ -e "$Log1"x ]];
     then cat "$Log1"x>>"$Log1";
          rm "$Log1"x;
     fi;

      }  ## end Get_Partition_Info function



## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
        name_file="$1$2:"; name_file_length=${#name_file}
        equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
        for length in $(seq $equal_signs_line_length); do
              equal_signs_line='='$equal_signs_line
        done;
                echo >> "$Log1";
        echo "$equal_signs_line $name_file $equal_signs_line" >> "$Log1";
                echo >> "$Log1";
                }


echo "                Boot Info Script $VERSION    dated $DATE                    ">>"Log";
echo>>"Log";
echo '============================= Boot Info Summary: =============================='>>"$Log"; 
echo>>"$Log";

#####   Search  for  hard drives which don't exist,have a  corrupted partition table
#####  or  don't have a parition table(whole drive is a file system) 
#####  Information on all  hard drives which a valid partition table are stored in the 
#####  Hard drives arrays: HD?????
FSD=0;  #id for Filesystem Drives
for drive in  $All_Hard_Drives;
do
     size=$(fdisks $drive);
     PrintBlkid $drive;        
     if [ 0 -lt $size 2>>$Trash ];
     then
          if  [ "$(blkid  $drive)" = "" ] || [ "$(blkid  | grep $drive:)" = "" ]; #Check whether drive is a filesystem
          then  #if drive is  not a filesytem
             size=$((2*size));
 # (not used) Hard_Drives=$Hard_Drives" "$drive;
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
          else   #if drive is  filesystem
              if [ $( expr match "$(BlkidTag "$drive" TYPE)" '.*raid') -eq 0 ] || [ "$(BlkidTag "$drive" UUID)" != "" ];
              then
                   FilesystemDrives[$FSD]="$drive";
                   ((FSD++));
              fi;
          fi;
      else
            echo -n "$(basename $drive) " >>$FakeHardDrives;
      fi;
done;
############ Identify the MBR of each  hard drive.
echo "Identifying MBRs..." ;
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

################### If  Grub 2 in the MBR###################################
        eb63 ) BL="Grub 2"
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
    eb31) BL=Paragon;;
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
    fceb) BL="BootIt NG";;
          00) BL="No boot loader";;
       *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -v -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => ">>"$Log"
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/' >>"$Log"  
        HDMBR[$hi]=$BL;
    done;
    echo>>"$Log";
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive...";
    FP=$((PI+1)); #used if non-MS_DOS partition table is not in use.
    FirstPartition[$HI]=$FP;
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
      BootIt)  echo -n  BootIt NG Partition Table detected>>$PartitionTable;
              [[ "${HDMBR[$HI]}" = "BootIt NG" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable;
              echo>>$PartitionTable;
              ReadEMBR  $HI $PartitionTable;
          echo >>$PartitionTable;
              if [ "${HDMBR[$HI]}" = "BootIt NG" ];
          then
                   LastPartition[$HI]=$PI;
                   CheckPT  ${FirstPartition[$HI]} ${LastPartition[$HI]}  $PartitionTable $HI; 
          else
                   FirstPartition[$HI]=$FP;
              fi;;
         EFI) FirstPartition[$HI]=$((PI+1));
              EFIee=$(hexdump -v -s 450 -n 1 -e '"%x"' $drive);
              echo -n  GUID Partition Table detected>>$PartitionTable;
              [[ "$EFIee" = "ee" ]] && echo . >>$PartitionTable || echo , but does not seem to be used. >>$PartitionTable ;
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
         
      part_type=${TypeArray[$pi]};  #### Type of the partition according to fdisk
      start=${StartArray[$pi]};
      size=${SizeArray[$pi]};
      end=${EndArray[$pi]};
      kind=${KindArray[$pi]};
      system=${SystemArray[$pi]};
      if [[ "${DeviceArray[$pi]}" = "" ]];
      then
          name="${NamesArray[$pi]}";
          mountname=$(basename $drive)"_"$pi;
          part=$(losetup -f --show  -o $((start*512)) $drive);
         #### --sizelimit $((size*512))    --sizelimit seems to be a recently added option for losetup.  Failed on Hardy 
      else
          part="${DeviceArray[$pi]}";
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda8)
          mountname=$name;      
      fi;

      Get_Partition_Info "$Log" "$Log1" "$part" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
     
     [[ "${DeviceArray[$pi]}" = ""  ]] && losetup -d $part;
     done;  ### end of partition loop
     done;  ### end of hard drive loop


################ Deactivate dmraid's activated by the script#############

if [ "$InActiveDMRaid" != "" ];
then
   dmraid -an $InActiveDMRaid
fi; 

##################### Search LVM partitions for information.             #########
##################### only works if the "LVM2"-package is installed     #########
if type lvscan >>$Trash 2>>$Trash && type lvdisplay >>$Trash 2>>$Trash && type lvchange >>$Trash 2>>$Trash;

then   ###  if LVM2 is installed
   
   LVM_Partitions=$(lvscan| awk '{print $2}'| awk -F / '{print "/dev/mapper" "/" $3 "-" $4}'|sed s/.$//)

   for LVM in $LVM_Partitions;
   do 
      LVM_Size=$(lvdisplay -c $LVM  |awk -F : '{print $7}');
      LVM_Status=$(lvdisplay $LVM |grep "LV Status"|awk '{print $3}');
      lvchange -ay $LVM;
      name=${LVM:12};
      mountname="LVM/""$name";
      kind="LVM";
      start=0;
      end=$LVM_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$LVM" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
      
  [[ "$LVM_Status" = "NOT" ]] && lvchange -an "$LVM";
                         #deactivate all LVM's,which were not active. 
  
     
    done;
fi;


####################### Search MDRaid Partitons for Information##############################
######################  Only works if "mdadm" is installed     #############################
if type mdadm >>$Trash 2>>$Trash;
then
    MD_Active_Array=$(mdadm --detail --scan |awk '{print $2}');
                   ## all arrays which are already assembled
    mdadm --assemble  --scan  #assemble all arrays
    MD_Array=$(mdadm --detail --scan|awk '{print $2}');
                    ## all arrays.
    for MD in $MD_Array;
    do
        MD_Size=$(fdisks $MD); #size in blocks
        MD_Size=$((2*MD_Size)); #size in sectors
        MD_Active=0;
        for MDA in $MD_Active_Array;  ## check whether MD is active
        do
          if [[ "$MDA" = "$MD" ]]
          then
              MD_Active=1;
              break;
          fi;
    done;
      name=${MD:5};
      mountname="MDRaid/""$name";
      kind="MDRaid";
      start=0;
      end=$MD_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$MD" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
      
  [[ "$MD_Active" = 0 ]] && mdadm --stop $MD

                         #deactivate all MD_Raid's,which were not active.
   done;
fi; 

####################### Search Filessystem hard drive for information########################

    for FD  in ${FilesystemDrives[@]};
    do
      FD_Size=$(fdisks $FD); #size in blocks
      FD_Size=$((2*FD_Size)); #size in sectors
      name=${FD:5};
      mountname="FD/""$name";
      kind="FD";
      start=0;
      end=$FD_Size;
      system="";
      pi="";
     
      Get_Partition_Info "$Log" "$Log1" "$FD" "$name" "$mountname" "$kind" "$start" "$end" "$system" "$pi";
    done;
  

###############################################################################################

echo '=========================== Drive/Partition Info: ============================='>>"$Log";
echo>>"$Log";
 
[ -e $PartitionTable ] && cat $PartitionTable>>"$Log" || echo no valid partition table found>>"$Log";


echo "blkid -c /dev/null: ____________________________________________________________">>"$Log";
echo>>"$Log";
printf "$BlkidFormat" Device  UUID TYPE LABEL>>"$Log";
echo>>"$Log"
for dev in $(blkid -o device);do PrintBlkid $dev;done;
sort -u $BLKID>>"$Log";
echo>>"$Log";

if [ $(ls -R /dev/mapper 2>>$Trash | wc -l) -gt 2 ]
then

  echo '=============================== "ls -R /dev/mapper/" output: ==============================='>>"$Log";
   ls -R /dev/mapper>>$Log
  echo>>"$Log";
fi;
         




echo '============================ "mount | grep ^/dev  output: ==========================='>>"$Log";
MountFormat='%-16s %-24s %-10s %s\n';
Fis=':x:x:x:x:'
echo>>"$Log";
printf "$MountFormat" "Device" "Mount_Point"  "Type"  "Options" >>"$Log";
echo>>"$Log";
mount | grep ' / '| grep -v '^/'| sed  's/ on /'$Fis'/' |sed 's/ type /'$Fis'/'|sed  's/ (/'$Fis'(/'|awk -F $Fis '{printf "'"$MountFormat"'", $1, $2, $3, $4 }'>>"$Log";
mount | grep '^/dev'|sed  's/ on /'$Fis'/' |sed 's/ type /'$Fis'/' |sed  's/ (/'$Fis'(/'|awk -F $Fis '{printf "'"$MountFormat"'", $1, $2, $3, $4 }'>>"$Log";
echo>>"$Log";


#################   Write the content of Log1 to the log file
[ -e "$Log1" ] && cat "$Log1">>"$Log"; 

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs/Boot Sectors/etc =======================">>"$Log";
 echo>>"$Log";
 cat $Unknown_MBR>>"$Log";
 echo>>"$Log";
fi;

if [ -e $FakeHardDrives ];
then 
 echo "=======Devices which don't seem to have a corresponding hard drive==============">>"$Log";
 echo>>"$Log";
 cat $FakeHardDrives>>"$Log";
 echo>>"$Log";
fi;
  

#####################  Write the Error Log to the log file
if [ -s $Error_Log ];
then
    echo "=============================== StdErr Messages: ===============================">>"$Log";
    echo>>"$Log";
    cat $Error_Log>>"$Log";
fi;

#####   Copy the  Log file to RESULTS file and make the  user the owner of Result file
cp "$Log" "$LogFile"
chown $(basename ~) "$LogFile";   

#######  Reset the Standard Output to the Terminal 
#exec 1>&-;
#exec 1>&6;
#exec 6>&-;

echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit

```

---

### Post by oldfred on 2010-07-20
You posted the script. You are supposed to run the script and it will generate a results.txt which is what we want your to post.

Boot Info Script courtesy of forum member meierfra
[COLOR=Red]Page with instructions[/COLOR] and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by ererr10 on 2010-07-21
Ok sorry. WOW im a noob. Anyways i hope this is right.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    48,828,415    48,826,368  83 Linux
/dev/sda2          48,830,462   488,396,799   439,566,338   5 Extended
/dev/sda5          48,830,464   244,140,031   195,309,568  83 Linux
/dev/sda6         244,142,080   263,671,807    19,529,728  82 Linux swap / Solaris
/dev/sda7         263,673,856   488,396,799   224,722,944   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   625,135,615   625,133,568   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        46c3f3b1-e431-40b7-abd8-60d99dfb6745   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cdbda1ca-17e5-4287-88ce-b02964d3abb2   ext4                                     
/dev/sda6        7c9b400b-1337-42cd-bf51-ec5af0a987a3   swap                                     
/dev/sda7        3C0B-8705                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12B8F037B8F01B45                       ntfs       Timmy                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=46c3f3b1-e431-40b7-abd8-60d99dfb6745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=46c3f3b1-e431-40b7-abd8-60d99dfb6745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=46c3f3b1-e431-40b7-abd8-60d99dfb6745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=46c3f3b1-e431-40b7-abd8-60d99dfb6745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 46c3f3b1-e431-40b7-abd8-60d99dfb6745
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=cdbda1ca-17e5-4287-88ce-b02964d3abb2 /home           ext4    defaults        0       2
# /shared was on /dev/sdb7 during installation
UUID=3C0B-8705  /shared         vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb6 during installation
UUID=7c9b400b-1337-42cd-bf51-ec5af0a987a3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  13.8GB: boot/grub/grub.cfg
  17.5GB: boot/initrd.img-2.6.32-21-generic
  17.6GB: boot/initrd.img-2.6.32-23-generic
  17.5GB: boot/vmlinuz-2.6.32-21-generic
   1.3GB: boot/vmlinuz-2.6.32-23-generic
  17.6GB: initrd.img
  17.5GB: initrd.img.old
   1.3GB: vmlinuz
  17.5GB: vmlinuz.old

=================== sda5: Location of files loaded by Grub: ===================


  38.0GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  7c 86 01 53 84 a3 91 1e  13 26 da cc 08 0f 7a 69  ||..S.....&....zi|
00000010  2d 79 29 d6 69 10 b1 54  bc c6 2f f8 fe 31 d6 a3  |-y).i..T../..1..|
00000020  6d b1 20 da 5d 81 a9 81  04 31 07 1f 69 6b 45 9c  |m. .]....1..ikE.|
00000030  f6 d8 b8 57 4b 98 9e 8f  70 3d c5 6c 6d 3e c4 5c  |...WK...p=.lm>.\|
00000040  cd 08 d9 12 31 e9 a2 63  a4 b5 7b f4 3e 7a 5d 56  |....1..c..{.>z]V|
00000050  2d ad b9 41 8c 6a f6 20  6c 4a c4 76 f3 7f 60 6a  |-..A.j. lJ.v..`j|
00000060  55 2f ba c6 3a b0 fc fc  3c 1c 3e b0 08 de 86 0b  |U/..:...<.>.....|
00000070  d8 67 19 16 1a 25 3c 97  3b ed ec a0 cf d5 8a f8  |.g...%<.;.......|
00000080  2d c6 1a f1 74 ff 44 2d  69 28 f7 fd 1b 72 6f bf  |-...t.D-i(...ro.|
00000090  09 9a 7b ce a2 7c f8 2c  ce 59 8f 20 ac 29 c4 f4  |..{..|.,.Y. .)..|
000000a0  3a ba a6 e7 1d b0 9f 92  b5 9d 60 e1 26 c1 79 98  |:.........`.&.y.|
000000b0  e9 4f c6 c1 7b e6 d3 bd  68 c1 a9 1d 07 08 8f ad  |.O..{...h.......|
000000c0  a2 af ba 2b e3 27 18 3a  fe 08 fa 7c 7f c6 49 cb  |...+.'.:...|..I.|
000000d0  09 39 4b 61 fd 2b ec a7  98 9a ef 2d a1 bd 3c 37  |.9Ka.+.....-..<7|
000000e0  7f 68 91 31 37 7b 6e 9d  1d fe fc f3 05 c7 42 e4  |.h.17{n.......B.|
000000f0  ff 47 e9 bd de a5 cf 22  3c b7 7a d5 fd ad fd bb  |.G....."<.z.....|
00000100  f3 ff bf d8 ca 10 77 d5  e3 92 ad 0e e1 4e 17 2e  |......w......N..|
00000110  6e ab c6 65 c2 c6 8f cb  8a 70 b9 a8 19 97 6b 79  |n..e.....p....ky|
00000120  bd af 42 dc 58 25 bd fa  4c 4a bf cc a8 f2 3b 9e  |..B.X%..LJ....;.|
00000130  d7 13 33 6b 6a 7e 4f d4  76 55 7e af 55 da 76 bc  |..3kj~O.vU~.U.v.|
00000140  2f 57 2a 3f 5b ae ff 0a  8e 93 59 79 b3 1a 55 2f  |/W*?[.....Yy..U/|
00000150  dd 25 f7 7d d6 e7 63 1e  b9 af 5c 6a b2 b0 e7 aa  |.%.}..c...\j....|
00000160  d7 24 fd df 79 6f b3 b1  ee 8f 53 ce 57 73 be c6  |.$..yo....S.Ws..|
00000170  3d 7f f6 d4 e3 7e 36 d7  76 39 8f d4 56 c9 5c 52  |=....~6.v9..V.\R|
00000180  ab b4 5f 99 e7 c7 18 c0  fa 33 5a 35 8b cf f5 5f  |.._......3Z5..._|
00000190  d6 65 e5 1e 37 e7 b1 cc  33 e3 ba 33 f3 fb c5 f7  |.e..7...3..3....|
000001a0  f3 4a 0c e5 3a 41 b9 ea  29 30 17 b0 d8 29 f1 9d  |.J..:A..)0...)..|
000001b0  67 05 3c 25 4a eb c8 22  b1 8a f1 5b a3 e6 00 fe  |g.<%J.."...[....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 a4 0b 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  a4 0b 00 08 2a 01 00 00  |.......0....*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-07-21
Well bootmgr is missing.

Normal boot files should be:
/bootmgr /Boot/BCD /Windows/System32/winload.exe

You only show winload.exe in your windows partition.

Did you also switch drives. Ubuntu says it is in hd1 but you have hd0 or sda where it actually is? Do you have two Ubuntus? grub says it is booting from sda5 which does not look complete or is it a boot partition? Install looks like it is in sda1.

Set windows drive as first boot drive before repairing windows. It then should not overwrite grub.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by ererr10 on 2010-07-21
Something is really wrong, because even when i boot to the repair cd and installation disk it says its missing and all i can do is restart.

Also, the reason there are 2 copies of linux is because im on an ubuntu cd right now. i wanted to see if it was everything or just windows. Windows repair and installation disks both get the bootmgr is missing message, but ubuntu doesnt.

---

### Post by oldfred on 2010-07-21
Sometimes you have to run chkdsk before any repairs so it can see NTFS partition.

---

### Post by ererr10 on 2010-07-24
how do i do that

---

### Post by oldfred on 2010-07-24
To run chkdsk you do need a windows CD that boots. You can use one of these to run chkdsk, but it will not repair XP.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---


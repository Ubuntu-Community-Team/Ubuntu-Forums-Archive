---
title: "New install of ubuntu will not boot"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Justin Smith on 2010-11-12
Ok I am a newbie at this but it seems like it should be working! I had windows on a 80g boot drive. I made a live cd and followed the install prompts. I told it to use the entire disk because I was fed up with windows and wanted rid of it. So everything seem to go perfect and it told me that I need to reboot the machine.So I did and that is were it stops. It runs through all its check screens but after verifying DMI data pool and checking the cd drives it just sets there never changing. So I am using the live cd to get on here and see if I can get some help. The machine has the 80g boot HDD and a 500g sata drive on a PCI raid card. It has a AMD64 dual core processor with 2g memory.The graphics card is a NVIDA something or other can't remember right now. And I don't remember what the mother board is without pulling off the side. I built this computer about three years ago and have had the windows virus on it since I built it and have had it crash so many time I am sick of it.

---

### Post by oldfred on 2010-11-12
Welcome to the forums.

I have nvidia 9600gt and had to do this. If you only have Ubuntu you do not normally get the grub menu. You need to hold down shift key from BIOS until menu appears.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Justin Smith on 2010-11-14
Ok sorry it took me so long to get back. I have tried to do the shift button multiple ways and cannot get it to do anything. For the life of me I cannot get a GRUB boot menu to show up or get it to boot up other than on the  live cd. I have tried holding the shift key down from the time I boot the machine up and have even gone into the BIOS setup and exited out and then held the shift key down. I have tried pressing the space bar at the little keyboard and human figure and tried to make it boot to the HDD from there. So any more ideas anyone. It kinda sucks having to use the cd to get on my machine LOL

---

### Post by drs305 on 2010-11-14
It's probably time for you to run the boot info script. You can do it from the LiveCD. Download the script from the following link, and post the contents of the RESULTS.txt here. It will show us how your system is set up to boot.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

In the post, copy/paste the contents, highlight them, then press the # icon in the menubar to enclose them in 'code' tags (for formatting purposes).

---

### Post by Justin Smith on 2010-11-14
#!/bin/bash
```

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
#hosted at: 
# 
#The birth of the boot info script:
# 
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
# 
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
  system="AIX";;
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
1 system="AST SmartSleep";;
1b) system="Hidden W95 FAT32";;
1c) system="Hidden W95 FAT32 (LBA)";;
1e) system="Hidden W95 FAT16 (LBA)";;
24) system="NEC DOS";;
27) system="Hidden HPFS/NTFS";;
32) system="NOS";;
35) system="JFS on OS2";;
3 system="Theos";;
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
8 system="Linux plaintext";;
8e) system="Linux LVM";;
93) system="Amoeba/Accidently Hidden Linux";;
94) system="Amoeba BBT";;
9f) system="BSD/OS";;
a0) system="IBM Thinkpad hibernation";;
a5) system="FreeBSD";;
a6) system="OpenBSD";;
a7) system="NeXTSTEP";;
a system="Darwin UFS";;
a9) system="NetBSD";;
ab) system="Darwin boot";;
af) system="HFS";;
b0) sytem="Boot Star";;
b1 | b2 | b3 | b4 | b6) system="SpeedStor";; 
b7) system="BSDI fs";;
b system="BSDI swap";;
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
    79d3d6e607f5c244a23c238f2a3df92  system="LVM";;
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
             48 BST="Grub 2's core.img";;
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
            e9d BST="Windows Vista/7";;
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
          if  [ "$(blkid  $drive)" = "" ] || [ "$(blkid  | grep $drive" = "" ]; #Check whether drive is a filesystem
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

    eb4 offset=$(hexdump -v -s 68 -n 4 -e '"%u"' $drive);### 0x44 contains the offset of the next stage
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
    fab BL="No boot loader";;   
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
          name=$(basename $part);  ####  Name of the partition (/dev/sda8 -> sda
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
Fis=':'
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

### Post by Justin Smith on 2010-11-14
sorry didn't see the pound symbol instructions if need be I can re-paste it

---

### Post by matt_symes on 2010-11-14
Hi

You have posted the script itself and not actually run the script. Follow these instructions from the site copied below and post the results of the RESULTS.TXT file. And _please_ use code tags for result. Click the # sign in the menu above  where you are typing to get CODE tags and put the results in between them. The # sign is next to <>. As below.

```
                                                                          
**boot_info_script**  is a bash script which searches all hard drives attached to the  computer for information 
related to booting and displays it in a  convenient format. Its primary use is for troubleshooting booting  problems.                                  
               ** How to use the boot info script**

  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*]  [                                                 Download the Boot Info Script ]("http://sourceforge.net/projects/bootinfoscript")
[*] Open a terminal (Applications>Accessories>Terminal in Gnome) and type   sudo bash [path/to/the/download_folder]/boot_info_script*.sh  For example if you downloaded the file to the desktop, use          sudo bash ~/Desktop/boot_info_script*.sh
[*] If your operation system does not use sudo, use              su 
     bash ~/Desktop/boot_info_script*.sh
[*] You will now have the file RESULTS.txt in the same directory as     the script.[SIZE=-1] But if the script is inside a system directory (like     /usr or /etc) RESULTS.txt will be in the home directory.[/SIZE]
[*] If you already have an existing RESULTS.txt, subsequent  files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of  RESULTS.txt into your next post. Make sure to use the appropriate  formating.   For example in the Ubuntu forums click on the code tags (the symbol #)  before pasting RESULTS.txt.
[/LIST]
 
```

EDIT: What a great script. Kudos to the author.

Kind regards

---

### Post by Justin Smith on 2010-11-14
```


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   153,477,119   153,475,072  83 Linux
/dev/sda2         153,479,166   160,086,015     6,606,850   5 Extended
/dev/sda5         153,479,168   160,086,015     6,606,848  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   437,194,603   437,194,541   7 HPFS/NTFS
/dev/sdb2         437,194,750   976,771,071   539,576,322   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        91ef00a8-bc70-4ac9-98a2-07fc541497dc   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f54f713d-28a4-4c2b-bbca-ed69ae39ea34   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1A30954230952633                       ntfs       Justin 2                      
/dev/sdb2: PTTYPE="dos" 
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
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=91ef00a8-bc70-4ac9-98a2-07fc541497dc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=91ef00a8-bc70-4ac9-98a2-07fc541497dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 91ef00a8-bc70-4ac9-98a2-07fc541497dc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=91ef00a8-bc70-4ac9-98a2-07fc541497dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f54f713d-28a4-4c2b-bbca-ed69ae39ea34 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  23.7GB: boot/grub/core.img
   8.7GB: boot/grub/grub.cfg
   9.3GB: boot/initrd.img-2.6.35-22-generic
  23.7GB: boot/vmlinuz-2.6.35-22-generic
   9.3GB: initrd.img
  23.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 22 80 26 00 32 00 19  00 2e 00 34 00 1e 00 3c  |.".&.2.....4...<|
00000010  00 42 00 2c 00 45 00 47  00 32 00 34 00 36 80 20  |.B.,.E.G.2.4.6. |
00000020  00 2a 00 2e 00 1c 80 29  80 2d 80 1b 00 27 80 30  |.*.....).-...'.0|
00000030  00 14 80 26 00 30 00 14  00 27 80 34 00 0f 80 2d  |...&.0...'.4...-|
00000040  80 3b 80 15 00 34 00 42  00 1b 80 35 00 43 80 1c  |.;...4.B...5.C..|
00000050  80 2f 00 39 00 1a 00 29  80 32 80 13 00 23 00 29  |./.9...).2...#.)|
00000060  80 11 00 22 00 28 80 10  80 24 80 2a 80 14 80 26  |...".(...$.*...&|
00000070  80 2c 00 17 80 28 80 30  80 18 80 29 00 31 80 19  |.,...(.0...).1..|
00000080  80 27 80 33 80 16 00 2b  00 37 00 1a 00 2e 00 37  |.'.3...+.7.....7|
00000090  00 16 80 2e 80 37 80 16  80 30 80 36 80 16 80 2d  |.....7...0.6...-|
000000a0  80 33 80 13 00 26 00 2e  00 11 00 1d 00 25 00 08  |.3...&.......%..|
000000b0  80 1f 00 2d 80 0c 80 25  00 33 80 12 00 24 00 36  |...-...%.3...$.6|
000000c0  80 0e 00 28 80 39 80 12  00 2f 80 3e 00 1a 80 39  |...(.9.../.>...9|
000000d0  00 49 80 24 00 3b 00 46  00 2a 80 31 80 3c 80 20  |.I.$.;.F.*.1.<. |
000000e0  80 30 00 3b 80 26 00 3d  80 47 00 33 00 43 80 48  |.0.;.&.=.G.3.C.H|
000000f0  00 38 80 3b 00 41 00 31  80 31 80 32 00 25 80 2e  |.8.;.A.1.1.2.%..|
00000100  80 2f 00 22 80 2c 80 2f  80 1d 80 2a 00 2d 80 1b  |./.".,./...*.-..|
00000110  80 22 00 2b 00 10 80 24  00 2d 00 12 00 2c 00 38  |.".+...$.-...,.8|
00000120  00 14 00 2f 00 3b 80 17  80 2e 00 39 00 12 80 30  |.../.;.....9...0|
00000130  00 3b 00 14 80 33 00 3b  00 14 00 31 80 38 80 11  |.;...3.;...1.8..|
00000140  80 31 80 3d 80 11 80 31  00 3e 00 12 00 34 00 3e  |.1.=...1.>...4.>|
00000150  80 0f 00 36 00 40 80 11  80 3a 80 41 00 15 00 39  |...6.@...:.A...9|
00000160  00 40 80 13 00 36 00 3b  80 17 80 34 00 3a 00 16  |.@...6.;...4.:..|
00000170  00 32 80 36 80 1e 00 2e  80 32 80 1a 00 2a 00 30  |.2.6.....2...*.0|
00000180  80 1c 00 26 00 2c 80 18  00 24 00 2c 00 14 80 26  |...&.,...$.,...&|
00000190  80 2e 80 16 80 29 00 32  00 14 00 2e 80 36 80 18  |.....).2.....6..|
000001a0  00 2a 00 37 00 12 80 28  80 35 80 10 00 28 80 34  |.*.7...(.5...(.4|
000001b0  00 10 00 30 80 3c 00 18  00 37 80 41 80 1f 00 fe  |...0.<...7.A....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 64 00 00 00  |............d...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  f9 b4 58 91 52 d6 a1 f3  c0 1d 02 1f fc 74 08 ff  |..X.R........t..|
00000010  fb 84 36 f8 38 02 d4 80  0e 88 a0 8e 00 fc 80 0d  |..6.8...........|
00000020  2b 7d d4 01 92 51 22 81  1f ff 30 86 df 0a 00 5f  |+}...Q"...0...._|
00000030  0d ff 11 e4 04 50 06 78  00 d2 b7 a1 ff 3f 1b 2e  |.....P.x.....?..|
00000040  9a 89 fd 4b 04 10 15 23  80 39 00 67 b9 d3 ab e4  |...K...#.9.g....|
00000050  dd 52 e4 9e 50 fb 6d 18  df 0c 00 5a 00 f3 ec 00  |.R..P.m....Z....|
00000060  fb f9 c0 a1 59 44 65 32  a3 91 09 e6 48 ba a4 d9  |....YDe2....H...|
00000070  46 45 6a ff 80 09 84 80  3c 00 ac 8e ba fa 2f 0c  |FEj.....<...../.|
00000080  31 d9 2f 96 2a db 52 a8  4b 40 05 a4 51 1d 00 36  |1./.*.R.K@..Q..6|
00000090  f7 d4 c3 32 65 8a 3f 21  e8 30 b6 d8 59 1e 45 74  |...2e.?!.0..Y.Et|
000000a0  8a b1 15 b7 9f 15 fb 1e  a9 25 50 98 d4 5f aa 82  |.........%P.._..|
000000b0  07 eb 11 78 ff 00 3a f7  17 e7 92 6f c5 4d 3a 5a  |...x..:....o.M:Z|
000000c0  5c 21 8c 6f d5 60 80 09  0f 7f c0 01 b9 1c c8 f7  |\!.o.`..........|
000000d0  19 0f 29 6d 54 48 3d 46  37 cf 01 03 f4 bb e7 dc  |..)mTH=F7.......|
000000e0  00 8b bd af 96 00 1e ca  81 94 fc 81 8a 5b 6e 04  |.............[n.|
000000f0  00 35 22 7c 70 00 e3 fd  9d ef 97 04 5f 74 7c 2e  |.5"|p......._t|.|
00000100  dd dc b4 a5 19 8d e2 ff  a1 85 c1 85 df 06 f7 40  |...............@|
00000110  1f d3 62 0f 2b d5 b7 81  00 79 fc f7 82 85 fb 70  |..b.+....y.....p|
00000120  f0 0b 35 ef e9 fd 89 1b  b2 d3 5f 98 3c a1 ac 80  |..5......._.<...|
00000130  0d c0 1b 11 05 fd be bc  fd c0 1f 93 c4 73 f3 82  |.............s..|
00000140  64 cd 47 3b 38 89 1d 62  d3 4b 3e 46 1f d0 07 9d  |d.G;8..b.K>F....|
00000150  e7 df 45 fc 91 6b 9c ee  f5 ee eb 36 19 1c 61 9c  |..E..k.....6..a.|
00000160  16 32 48 5d 53 db d7 09  00 28 15 84 6e bd a8 b7  |.2H]S....(..n...|
00000170  bc 51 82 e5 9b 62 dd e6  a9 b1 10 e6 e9 7b e8 91  |.Q...b.......{..|
00000180  68 b1 6d 2a 34 3b 20 8e  96 aa 48 5d 6a 27 38 01  |h.m*4; ...H]j'8.|
00000190  18 02 32 20 03 d2 35 13  c2 68 a8 23 3a f6 b9 24  |..2 ..5..h.#:..$|
000001a0  96 bc fb a1 a9 0e 6f 43  fc fa 68 00 88 5d bd ba  |......oC..h..]..|
000001b0  70 23 ca 4e ad 2f 75 f5  77 cb 0b 95 2d c3 00 00  |p#.N./u.w...-...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2010-11-14
Grub was installed on sdb but your Ubuntu OS is on sda1.

To install G2 on Ubuntu's drive/partition, boot the LiveCD and run these two commands. Note the first contains the partition (sda1) but the second only the drive (sda).
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Make sure your BIOS points to sda first during boot.

---

### Post by Justin Smith on 2010-11-14
Ok two questions: where do I enter this command line? In terminal? And by making sure my BIOS points to sda first do you mean checks the HDD first instead of the cd? I know dumb questions! I guess that was three questions

---

### Post by drs305 on 2010-11-14
> **Justin Smith said:**
> Ok two questions: where do I enter this command line? In terminal? And by making sure my BIOS points to sda first do you mean checks the HDD first instead of the cd? I know dumb questions! I guess that was three questions

Yes, open a terminal while running the LiveCD: Applications, Accessories, Terminal.

Your BIOS is set to boot drives in a specified order. Grub will be installed correctly in the MBR of your Ubuntu (sda) drive. You want to make sure the BIOS points to sda and not sdb.

To enter BIOS, normally you press the DEL key or one of the F function keys to access the BIOS setup pages. Sometimes which key to press is displayed on the screen as the computer powers up.

Here's a linux hint about copying commands. It's easier and more accurate to copy/paste. In linux, just highlight the command or text line with your mouse (no buttons are necessary). Place the mouse cursor where you want to insert it and click the middle mouse button to paste.

---

### Post by Justin Smith on 2010-11-14
HOT DOG!! It works thank you so much! Ok this is my first boot up without the live cd so I have to go explore. Thank you again.

---


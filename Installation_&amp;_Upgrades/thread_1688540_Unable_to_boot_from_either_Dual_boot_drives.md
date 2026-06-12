---
title: "Unable to boot from either Dual boot drives"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-15
I can only use the Live CD to operate Ubuntu. After typing in the command sudo fdisk -l, I get the following?

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27966   224636863+   7  HPFS/NTFS
/dev/sda2           27967       38164    81915435   83  Linux
/dev/sda3           38165       38914     6013953    5  Extended
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris

And when I boot without the Live CD, I get the following message in the GNU GRUB Version 1.98-1ubuntu7 window page. Any suggestions would be helpful. Thank you.

---

### Post by oldfred on 2011-02-15
Claude,

I thought we got you working.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by F8M on 2011-02-16
Hi OldFred. I think it was one of my Windows update that disconfigured my grub or something like that. Here's the info you requested - I just you can help me.
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
#	      BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file	##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> "$Log1" ; 
#             
#	  fi;
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
A big thank you.

---

### Post by oldfred on 2011-02-16
You posted script. You need to run script and post results.txt that it makes.

Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's  menu and then paste the contents between the generated [ code] paste  here [ /code] tags.

---

### Post by JayneScarlett on 2011-02-16
> **oldfred said:**
> Claude,

I thought we got you working.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

I think I have the same problem as Claude, or similar...  [B][http://ubuntuforums.org/showthread.php?t=1689388](http://ubuntuforums.org/showthread.php?t=1689388)

[/B]On trying to boot, I get the folowing messages: 

Try (hd,0): NTFS5: error no such device ubuntu/disks/root.disk.

Try (hd,0): NTFS5: error no such device ubuntu/install/boot/grub/grub.cfg.

Then this screen: GNU GRUB version 1.98 - 1ubuntu6

--- 

I'm less experienced and have not tried to rebot with a Live CD. Can you help a neophyte, F8M? Ubuntu is holding several deadlines hotage including play for competition and one piece of investigative journalism, both due tomorrow am!

Thanks a million in advance!

---

### Post by wilee-nilee on 2011-02-16
> **JayneScarlett said:**
> I think I have the same problem as Claude, or similar...  [B][http://ubuntuforums.org/showthread.php?t=1689388](http://ubuntuforums.org/showthread.php?t=1689388)

[/B]On trying to boot, I get the folowing messages: 

Try (hd,0): NTFS5: error no such device ubuntu/disks/root.disk.

Try (hd,0): NTFS5: error no such device ubuntu/install/boot/grub/grub.cfg.

Then this screen: GNU GRUB version 1.98 - 1ubuntu6

--- 

I'm less experienced and have not tried to rebot with a Live CD. Can you help a neophyte, F8M? Ubuntu is holding several deadlines hotage including play for competition and one piece of investigative journalism, both due tomorrow am!

Thanks a million in advance!

Although it seems similar, generally its not. So the best thing to do here is to start your own thread and post the bootscript that oldfred linked, it is also in my signature.

---

### Post by F8M on 2011-02-16
Ok oldFred,I typed in the following sudo command:
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot infoscript055.sh
bash: /home/ubuntu/Desktop/boot: No such file or directory
ubuntu@ubuntu:~$
OR
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot infoscript*.sh
bash: /home/ubuntu/Desktop/boot: No such file or directory
ubuntu@ubuntu:~$ 
Where do I go from here.

---

### Post by presence1960 on 2011-02-16
> **F8M said:**
> Ok oldFred,I typed in the following sudo command:
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot infoscript055.sh
bash: /home/ubuntu/Desktop/boot: No such file or directory
ubuntu@ubuntu:~$
OR
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot infoscript*.sh
bash: /home/ubuntu/Desktop/boot: No such file or directory
ubuntu@ubuntu:~$ 
Where do I go from here.

Not where do you go from here, but rather where does the boot info script that you downloaded go! **_Move it to desktop!!!!!!!!!!_**
Here it all is:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by F8M on 2011-02-17
After being unable to get the sudo bash command to work, I went to see if there was anything wrong in the Gparted. I was surprised to see the /dev/sda into the /dev/sdb(storage drive) and /dev/sdb into my /dev/sda.
Here is what is shown in Gparted for my storage drive(/dev/sda):
Partition-------File-System------Label--------Size------. . .
unallocated-----unallocated-------------------1.00MiB---. . .
/dev/sda1---------ntfs---------100GB drive---93.16GiB---. . .

And here is what is shown in Gparted for my dual-boot drive(/dev/sdb):
Partition-------File-System------Label-------Size-------Flags
/dev/sdb1-------ntfs(error)------Vista------214.23GiB---boot
/dev/sdb2--------ext4-----------Ubuntu-------78.12GiB-------
unallocated-----unallocated-------------------4.49MiB-------
/dev/sdb3--------extended---------------------5.74GiB-------
/dev/sdb5-------linux-swap--------------------5.74GiB-------

I would appreciate any suggestions how to fix this. Thanks

---

### Post by oldfred on 2011-02-17
If you copy the command presence1960 posted, it should work. You were using spaces, not underscores when you were typing it. Much better to just copy command.

Copy & paste the results.txt in code tags so we can see it. Thanks.

---

### Post by F8M on 2011-02-17
Wow, I don't know how I miss the underscore part.
Ok, here is the Text result.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   195,366,887   195,364,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   449,273,789   449,273,727   7 HPFS/NTFS
/dev/sdb2         449,273,790   613,104,659   163,830,870  83 Linux
/dev/sdb3         613,113,854   625,141,759    12,027,906   5 Extended
/dev/sdb5         613,113,856   625,141,759    12,027,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5842DB8842DB6970                       ntfs       100GB Drive                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2C2B79D13BA924A1                       ntfs       Vista Home Premium            
/dev/sdb2        0b54f8c5-9c78-4c95-8494-bb38cfacdf98   ext4       UbuntuLTS10.04                
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        b71c468a-fdb9-4bfa-9ce7-1368550ca01b   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/100GB Drive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

============================= sdb2/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b71c468a-fdb9-4bfa-9ce7-1368550ca01b none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 281.7GB: boot/grub/core.img
 240.6GB: boot/grub/grub.cfg
 283.8GB: boot/initrd.img-2.6.32-29-generic
 283.8GB: boot/vmlinuz-2.6.32-29-generic
 259.1GB: grub/core.img
 230.0GB: grub/grub.cfg
 283.8GB: initrd.img
 283.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ba 9b 5d 68 93 3c 9b 3c  c7 09 eb 91 22 39 d3 69  |..]h.<.<...."9.i|
00000010  53 88 bd 9f 01 c1 e9 38  6a 4a 8c 60 06 d8 60 0d  |S......8jJ.`..`.|
00000020  99 67 43 0c e9 b8 ce 36  ae bd ab af 1d 17 3b 8c  |.gC....6......;.|
00000030  1b 10 eb ba d1 38 a4 b6  97 e1 61 b9 b6 05 f1 4d  |.....8....a....M|
00000040  ec b7 93 4f 84 c8 e7 d8  b4 28 7b 83 d3 00 e9 b4  |...O.....({.....|
00000050  2f 82 80 1f 88 06 34 07  bd 9c 07 4d 3e bc 63 8e  |/.....4....M>.c.|
00000060  cf 1b 11 6c 7a 91 e7 bc  4c aa 41 29 41 29 88 51  |...lz...L.A)A).Q|
00000070  99 67 44 0c 09 b9 ff 17  77 7d fb f9 fd b8 a1 90  |.gD.....w}......|
00000080  23 5a 10 3e cf f1 a6 d6  d4 96 36 40 9b 6c 45 98  |#Z.>......6@.lE.|
00000090  16 3f e2 ef e4 1a e3 ce  92 01 22 a6 a2 4e f1 bd  |.?........"..N..|
000000a0  ce ad a9 7a 6c 00 96 67  84 2c 8e 0a 13 3b 11 32  |...zl..g.,...;.2|
000000b0  11 64 39 10 44 03 f2 b5  e6 a1 27 13 9b 35 a1 41  |.d9.D.....'..5.A|
000000c0  99 67 45 0c 90 36 41 79  2c 4e 30 4b b1 b9 82 71  |.gE..6Ay,N0K...q|
000000d0  07 81 90 36 45 34 82 43  b1 13 4b 63 3c e1 a7 80  |...6E4.C..Kc<...|
000000e0  90 36 da 21 60 a8 68 d0  22 96 72 ae 93 f0 90 36  |.6.!`.h.".r....6|
000000f0  92 30 07 e9 b1 51 45 21  f4 51 c1 07 00 36 49 85  |.0...QE!.Q...6I.|
00000100  c2 87 06 8b c3 42 00 36  0e c6 f6 00 00 00 00 00  |.....B.6........|
00000110  99 67 46 0c f8 af e7 8f  e5 f8 e4 f6 47 73 2f 33  |.gF.........Gs/3|
00000120  37 af df 25 9a ff 17 f5  37 7a d6 d6 93 aa 56 45  |7..%....7z....VE|
00000130  ff 2b fd ff 7f b9 d5 cf  d6 db 45 4b 73 5f f2 2f  |.+........EKs_./|
00000140  e4 4f e4 1d fb 3a b9 32  c2 63 66 51 1c bb 66 76  |.O...:.2.cfQ..fv|
00000150  2c 51 8e 86 5a 15 f0 b4  41 5c 47 0d 82 85 74 c0  |,Q..Z...A\G...t.|
00000160  99 67 47 0c ef af 5e c8  fa b1 e7 fa 11 db b4 ee  |.gG...^.........|
00000170  ce 81 fb 2f e3 1b d2 47  34 9f 57 42 0b 31 8d c4  |.../...G4.WB.1..|
00000180  09 2b fb 60 22 a5 99 d4  ea f3 61 b0 e7 1d 0e 2c  |.+.`".....a....,|
00000190  ff c6 7d f9 4d 24 27 50  00 14 0a 10 25 3d d3 52  |..}.M$'P....%=.R|
000001a0  b9 93 03 03 ac 28 e7 3b  03 c3 38 17 03 85 1c 71  |.....(.;..8....q|
000001b0  99 67 48 0c ec 20 1c 70  bc 9c 4e 2d 5a 50 00 fe  |.gH.. .p..N-ZP..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```
Thank you.

---

### Post by oldfred on 2011-02-17
You have two /boot folders in windows. I have seen it where grub installs a /boot and windows has a /Boot. In Linux capitals are different than small letters, but in windows they are the same so windows cannot boot with two folders the same. But even Linux should not let you create two /boot folders.

```
sdb1: __________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr [COLOR=Red]/boot/BCD[/COLOR] /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]

```

Delete the /boot/grub/core.img folder and anything else in it, but be careful not to delete /boot/BCD as windows has to have that.

Then from Ubuntu run:
```

sudo update-grub
```

Did you change drive order? I see the grub.cfg thinks it is hd0 but is now sdb or hd1? The update grub will probably change it anyway.

---

### Post by F8M on 2011-02-17
Ok oldFred, I am being extra careful here. How do you delete the /boot/grub/core.img folder and anything else in it, and not the /boot/BCD, before I go ahead and reboot without the Live CD with the sudo update-grub.

---

### Post by oldfred on 2011-02-17
You need to do it from Ubuntu liveCD. It should let you mount the windows partition and drill down to windows root which in windows, most if not all the files, are normally hidden.

If real concerned you can also copy any folders to an external device, so you could copy back if you delete the wrong folder. Probably just changing folder name from /boot to /boota or any name that is not /boot would get you working again.

---

### Post by F8M on 2011-02-18
Wow, oldFred you make this look complicted. I know how to mount Windows or Ubuntu, but when it comes to root files or copying folders to another folder with a different name like /boota.

The first question I have here; if I go ahead to mount Windows, would I also erase all folders with all new ones?

---

### Post by oldfred on 2011-02-18
No.

You only want to remove from windows the second /boot that also contains grub files, not the folder with BCD.

You should from liveCD just see your windows in the left panel, It may have a label or just be 214GB as  a default label. When you click on it you should be at the lowest level of windows which is its root. Then you should see folders.

/boot
/boot
/windows

etc.
Check which /boot has BCD and make sure not to delete it. Check that the other /boot has grub type files and delete. If you want to rename just right click.

Have you gone thru some of the new user instructions?
Beginners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485) (Newbie 101) 
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (Terminal for Beginners)

---

### Post by F8M on 2011-02-19
Hi oldFred, thanks for the info guides.
In the left panel I get to see the following info:
/boot (VISTA)
/boot (UBUNTU)
/windows (100GB)

Both the Vista and the 100GB drives have a BOOT folder with BCD files at the end as shown below.
/media/Vista Home Premium/boot/cs-CZ
/media/Vista Home Premium/boot/da-DK
/media/Vista Home Premium/boot/de-DE
/media/Vista Home Premium/boot/el-GR
/media/Vista Home Premium/boot/en-US
/media/Vista Home Premium/boot/es-ES
/media/Vista Home Premium/boot/fi-FI
/media/Vista Home Premium/boot/Fonts
/media/Vista Home Premium/boot/fr-FR
/media/Vista Home Premium/boot/grub
/media/Vista Home Premium/boot/hu-HU
/media/Vista Home Premium/boot/it-IT
/media/Vista Home Premium/boot/ja-JP
/media/Vista Home Premium/boot/ko-KR
/media/Vista Home Premium/boot/nb-NO
/media/Vista Home Premium/boot/nl-NL
/media/Vista Home Premium/boot/pl-PL
/media/Vista Home Premium/boot/pt-BR
/media/Vista Home Premium/boot/pt-PT
/media/Vista Home Premium/boot/ru-RU
/media/Vista Home Premium/boot/sv-SE
/media/Vista Home Premium/boot/tr-TR
/media/Vista Home Premium/boot/zh-CN
/media/Vista Home Premium/boot/zh-HK
/media/Vista Home Premium/boot/zh-TW
/media/Vista Home Premium/boot/BCD
/media/Vista Home Premium/boot/BCD.LOG
/media/Vista Home Premium/boot/memtest.exe
 
and here is the 100GB dive
/media/100GB Drive/Boot/cs-CZ
/media/100GB Drive/Boot/da-DK
/media/100GB Drive/Boot/de-DE
/media/100GB Drive/Boot/el-GR
/media/100GB Drive/Boot/en-US
/media/100GB Drive/Boot/es-ES
/media/100GB Drive/Boot/fi-FI
/media/100GB Drive/Boot/Fonts
/media/100GB Drive/Boot/fr-FR
/media/100GB Drive/Boot/hu-HU
/media/100GB Drive/Boot/it-IT
/media/100GB Drive/Boot/ja-JP
/media/100GB Drive/Boot/ko-KR
/media/100GB Drive/Boot/nb-NO
/media/100GB Drive/Boot/nl-NL
/media/100GB Drive/Boot/pl-PL
/media/100GB Drive/Boot/pt-BR
/media/100GB Drive/Boot/pt-PT
/media/100GB Drive/Boot/ru-RU
/media/100GB Drive/Boot/sv-SE
/media/100GB Drive/Boot/tr-TR
/media/100GB Drive/Boot/zh-CN
/media/100GB Drive/Boot/zh-HK
/media/100GB Drive/Boot/zh-TW
/media/100GB Drive/Boot/BCD
/media/100GB Drive/Boot/BCD.LOG
/media/100GB Drive/Boot/BCD.LOG1
/media/100GB Drive/Boot/BCD.LOG2
/media/100GB Drive/Boot/bootstat.dat
/media/100GB Drive/Boot/memtest.exe

Now with all this info given to you, my question is - Should I delete everything in the 100GB Drive/Boot except only the 100GB Drive/Boot/BCD? Which means that the BCD.LOG, BCD.LOG1, and BCD.LOG2 will be deleted.

---

### Post by oldfred on 2011-02-20
Both show BCD, so no those are not the ones to delete. 

I am not sure what the 100GB drive is. The boot I want you to delete was in the VISTA partition. Or is the Vista partition a recovery partition and the 100GB is your full windows install.

Rerun boot script, so we can see what is where now.

---

### Post by F8M on 2011-02-21
The 100GB Drive(sda1) is my storage drive which is not partitioned, and it is completely separate from the Vista/Ubuntu partitioned drive.
Here is the boot script you requested, it seems the problem is in the sdb1(Vista in my Vista/Ubuntu drive).

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   195,366,887   195,364,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   449,273,789   449,273,727   7 HPFS/NTFS
/dev/sdb2         449,273,790   613,104,659   163,830,870  83 Linux
/dev/sdb3         613,113,854   625,141,759    12,027,906   5 Extended
/dev/sdb5         613,113,856   625,141,759    12,027,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5842DB8842DB6970                       ntfs       100GB Drive                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2C2B79D13BA924A1                       ntfs       Vista Home Premium            
/dev/sdb2        0b54f8c5-9c78-4c95-8494-bb38cfacdf98   ext4       UbuntuLTS10.04                
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        b71c468a-fdb9-4bfa-9ce7-1368550ca01b   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

============================= sdb2/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b71c468a-fdb9-4bfa-9ce7-1368550ca01b none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 281.7GB: boot/grub/core.img
 240.6GB: boot/grub/grub.cfg
 283.8GB: boot/initrd.img-2.6.32-29-generic
 283.8GB: boot/vmlinuz-2.6.32-29-generic
 259.1GB: grub/core.img
 230.0GB: grub/grub.cfg
 283.8GB: initrd.img
 283.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ba 9b 5d 68 93 3c 9b 3c  c7 09 eb 91 22 39 d3 69  |..]h.<.<...."9.i|
00000010  53 88 bd 9f 01 c1 e9 38  6a 4a 8c 60 06 d8 60 0d  |S......8jJ.`..`.|
00000020  99 67 43 0c e9 b8 ce 36  ae bd ab af 1d 17 3b 8c  |.gC....6......;.|
00000030  1b 10 eb ba d1 38 a4 b6  97 e1 61 b9 b6 05 f1 4d  |.....8....a....M|
00000040  ec b7 93 4f 84 c8 e7 d8  b4 28 7b 83 d3 00 e9 b4  |...O.....({.....|
00000050  2f 82 80 1f 88 06 34 07  bd 9c 07 4d 3e bc 63 8e  |/.....4....M>.c.|
00000060  cf 1b 11 6c 7a 91 e7 bc  4c aa 41 29 41 29 88 51  |...lz...L.A)A).Q|
00000070  99 67 44 0c 09 b9 ff 17  77 7d fb f9 fd b8 a1 90  |.gD.....w}......|
00000080  23 5a 10 3e cf f1 a6 d6  d4 96 36 40 9b 6c 45 98  |#Z.>......6@.lE.|
00000090  16 3f e2 ef e4 1a e3 ce  92 01 22 a6 a2 4e f1 bd  |.?........"..N..|
000000a0  ce ad a9 7a 6c 00 96 67  84 2c 8e 0a 13 3b 11 32  |...zl..g.,...;.2|
000000b0  11 64 39 10 44 03 f2 b5  e6 a1 27 13 9b 35 a1 41  |.d9.D.....'..5.A|
000000c0  99 67 45 0c 90 36 41 79  2c 4e 30 4b b1 b9 82 71  |.gE..6Ay,N0K...q|
000000d0  07 81 90 36 45 34 82 43  b1 13 4b 63 3c e1 a7 80  |...6E4.C..Kc<...|
000000e0  90 36 da 21 60 a8 68 d0  22 96 72 ae 93 f0 90 36  |.6.!`.h.".r....6|
000000f0  92 30 07 e9 b1 51 45 21  f4 51 c1 07 00 36 49 85  |.0...QE!.Q...6I.|
00000100  c2 87 06 8b c3 42 00 36  0e c6 f6 00 00 00 00 00  |.....B.6........|
00000110  99 67 46 0c f8 af e7 8f  e5 f8 e4 f6 47 73 2f 33  |.gF.........Gs/3|
00000120  37 af df 25 9a ff 17 f5  37 7a d6 d6 93 aa 56 45  |7..%....7z....VE|
00000130  ff 2b fd ff 7f b9 d5 cf  d6 db 45 4b 73 5f f2 2f  |.+........EKs_./|
00000140  e4 4f e4 1d fb 3a b9 32  c2 63 66 51 1c bb 66 76  |.O...:.2.cfQ..fv|
00000150  2c 51 8e 86 5a 15 f0 b4  41 5c 47 0d 82 85 74 c0  |,Q..Z...A\G...t.|
00000160  99 67 47 0c ef af 5e c8  fa b1 e7 fa 11 db b4 ee  |.gG...^.........|
00000170  ce 81 fb 2f e3 1b d2 47  34 9f 57 42 0b 31 8d c4  |.../...G4.WB.1..|
00000180  09 2b fb 60 22 a5 99 d4  ea f3 61 b0 e7 1d 0e 2c  |.+.`".....a....,|
00000190  ff c6 7d f9 4d 24 27 50  00 14 0a 10 25 3d d3 52  |..}.M$'P....%=.R|
000001a0  b9 93 03 03 ac 28 e7 3b  03 c3 38 17 03 85 1c 71  |.....(.;..8....q|
000001b0  99 67 48 0c ec 20 1c 70  bc 9c 4e 2d 5a 50 00 fe  |.gH.. .p..N-ZP..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```
A big Thank you. - - - CLAUDE

---

### Post by oldfred on 2011-02-21
That is correct.

/boot/BCD
/boot/grub/core.img

Since they are both /boot not one /Boot. The /boot/grub is then in the same folder (/boot) as BCD and other windows files. If you can see /boot/grub delete that but not others files in /boot.

---

### Post by F8M on 2011-02-21
When I went into Vista and open the boot folder, then the grub folder, I found the core.img file. 
Now to make sure I do this right, do I delete only
/media/Vista Home Premium/boot/grub/core.img as listed below
or all the grub Folder that doesn`t have /boot/BCD, which is 
all the files below.

/media/Vista Home Premium/boot/grub/locale
/media/Vista Home Premium/boot/grub/915resolution.mod
/media/Vista Home Premium/boot/grub/acpi.mod
/media/Vista Home Premium/boot/grub/affs.mod
/media/Vista Home Premium/boot/grub/afs.mod
/media/Vista Home Premium/boot/grub/afs_be.mod
/media/Vista Home Premium/boot/grub/aout.mod
/media/Vista Home Premium/boot/grub/ata.mod
/media/Vista Home Premium/boot/grub/ata_pthru.mod
/media/Vista Home Premium/boot/grub/at_keyboard.mod
/media/Vista Home Premium/boot/grub/befs.mod
/media/Vista Home Premium/boot/grub/befs_be.mod
/media/Vista Home Premium/boot/grub/biosdisk.mod
/media/Vista Home Premium/boot/grub/bitmap.mod
/media/Vista Home Premium/boot/grub/bitmap_scale.mod
/media/Vista Home Premium/boot/grub/blocklist.mod
/media/Vista Home Premium/boot/grub/boot.img
/media/Vista Home Premium/boot/grub/boot.mod
/media/Vista Home Premium/boot/grub/bsd.mod
/media/Vista Home Premium/boot/grub/bufio.mod
/media/Vista Home Premium/boot/grub/cat.mod
/media/Vista Home Premium/boot/grub/cdboot.img
/media/Vista Home Premium/boot/grub/chain.mod
/media/Vista Home Premium/boot/grub/charset.mod
/media/Vista Home Premium/boot/grub/cmp.mod
/media/Vista Home Premium/boot/grub/command.lst
/media/Vista Home Premium/boot/grub/configfile.mod
/media/Vista Home Premium/boot/grub/core.img
/media/Vista Home Premium/boot/grub/cpio.mod
/media/Vista Home Premium/boot/grub/cpuid.mod
/media/Vista Home Premium/boot/grub/crc.mod
/media/Vista Home Premium/boot/grub/crypto.lst
/media/Vista Home Premium/boot/grub/crypto.mod
/media/Vista Home Premium/boot/grub/date.mod
/media/Vista Home Premium/boot/grub/datehook.mod
/media/Vista Home Premium/boot/grub/datetime.mod
/media/Vista Home Premium/boot/grub/diskboot.img
/media/Vista Home Premium/boot/grub/dm_nv.mod
/media/Vista Home Premium/boot/grub/drivemap.mod
/media/Vista Home Premium/boot/grub/echo.mod
/media/Vista Home Premium/boot/grub/efiemu.mod
/media/Vista Home Premium/boot/grub/efiemu32.o
/media/Vista Home Premium/boot/grub/efiemu64.o
/media/Vista Home Premium/boot/grub/elf.mod
/media/Vista Home Premium/boot/grub/example_functional_test.mod
/media/Vista Home Premium/boot/grub/ext2.mod
/media/Vista Home Premium/boot/grub/extcmd.mod
/media/Vista Home Premium/boot/grub/fat.mod
/media/Vista Home Premium/boot/grub/font.mod
/media/Vista Home Premium/boot/grub/fs.lst
/media/Vista Home Premium/boot/grub/fshelp.mod
/media/Vista Home Premium/boot/grub/functional_test.mod
/media/Vista Home Premium/boot/grub/gcry_arcfour.mod
/media/Vista Home Premium/boot/grub/gcry_blowfish.mod
/media/Vista Home Premium/boot/grub/gcry_camellia.mod
/media/Vista Home Premium/boot/grub/gcry_cast5.mod
/media/Vista Home Premium/boot/grub/gcry_crc.mod
/media/Vista Home Premium/boot/grub/gcry_des.mod
/media/Vista Home Premium/boot/grub/gcry_md4.mod
/media/Vista Home Premium/boot/grub/gcry_md5.mod
/media/Vista Home Premium/boot/grub/gcry_rfc2268.mod
/media/Vista Home Premium/boot/grub/gcry_rijndael.mod
/media/Vista Home Premium/boot/grub/gcry_rmd160.mod
/media/Vista Home Premium/boot/grub/gcry_seed.mod
/media/Vista Home Premium/boot/grub/gcry_serpent.mod
/media/Vista Home Premium/boot/grub/gcry_sha1.mod
/media/Vista Home Premium/boot/grub/gcry_sha256.mod
/media/Vista Home Premium/boot/grub/gcry_sha512.mod
/media/Vista Home Premium/boot/grub/gcry_tiger.mod
/media/Vista Home Premium/boot/grub/gcry_twofish.mod
/media/Vista Home Premium/boot/grub/gcry_whirlpool.mod
/media/Vista Home Premium/boot/grub/gettext.mod
/media/Vista Home Premium/boot/grub/gfxmenu.mod
/media/Vista Home Premium/boot/grub/gfxterm.mod
/media/Vista Home Premium/boot/grub/gptsync.mod
/media/Vista Home Premium/boot/grub/grldr.img
/media/Vista Home Premium/boot/grub/grubenv
/media/Vista Home Premium/boot/grub/gzio.mod
/media/Vista Home Premium/boot/grub/halt.mod
/media/Vista Home Premium/boot/grub/handler.lst
/media/Vista Home Premium/boot/grub/handler.mod
/media/Vista Home Premium/boot/grub/hashsum.mod
/media/Vista Home Premium/boot/grub/hdparm.mod
/media/Vista Home Premium/boot/grub/hello.mod
/media/Vista Home Premium/boot/grub/help.mod
/media/Vista Home Premium/boot/grub/hexdump.mod
/media/Vista Home Premium/boot/grub/hfs.mod
/media/Vista Home Premium/boot/grub/hfsplus.mod
/media/Vista Home Premium/boot/grub/iso9660.mod
/media/Vista Home Premium/boot/grub/jfs.mod
/media/Vista Home Premium/boot/grub/jpeg.mod
/media/Vista Home Premium/boot/grub/kernel.img
/media/Vista Home Premium/boot/grub/keystatus.mod
/media/Vista Home Premium/boot/grub/linux.mod
/media/Vista Home Premium/boot/grub/linux16.mod
/media/Vista Home Premium/boot/grub/lnxboot.img
/media/Vista Home Premium/boot/grub/loadenv.mod
/media/Vista Home Premium/boot/grub/loopback.mod
/media/Vista Home Premium/boot/grub/ls.mod
/media/Vista Home Premium/boot/grub/lsmmap.mod
/media/Vista Home Premium/boot/grub/lspci.mod
/media/Vista Home Premium/boot/grub/lvm.mod
/media/Vista Home Premium/boot/grub/mdraid.mod
/media/Vista Home Premium/boot/grub/memdisk.mod
/media/Vista Home Premium/boot/grub/memrw.mod
/media/Vista Home Premium/boot/grub/minicmd.mod
/media/Vista Home Premium/boot/grub/minix.mod
/media/Vista Home Premium/boot/grub/mmap.mod
/media/Vista Home Premium/boot/grub/moddep.lst
/media/Vista Home Premium/boot/grub/msdospart.mod
/media/Vista Home Premium/boot/grub/multiboot.mod
/media/Vista Home Premium/boot/grub/multiboot2.mod
/media/Vista Home Premium/boot/grub/normal.mod
/media/Vista Home Premium/boot/grub/ntfs.mod
/media/Vista Home Premium/boot/grub/ntfscomp.mod
/media/Vista Home Premium/boot/grub/ohci.mod
/media/Vista Home Premium/boot/grub/part_acorn.mod
/media/Vista Home Premium/boot/grub/part_amiga.mod
/media/Vista Home Premium/boot/grub/part_apple.mod
/media/Vista Home Premium/boot/grub/part_gpt.mod
/media/Vista Home Premium/boot/grub/partmap.lst
/media/Vista Home Premium/boot/grub/part_msdos.mod
/media/Vista Home Premium/boot/grub/part_sun.mod
/media/Vista Home Premium/boot/grub/parttool.lst
/media/Vista Home Premium/boot/grub/parttool.mod
/media/Vista Home Premium/boot/grub/password.mod
/media/Vista Home Premium/boot/grub/password_pbkdf2.mod
/media/Vista Home Premium/boot/grub/pbkdf2.mod
/media/Vista Home Premium/boot/grub/pci.mod
/media/Vista Home Premium/boot/grub/play.mod
/media/Vista Home Premium/boot/grub/png.mod
/media/Vista Home Premium/boot/grub/probe.mod
/media/Vista Home Premium/boot/grub/pxe.mod
/media/Vista Home Premium/boot/grub/pxeboot.img
/media/Vista Home Premium/boot/grub/pxecmd.mod
/media/Vista Home Premium/boot/grub/raid.mod
/media/Vista Home Premium/boot/grub/raid5rec.mod
/media/Vista Home Premium/boot/grub/raid6rec.mod
/media/Vista Home Premium/boot/grub/read.mod
/media/Vista Home Premium/boot/grub/reboot.mod
/media/Vista Home Premium/boot/grub/reiserfs.mod
/media/Vista Home Premium/boot/grub/relocator.mod
/media/Vista Home Premium/boot/grub/scsi.mod
/media/Vista Home Premium/boot/grub/search.mod
/media/Vista Home Premium/boot/grub/search_fs_file.mod
/media/Vista Home Premium/boot/grub/search_fs_uuid.mod
/media/Vista Home Premium/boot/grub/search_label.mod
/media/Vista Home Premium/boot/grub/serial.mod
/media/Vista Home Premium/boot/grub/setjmp.mod
/media/Vista Home Premium/boot/grub/setpci.mod
/media/Vista Home Premium/boot/grub/sfs.mod
/media/Vista Home Premium/boot/grub/sh.mod
/media/Vista Home Premium/boot/grub/sleep.mod
/media/Vista Home Premium/boot/grub/tar.mod
/media/Vista Home Premium/boot/grub/terminal.lst
/media/Vista Home Premium/boot/grub/terminal.mod
/media/Vista Home Premium/boot/grub/terminfo.mod
/media/Vista Home Premium/boot/grub/test.mod
/media/Vista Home Premium/boot/grub/tga.mod
/media/Vista Home Premium/boot/grub/trig.mod
/media/Vista Home Premium/boot/grub/true.mod
/media/Vista Home Premium/boot/grub/udf.mod
/media/Vista Home Premium/boot/grub/ufs1.mod
/media/Vista Home Premium/boot/grub/ufs2.mod
/media/Vista Home Premium/boot/grub/uhci.mod
/media/Vista Home Premium/boot/grub/usb.mod
/media/Vista Home Premium/boot/grub/usb_keyboard.mod
/media/Vista Home Premium/boot/grub/usbms.mod
/media/Vista Home Premium/boot/grub/usbtest.mod
/media/Vista Home Premium/boot/grub/vbe.mod
/media/Vista Home Premium/boot/grub/vbeinfo.mod
/media/Vista Home Premium/boot/grub/vbetest.mod
/media/Vista Home Premium/boot/grub/vga.mod
/media/Vista Home Premium/boot/grub/vga_text.mod
/media/Vista Home Premium/boot/grub/video.lst
/media/Vista Home Premium/boot/grub/video.mod
/media/Vista Home Premium/boot/grub/video_fb.mod
/media/Vista Home Premium/boot/grub/videotest.mod
/media/Vista Home Premium/boot/grub/xfs.mod
/media/Vista Home Premium/boot/grub/xnu.mod
/media/Vista Home Premium/boot/grub/xnu_uuid.mod
/media/Vista Home Premium/boot/grub/zfs.mod
/media/Vista Home Premium/boot/grub/zfsinfo.mod

I wait for your response bro, thank you

---

### Post by oldfred on 2011-02-21
You want to delete the entire grub folder that has all those files.

Please use code tags for those kind of posts. Code tags are the # sign above your post as you enter it. Highlight what you want to put into code tags, click on # in edit panel & it auto adds code tags before & after highlighted text. You can add then in edit mode if you click on advanced at the bottom and then the edit mode gives you the full edit panel at the top.

---

### Post by F8M on 2011-02-22
When I deleted the entire grub folder and then went through the procedure 
to reinstall the Grub to fix broken system files, I rebooted without the CD and voila, the grub worked. But when I updated the grub to organize the drives in the proper order, the Vista/Ubuntu was still /dev/sdb1 and /dev/sdb2, whereas the unpartition drive(100GB) was still /dev/sda.
So after manually checking all three drives, only the Ubuntu drive had the boot/grub/boot.img file. 
Below is the result of the Boot Script

```
             Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   195,366,887   195,364,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   449,273,789   449,273,727   7 HPFS/NTFS
/dev/sdb2    *    449,273,790   613,104,659   163,830,870  83 Linux
/dev/sdb3         613,113,854   625,141,759    12,027,906   5 Extended
/dev/sdb5         613,113,856   625,141,759    12,027,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5842DB8842DB6970                       ntfs       100GB Drive                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2C2B79D13BA924A1                       ntfs       Vista Home Premium            
/dev/sdb2        0b54f8c5-9c78-4c95-8494-bb38cfacdf98   ext4       UbuntuLTS10.04                
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        b71c468a-fdb9-4bfa-9ce7-1368550ca01b   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/UbuntuLTS10.04    ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Vista Home Premium fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/100GB Drive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sdb2/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5842db8842db6970
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2c2b79d13ba924a1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b71c468a-fdb9-4bfa-9ce7-1368550ca01b none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 281.7GB: boot/grub/core.img
 283.6GB: boot/grub/grub.cfg
 283.8GB: boot/initrd.img-2.6.32-29-generic
 283.8GB: boot/vmlinuz-2.6.32-29-generic
 259.1GB: grub/core.img
 230.0GB: grub/grub.cfg
 283.8GB: initrd.img
 283.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ba 9b 5d 68 93 3c 9b 3c  c7 09 eb 91 22 39 d3 69  |..]h.<.<...."9.i|
00000010  53 88 bd 9f 01 c1 e9 38  6a 4a 8c 60 06 d8 60 0d  |S......8jJ.`..`.|
00000020  99 67 43 0c e9 b8 ce 36  ae bd ab af 1d 17 3b 8c  |.gC....6......;.|
00000030  1b 10 eb ba d1 38 a4 b6  97 e1 61 b9 b6 05 f1 4d  |.....8....a....M|
00000040  ec b7 93 4f 84 c8 e7 d8  b4 28 7b 83 d3 00 e9 b4  |...O.....({.....|
00000050  2f 82 80 1f 88 06 34 07  bd 9c 07 4d 3e bc 63 8e  |/.....4....M>.c.|
00000060  cf 1b 11 6c 7a 91 e7 bc  4c aa 41 29 41 29 88 51  |...lz...L.A)A).Q|
00000070  99 67 44 0c 09 b9 ff 17  77 7d fb f9 fd b8 a1 90  |.gD.....w}......|
00000080  23 5a 10 3e cf f1 a6 d6  d4 96 36 40 9b 6c 45 98  |#Z.>......6@.lE.|
00000090  16 3f e2 ef e4 1a e3 ce  92 01 22 a6 a2 4e f1 bd  |.?........"..N..|
000000a0  ce ad a9 7a 6c 00 96 67  84 2c 8e 0a 13 3b 11 32  |...zl..g.,...;.2|
000000b0  11 64 39 10 44 03 f2 b5  e6 a1 27 13 9b 35 a1 41  |.d9.D.....'..5.A|
000000c0  99 67 45 0c 90 36 41 79  2c 4e 30 4b b1 b9 82 71  |.gE..6Ay,N0K...q|
000000d0  07 81 90 36 45 34 82 43  b1 13 4b 63 3c e1 a7 80  |...6E4.C..Kc<...|
000000e0  90 36 da 21 60 a8 68 d0  22 96 72 ae 93 f0 90 36  |.6.!`.h.".r....6|
000000f0  92 30 07 e9 b1 51 45 21  f4 51 c1 07 00 36 49 85  |.0...QE!.Q...6I.|
00000100  c2 87 06 8b c3 42 00 36  0e c6 f6 00 00 00 00 00  |.....B.6........|
00000110  99 67 46 0c f8 af e7 8f  e5 f8 e4 f6 47 73 2f 33  |.gF.........Gs/3|
00000120  37 af df 25 9a ff 17 f5  37 7a d6 d6 93 aa 56 45  |7..%....7z....VE|
00000130  ff 2b fd ff 7f b9 d5 cf  d6 db 45 4b 73 5f f2 2f  |.+........EKs_./|
00000140  e4 4f e4 1d fb 3a b9 32  c2 63 66 51 1c bb 66 76  |.O...:.2.cfQ..fv|
00000150  2c 51 8e 86 5a 15 f0 b4  41 5c 47 0d 82 85 74 c0  |,Q..Z...A\G...t.|
00000160  99 67 47 0c ef af 5e c8  fa b1 e7 fa 11 db b4 ee  |.gG...^.........|
00000170  ce 81 fb 2f e3 1b d2 47  34 9f 57 42 0b 31 8d c4  |.../...G4.WB.1..|
00000180  09 2b fb 60 22 a5 99 d4  ea f3 61 b0 e7 1d 0e 2c  |.+.`".....a....,|
00000190  ff c6 7d f9 4d 24 27 50  00 14 0a 10 25 3d d3 52  |..}.M$'P....%=.R|
000001a0  b9 93 03 03 ac 28 e7 3b  03 c3 38 17 03 85 1c 71  |.....(.;..8....q|
000001b0  99 67 48 0c ec 20 1c 70  bc 9c 4e 2d 5a 50 00 fe  |.gH.. .p..N-ZP..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=======Devices which don't seem to have a corresponding hard drive==============
sdc 
```
Thank you.

---

### Post by oldfred on 2011-02-22
Grub does not organize drive order BIOS does. 

Usually you can change boot order of SATA drives, but that only changes boot order not normally sda, sdb etc. On my machine whatever I set boot order to, the first boot drive is hd0 in grub, but in Ubuntu the sda, sdb, sdc is the order plugged into the SATA ports on the motherboard.

With IDE drives, order is set by jumper on drive or location on cable with cable select drives. You have primary & secondary (two cables) and then master & slave( two connectors on each cable).

---

### Post by F8M on 2011-02-22
Thanks oldFred, switching the SATA cables did the trick. Now that my boot/grup issue is delt with, I could work on my other minor problems.
And that is with my compiz, which I will look at tomorrow.
A big thank you, --- CLAUDE

---

### Post by oldfred on 2011-02-22
If you changed drive order, you may want to do this to make sure menu has correct entry. Grub still finds correct partition with UUIDs, so it is not vital.

sudo update-grub

Windows may have issues also. Not as familiar with win7 as XP. If any issues then you may have to use BCDedit to check or EasyBCD from neosmart.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---


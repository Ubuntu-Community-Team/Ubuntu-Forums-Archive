---
title: "Lost my grub menu at start up"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by latestarter on 2010-01-24
Just upgraded to 9.10 on a laptop with dead Vista which I lost when I moved over to UBUNTU some time ago. Never any problems but when fiddling at boot up tonight I accidentally selected to boot up the Vista loader which went into the Vista recovery, and since then the laptop only opens up the Vista Recovery, ie it does not go to the Grub. Any ideas on how I can get to boot UBUNTU again?

---

### Post by presence1960 on 2010-01-24
I need more info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by latestarter on 2010-01-25
Thanks for picking this up, hope I have got your instructions right.

```
#!/bin/bash
#to use this script:
#
#     sudo bash boot_info_script048.sh
#or
#     su -
#     bash boot_info_script_048.sh
#
#version 0.48
#
#date 1/12/10
#
#author  Ulrich Meierfankenfeld (aka meierfra.) 
# with  contributions from caljohnsmith
# (both members of ubuntuforums.org)
# and Gert Hulselmans
#
#hosted at: http://sourceforge.net/projects/bootinfoscript/
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
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script. But  when run from /bin, /sbin, /usr/bin,
#    or  other system folder the file "RESULTS.txt" is written to the
#    home directory of the user who runs this script.


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
     /ubuntu/disks/root.disk
     /ubuntu/disks/
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU /default.mnu
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
     /ubuntu/disks/root.disk
     /ubuntu/disks/
     /ubuntu/disks/swap.disk
     /core.img   /grub/core.img     /boot/grub/core.img
     /boot/map      /map
     /DEFAULT.MNU 
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
#exec 6>&1   
#exec > "$LogFile"

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

####Arrays to hold information about Partitions: name, starting sector, ending sector, size in sector, Partition Type, Filesystem typ, UUID, Kind(Logical, Primary, Extended), HardDrive, boot flag,  parent (for logical partitions), label, system(the partition id according the partition table), the device associate to the partition.

declare -a NamesArray StartArray EndArray SizeArray TypeArray  FileArray UUIDArray KindArray DriveArray BootArray ParentArray LabelArray SystemArray DeviceArray  


#####Arrays to hold information about the harddrives.
declare -a HDName  FirstPartion LastPartition  HDSize HDMBR HDHead HDTrack HDCylinder HDPT HDStart HDEnd HDUUID;



PI=-1 ## Counter for the identification number of a partition. (each partition gets unique number)
HI=0 ## Counter for the identification number of a hard drive. (each hard drive gets unique number)
PTFormat='%-10s %4s%14s%14s%14s %3s %s\n';  ### standard format to use for Partition table,
           


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
local BST=""  BSI=""  BFI=""  OS="" BootFiles="";


       echo "Searching $name for information... ";
       blkid -c /dev/null $part 2>$Tmp_Log  >>$BLKID; # | sed  "s;.*:;$name:;"
       type=$(blkid -c /dev/null -s TYPE $part 2>>$Trash);  ##### type of file system according to blkid
       type=${type#*=\"};
       type=${type%\"*};
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
         [[ "$CheckMount" != "" ]]  &&  mountname=$CheckMount;  #### if yes,use existing mount point.
         if  [ "$CheckMount" != "" ] || mount -r  -t "$type" $part "$mountname" 2>>$Mount_Error  || ( [ "$type" = ntfs ] && ntfs-3g -o ro  $part "$mountname" 2>>$Mount_Error  ) ;     ####### Try to mount partition
         then     ############  if partition is  mounted.
         #####Try to identify the Operating  System (OS) by  looking for files specific to the OS
       OS=""

        grep -q "W.i.n.d.o.w.s. .V.i.s.t.a"  $mountname/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows Vista";

       grep -q "W.i.n.d.o.w.s. .7" $mountname/{windows,Windows,WINDOWS}/{System32,system32}/{Winload,winload}.exe 2>>$Trash && OS="Windows 7";

       [ -e "$mountname/Windows/System32/config/SecEvent.Evt" ] ||  [ -e "$mountname/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e "$mountname/WINDOWS/system32/config/secevent.evt" ] || [ -e "$mountname/windows/system32/config/secevent.evt" ] && OS="Windows XP";

       [ -e "$mountname/etc/issue" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/issue);

        [ -e "$mountname/etc/slackware-version" ] && OS=$(sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' "$mountname"/etc/slackware-version);


 ####################################  search for  the files in $Bootfiles   ########################
###################################### and if found, display there contained ########################
       BootFiles="" 
       if [ "$type" = "vfat" ];
       then
           Boot_Files=$Boot_Files_Fat;
       else
           Boot_Files=$Boot_Files_Normal;  
       fi;
       
       for file in $Boot_Files;
       do
           if [ -f "$mountname"$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
              if ! [ -h "$mountname"$file ];  ### check whether file is  symlink
              then
                 titlebar_gen "$name" $file;	##generates a titlebar above each file/dir listed
                 cat "$mountname"$file >> "$Log1";  ### if not a symlink, display content.
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
          [[ $WubiDev = 0 ]] && losetup -d "$Wubi";  #delete Wubu loop device, if created by B_I_S.
          else 
             echo "Found Wubi on $name. But could not create a loop device">>$Error_Log;
          fi;      
        fi;            
                    
                      
             
#################################### Search for the programs in $Boot_Prog, ###############
################################### if found disply where names.           ###############
        if [ "$type" = "vfat" ];
       then
           Boot_Prog=$Boot_Prog_Fat;
       else
           Boot_Prog=$Boot_Prog_Normal;  
       fi;

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
#	      BootFiles=$(echo $BootFiles"  "$file); 
#              titlebar_gen "$name" $file	##generates a titlebar above each file/dir listed
#              ls -la  "$mountname"$file >> "$Log1" ; 
#             
#	  fi;
#       done;

####################  Search for files containing boot codes #################################

       for file in $Boot_Codes_Dir    #####  loop through all directories which might contain boot_code files
       do
	   if [ -d "$mountname"$file ];   ##### if such directory exist
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



echo '============================= Boot Info Summary: =============================='>>"$Log"; 
echo>>"$Log";

#####   Search  for  hard drives which don't exist   or have a  corrupted partition table.
#####  Information on all  hard drives which a valid partition table are stored in the 
#####  Hard drives arrays: HD?????
for drive in  $All_Hard_Drives;
do
        size=$(fdisk -s $drive 2>>$Trash);        
        if [ 0 -lt $size 2>>$Trash ];
	then
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
    done
    echo;
######################################################################################
#############   Store and Display all the partitions tables.##########################
for HI in ${!HDName[@]};
    do
    drive=${HDName[$HI]};
    echo "Computing Partition Table of $drive...";
    FP=$((PI+1)); #used of non-DOD partition table is not in use.
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
              [[ "${HDMBR[$HI]}" = "BootIt NG" ]] && echo . >>$PartitionTable || echo ,but does not seem to be used. >>$PartitionTable;
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


##################### Search LVM partitions for information.             #########
##################### only works if the "LVM2"-package is installed     #########
if type lvscan >>$Trash 2>&1 && type lvdisplay >>$Trash 2>&1 && type lvchange >>$Trash 2>&1;

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
if type mdadm >>$Trash 2>&1;
then
    MD_Active_Array=$(mdadm --detail --scan |awk '{print $2}');
                   ## all arrays which are already assembled
    mdadm --assemble  --scan  #assemble all arrays
    MD_Array=$(mdadm --detail --scan|awk '{print $2}');
                    ## all arrays.
    for MD in $MD_Array;
    do
        MD_Size=$(sfdisk -s $MD); #size in blocks
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
  

###############################################################################################

echo '=========================== Drive/Partition Info: ============================='>>"$Log";
echo>>"$Log";
 
[ -e $PartitionTable ] && cat $PartitionTable>>"$Log" || echo no valid partition table found>>"$Log";


echo "blkid -c /dev/null: ____________________________________________________________">>"$Log";
echo>>"$Log";
blkid -c /dev/null >>$BLKID;
sort -u $BLKID>>"$Log";
echo>>"$Log";

if [ $(ls -R /dev/mapper | wc -l) -gt 2 ]
then

  echo '=============================== "ls -R /dev/mapper/" output: ==============================='>>"$Log";
   ls -R /dev/mapper>>$Log
  echo>>"$Log";
fi;
         



echo '=============================== "mount" output: ==============================='>>"$Log";
echo>>"$Log";
mount>>"$Log";
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

### Post by presence1960 on 2010-01-25
No not correct. 

1. Boot the Live Cd and choose try ubuntu without any changes. Open firefox & come back here.

2. Download the boot info script from the link in my signature.

3. Once downloaded make sure the file is on desktop.

4. Then run that command in terminal

5. Open RESULTS.txt file on desktop which was generated by the script. Copy/paste the contents of that file back here.

---

### Post by latestarter on 2010-01-25
Hope this is right this time, thanks for your patience!

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c62b218

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     2,907,764     2,907,702   7 HPFS/NTFS
/dev/sda2    *    294,146,048   300,478,079     6,332,032   7 HPFS/NTFS
/dev/sda3         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS
/dev/sda4           2,907,765   294,134,084   291,226,320   5 Extended
/dev/sda5           2,907,828   207,704,384   204,796,557  83 Linux
/dev/sda6         282,229,983   294,134,084    11,904,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6422abcc-4d9c-413c-a1d9-cdb54ac69812" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="2012FB0812FAE1A8" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="9CCC8FE8CC8FBB52" LABEL="OS_TOOLS" TYPE="ntfs" 
/dev/sda5: UUID="57901173-89fe-4159-9be7-88afbeaf813f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="fa1bcea3-f0ff-42bd-a238-481b4f909bd5" TYPE="swap" 

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


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.28-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.10, kernel 2.6.27-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=57901173-89fe-4159-9be7-88afbeaf813f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=57901173-89fe-4159-9be7-88afbeaf813f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fa1bcea3-f0ff-42bd-a238-481b4f909bd5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   1.4GB: boot/grub/menu.lst
   1.4GB: boot/grub/stage2
   1.4GB: boot/initrd.img-2.6.27-14-generic
   1.4GB: boot/initrd.img-2.6.28-17-generic
   1.4GB: boot/initrd.img-2.6.31-17-generic
   1.4GB: boot/vmlinuz-2.6.27-14-generic
   1.4GB: boot/vmlinuz-2.6.28-17-generic
   1.4GB: boot/vmlinuz-2.6.31-17-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
   1.4GB: vmlinuz
   1.4GB: vmlinuz.old
```

---

### Post by presence1960 on 2010-01-25
OK I see you got to 9.10 via dist-upgrade. You still have Legacy GRUB 0.97. You will need a 9.04  or earlier Live CD. Boot the Live CD & choose "try ubuntu without any changes". When the desktop loads do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

### Post by latestarter on 2010-01-25
Started up a version of 9.04 but it did not have a live session option only a 'recovery' option. had a copy of 8.10 so loaded this. However I am getting an error 15: File not found.

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stagel
find /boot/grub/stagel

Error 15: File not found
grub> ^C
ubuntu@ubuntu:~$

---

### Post by Leppie on 2010-01-25
> **latestarter said:**
> 
```
find /boot/grub/stage[COLOR=YellowGreen]l[/COLOR]

Error 15: File not found
grub> ^C
```
that's a 1 (number 1, like 1 chicken), not a lower case "L"...
```
find /boot/grub/stage[COLOR=Red]1[/COLOR]  ##the difference between [COLOR=Red]1[/COLOR] and [COLOR=YellowGreen]l[/COLOR]
```

---

### Post by latestarter on 2010-01-25
Hi presence1960
Thank you very much for your help and long suffering. Exactly as you said the boot grub is back. Thanks again.

---

### Post by presence1960 on 2010-01-25
Glad you got it working! Thank leppie too. Enjoy.

---

### Post by jripple on 2010-01-25
Seem to be having the same problem.  Recently installed karmic (not an upgrade), was trying to install some software and crashed.  Upon reboot, have access only to tty.

Attached is RESULTS.txt

Have followed instructions but [INDENT]find /boot/grub/stage1
[/INDENT]resulted in:[INDENT]Error 15: File not found
[/INDENT]I didn't make the error corrected by leppie

Thanks,
jripple

---

### Post by Leppie on 2010-01-25
the instructions posted by presence1960 are for grub legacy and not grub2 which is used in karmic clean installs.
boot off the livecd, then issue these commands:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --recheck /dev/sda
```

then reboot to see if it's working.

---

### Post by jripple on 2010-01-25
Appreciate your quick reply.

Had to install grub but that seemed to go OK.

I cut and pasted your instructions to avoid error, got this result:
------
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
------
Sorry to be so clueless . . .

Don't know if this is relevant but I have ubuntu set up for dual boot with WinXP.

Suggestions?

Thanks

---

### Post by Leppie on 2010-01-25
then try this:
```
sudo -i
sudo mkdir /mnt/temp
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
exit
```i suspect that not all files were installed properly during installation.

---

### Post by jripple on 2010-01-25
>>i suspect that not all files were installed properly during installation.

Probably so.

Your last batch of commands seemed to go fine until:
[INDENT]root@ubuntu:~# apt-get install purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package purge
root@ubuntu:~#

[/INDENT]

---

### Post by presence1960 on 2010-01-25
> **jripple said:**
> >>i suspect that not all files were installed properly during installation.

Probably so.

Your last batch of commands seemed to go fine until:
[INDENT]root@ubuntu:~# apt-get install purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package purge
root@ubuntu:~#

[/INDENT]

remove "install" from that command. You can't install & purge the same package

---

### Post by Leppie on 2010-01-25
> **presence1960 said:**
> remove "install" from that command. You can't install & purge the same package
yeah, sorry about that... am thinking with my fingers lately...

---

### Post by jripple on 2010-01-26
> sudo -i
sudo mkdir /mnt/temp
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
exitExecuted the above but upon reboot still boot to tty1.

Still open to suggestions.
Thanks

---

### Post by Leppie on 2010-01-26
> **jripple said:**
> Executed the above but upon reboot still boot to tty1.

Still open to suggestions.
Thanks
so you don't have grub issues?
it's just that boot takes you the cli?
at the cli, issue the startx command to launch an x session.

---

### Post by jripple on 2010-01-26
> at the cli, issue the startx command to launch an x session.Did that and got this:

-----
The XKEYBOARD Keymap compiler (xkbcomp) reports:
>Warning:     Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                  Ignoring extra symbols

Errors from xkbcomp are not fatal to the X server

Waiting for X server to shut down ddxSigGiveUp: Closing log
prompt . . .
-----

In case this is relevant: I was set up for the USA/Dvorak keyboard layout and had installed the NVIDIA v185 drivers before all this happened.

Please let me know at what point reinstalling ubuntu is the best option.

Thanks again

---

### Post by Leppie on 2010-01-26
> **jripple said:**
> Errors from xkbcomp are not fatal to the X server
as the message says, the keyboard layout does not prevent x from starting.

> **jripple said:**
> In case this is relevant: I was set up for the USA/Dvorak keyboard layout and had installed the NVIDIA v185 drivers before all this happened.
run nvidia-xconfig again, this most probably is some video card issue...

---


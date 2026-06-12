---
title: "Preseed with LVM and keep other distros"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by esdi on 2010-02-19
Hi, 

I am trying to preseed a ubuntu 9.10 installation allong side existing Windows7 and other linux distros under lvm (Fedora and Gentoo).
All existing distros use a common /boot partition.
I use the hd-media install method on a usb disk for amd64


So I started with the sample preseed file found here
[https://help.ubuntu.com/9.10/installation-guide/example-preseed.txt](https://help.ubuntu.com/9.10/installation-guide/example-preseed.txt)
got everything working up to the Partitioning section

I can't figure out how to use an existing /boot partition and install / in a new lvm logical volume without loosing my existing data.



here is my production setup

```
# fdisk -l /dev/sda

``````
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x172efea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9139    73401312+   7  HPFS/NTFS
/dev/sda2   *        9139        9400     2097152   83  Linux
/dev/sda3            9400       60801   412885536+  8e  Linux LVM

```/dev/sda1 (Win7 ntfs)
/dev/sda2 (/boot ext4)
/dev/sda3 (lvm with volume group "LinuxVG" and plenty of free space in the VG)

Logical volumes are
```
ls -l /dev/LinuxVG/

``````
lrwxrwxrwx. 1 root root 27 2010-02-19 18:46 Fed12LV -> /dev/mapper/LinuxVG-Fed12LV
lrwxrwxrwx. 1 root root 36 2010-02-19 18:46 GenStableKDE01LV -> /dev/mapper/LinuxVG-GenStableKDE01LV
lrwxrwxrwx. 1 root root 29 2010-02-19 18:46 LinSwapLV -> /dev/mapper/LinuxVG-LinSwapLV

```
I created an VM environment representing this and tried this
(lvm names are all prefixed with "VM" to avoid conflicts with the production config)



```
# partition
# Remove the hd-media warning of mounted partitions for my /dev/sdb usb disk.
d-i partman/filter_mounted boolean false
d-i partman/unmount_active boolean false

# Select partitionning method
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm

#If the folowing section is uncommented, the some new LVs are created and associated to mountpoints 
#but the LVs are not what is specified in the recipe below
#d-i partman-auto-lvm/new_vg_name string VMLinuxVG
#d-i partman-lvm/vgcreate string VMLinuxVG
#d-i partman-lvm/device_remove_lvm boolean true
#d-i partman-lvm/confirm boolean true
#When the above is commented, I get asked to erase the phisical volume 
# answering no ignores the folowing recipe and mountpoints are not mapped to partitions
d-i partman-auto/expert_recipe string boot-root ::         \
    2048 2048 2048 ext4                                    \
    $primary{ } $bootable{ }                               \
    method{ format } format{ }                             \
    $lvmignore{_}                                          \
    use_filesystem{ } filesystem{ ext4 }                   \
    mountpoint{ /boot } .                                  \
                                                           \
    2048 2048 2048 swap                                    \
    $lvmok{ } in_vg{ VMLinuxVG } lv_name{ VMLinSwapLV }    \
    $defaultignore{_}                                      \
    method{ swap } format{ } .                             \
                                                           \
    10240 10240 10240 ext4                                 \
    $lvmok{ } in_vg{ VMLinuxVG } lv_name{ VMKarmicLV }     \
    $defaultignore{_}                                      \
    method{ format } format{ }                             \
    use_filesystem{ } filesystem{ ext4 }                   \
    mountpoint{ / } .                                      

```Anybody know what I am doing wrong and help me create or reformat a LV named VMKarmicLV in the existing LinuxVG while sharing /dev/sda2 (/boot) with other distros.

I know the installer can do it because I did it manually
Can this scenario be preseeded?

Thanks

---

### Post by esdi on 2010-04-02
I finally got this working thanks to the information I found in this thread
[http://www.mail-archive.com/debian-boot@lists.debian.org/msg89027.html](http://www.mail-archive.com/debian-boot@lists.debian.org/msg89027.html)

I ended up creating a custom udeb that did the partitioning the way I wanted
It also deactivates partman and builds the /target/fstab and mounts partitions in /target so the installation can continue without user intervention


First you need these 3 files in a folder (SOURCE_FOLDER in the script)

**POTFILES.in**
```

[type: gettext/rfc822deb] custom-partition.templates

```**custom-partition.templates **
```

Template: debian-installer/custom-partition/title
Type: text
#  Main menu item
_Description: Perform My Custom Partitioning

```**partition.sh **
```

#!/bin/sh --
set -e

COMMANDS=`cat /hd-media/custom-partition.txt`


createlv ()
{
   VG_Name="$1"
   LV_Name="$2"
   size="$3"
   if echo "$VG_Name" | grep '[^0-9a-zA-Z_-]'>/dev/null; then
      logger custom-partition error "volume group name must be alpha-numeric. Not $VG_Name."
      exit 1
   elif ! vgdisplay $VG_Name | grep UUID >/dev/null; then
      logger custom-partition error "$VG_Name appears not to be a volume group."
      exit 1
   elif echo "$LV_Name" | grep '[^0-9a-zA-Z_-]'>/dev/null; then
      logger custom-partition error "logical volume name must be alpha-numeric. Not $LV_Name."
      exit 1
   elif echo "$size" | egrep -v '^[0-9][0-9]*([Tt]|[Gg]|[Mm]|[Kk]|)[Bb]?$' >/dev/null; then
      logger custom-partition error "$size is an invalid size (try a number followed by a size unit)."
      exit 1
   else
      if lvdisplay /dev/mapper/$VG_Name-$LV_Name | grep UUID >/dev/null; then
         # remove the existing LV
         log-output -t custom-partition lvremove -f /dev/mapper/$VG_Name-$LV_Name
      fi
      log-output -t custom-partition lvcreate $VG_Name --name $LV_Name --size $size
   fi
}

filesystem ()
{
   type="$1"
   device="$2"
   fstype="$3"
   mountpoint="$4"
   format="$5"
   if [[ "lvm" == "$type" ]]; then
      # make sure the logical volume is active
      log-output -t custom-partition lvchange --available y $device
   fi

   if ! [ -b $device ]; then
      logger custom-partition error "$device is not a special block device, refusing to mkfs it"
      exit 1
   fi

   # handle swap
   if [[ "swap" == "$fstype" ]]; then
      log-output -t custom-partition mkswap $device
      log-output -t custom-partition swapon $device
      echo $device none swap sw 0 0 >> /tmp/fstab
   else

      # format the partition 
      if [[ "format" == "$format" ]]; then
         log-output -t custom-partition mkfs.$fstype $device
      fi

      # set mountpoint
      if [[ "/" == "$mountpoint" ]]; then
         log-output -t custom-partition mkdir -p /target
         log-output -t custom-partition mount -t $fstype $device /target
         echo $device $mountpoint $fstype defaults 0 1 >> /tmp/fstab
      else
         if echo $mountpoint | grep '^[^/]' >/dev/null; then
            logger custom-partition error "Mountpoint must start with a / (not: $mountpoint)"
            exit 1
         fi
         log-output -t custom-partition mkdir -p /target$mountpoint
         log-output -t custom-partition mount -t $fstype $device /target$mountpoint

         if [[ "lvm" == "$type" ]]; then
            echo $device $mountpoint $fstype defaults 0 2 >> /tmp/fstab
         else
            UUID=`blkid -o value -s UUID $device`
            echo "# UUID $UUID is device $device" >> /tmp/fstab
            echo UUID=$UUID $mountpoint $fstype defaults 0 2 >> /tmp/fstab
         fi
      fi
   fi
}


# Create fstab stub
cat > /tmp/fstab <<EOF
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
EOF

# read commands in order
echo "$COMMANDS" | while read command params; do

   case $command in
      ""|\#*)
         continue
         ;;
      "lv")
         createlv $params
         ;;
      "fs")
         filesystem $params
         ;;
      *)
         logger custom-partition error "Unknown command $command in config. Aborting"
         exit 1
         ;;
   esac
done

## fstab
log-output -t custom-partition mkdir -p /target/etc/
log-output -t custom-partition cp /tmp/fstab /target/etc/fstab

#deactivate partman
#comment to be allow partman tu run (usefull for debugging)
sed -i -e 's/partman/#partman/' /var/lib/dpkg/info/partman-base.postinst


```Then you need to create the udeb
Here is the script I used


```

#!/bin/sh


# tools needed
#apt-get install autotools-dev fakeroot dh-make build-essential

# documentation for the installer is found here
#http://d-i.alioth.debian.org/doc/internals/


# run this script as a normal user
# intended to run on karmic. I guess newer versions of dh_make will generate different files so ajust this script accordingly

SOURCE_FOLDER="/media/Gemeni_nas/shared/ToBackup/Projects/Reinstall/Ubuntu_910/custom-partition-files"
TEMP_FOLDER="/media/Gemeni_nas/shared/ToBackup/Projects/Reinstall/Ubuntu_910/custom-partition-files/tempfiles"
UDEB_NAME="custom-partition"
UDEB_VERSION="1"

DEBIAN_FOLDER=$TEMP_FOLDER/$UDEB_NAME-$UDEB_VERSION/debian
CONTROL_FILE=$DEBIAN_FOLDER/control
RULES_FILE=$DEBIAN_FOLDER/rules


# Cleanup and build the files needed to compile
rm -rf $TEMP_FOLDER
mkdir $TEMP_FOLDER
cd $TEMP_FOLDER
mkdir $TEMP_FOLDER/$UDEB_NAME-$UDEB_VERSION

CURRENT_FOLDER=`pwd`
cd   $UDEB_NAME-$UDEB_VERSION
dh_make --single --indep --native


###### modify the control file ############
# Change the section to debian-installer
sed -i -e 's/Section: unknown/Section: debian-installer/' $CONTROL_FILE
# add udeb type to control file
sed -i -e '/Package: '$UDEB_NAME'/a\XC-Package-Type: udeb' $CONTROL_FILE
# change descriptions
sed -i -e 's/<insert up to 60 chars description>/Custom partition udeb/' $CONTROL_FILE
sed -i -e 's/<insert long description, indented with spaces>/Custom partition udeb that aplies a list of commands from a file in the order tahat one would do in manual partitioning/' $CONTROL_FILE
# Change dependency
sed -i -e 's/Depends: ${misc:Depends}/Depends: ${misc:Depends}, cdebconf-udeb, di-utils (>= 1.66)/' $CONTROL_FILE
# add the menuitem number
# menuitem numbers are documented here
# http://d-i.alioth.debian.org/doc/internals/apa.html
sed -i -e '/Depends: ${misc:Depends}/a\XB-Installer-Menu-Item: 4100' $CONTROL_FILE




###### modify the rules file ############
# add clean commands
sed -i -e '/Add here commands to clean up after the build process./a\\trm -f debian/'$UDEB_NAME'.postinst' $RULES_FILE
# add install commands
sed -i -e '/Add here commands to install the package into debian\/'$UDEB_NAME'./a\\tinstall -m755 partition.sh debian/'$UDEB_NAME'.postinst' $RULES_FILE
# deactivate all make commands
sed -i -e 's/$(MAKE)/#$(MAKE)/' $RULES_FILE


# Activate bluid items
sed -i -e 's/#\tdh_installdebconf/\tdh_installdebconf/' $RULES_FILE
sed -i -e 's/#\tdh_install/\tdh_install/' $RULES_FILE

# remove unnecessary build commands
sed -i -e '/dh_installchangelogs/d' $RULES_FILE
sed -i -e '/dh_installdocs/d' $RULES_FILE
sed -i -e '/dh_installexamples/d' $RULES_FILE
sed -i -e '/dh_installman/d' $RULES_FILE
sed -i -e '/dh_link/d' $RULES_FILE
sed -i -e '/dh_strip/d' $RULES_FILE
sed -i -e '/dh_compress/d' $RULES_FILE
sed -i -e '/dh_md5sums/d' $RULES_FILE
sed -i -e '/dh_installlogrotate/d' $RULES_FILE
sed -i -e '/dh_installemacsen/d' $RULES_FILE
sed -i -e '/dh_installpam/d' $RULES_FILE
sed -i -e '/dh_installmime/d' $RULES_FILE
sed -i -e '/dh_installinit/d' $RULES_FILE
sed -i -e '/dh_installcron/d' $RULES_FILE
sed -i -e '/dh_installinfo/d' $RULES_FILE
sed -i -e '/dh_installwm/d' $RULES_FILE
sed -i -e '/dh_installudev/d' $RULES_FILE
sed -i -e '/dh_lintian/d' $RULES_FILE
sed -i -e '/dh_undocumented/d' $RULES_FILE
sed -i -e '/dh_perl/d' $RULES_FILE
sed -i -e '/dh_python/d' $RULES_FILE
sed -i -e '/dh_installmenu/d' $RULES_FILE


# remove extra files
rm $DEBIAN_FOLDER/dirs
rm $DEBIAN_FOLDER/manpage.1.ex
rm $DEBIAN_FOLDER/prerm.ex
rm $DEBIAN_FOLDER/preinst.ex
rm $DEBIAN_FOLDER/postrm.ex
rm $DEBIAN_FOLDER/postinst.ex
rm $DEBIAN_FOLDER/init.d.lsb.ex
rm $DEBIAN_FOLDER/init.d.ex
rm $DEBIAN_FOLDER/emacsen-remove.ex
rm $DEBIAN_FOLDER/emacsen-install.ex
rm $DEBIAN_FOLDER/watch.ex
rm $DEBIAN_FOLDER/menu.ex
rm $DEBIAN_FOLDER/manpage.sgml.ex
rm $DEBIAN_FOLDER/emacsen-startup.ex
rm $DEBIAN_FOLDER/manpage.xml.ex
rm $DEBIAN_FOLDER/$UDEB_NAME.doc-base.EX
rm $DEBIAN_FOLDER/$UDEB_NAME.default.ex
rm $DEBIAN_FOLDER/cron.d.ex
rm $DEBIAN_FOLDER/README.Debian
rm $DEBIAN_FOLDER/README
rm $DEBIAN_FOLDER/docs


# copy my files
cp $SOURCE_FOLDER/partition.sh .
cp $SOURCE_FOLDER/$UDEB_NAME.templates $DEBIAN_FOLDER/.


# Create the translation files necesary for the menu to display something
mkdir $DEBIAN_FOLDER/po
cp $SOURCE_FOLDER/POTFILES.in $DEBIAN_FOLDER/po/.
debconf-updatepo

dpkg-buildpackage -rfakeroot -uc -us


cd $CURRENT_FOLDER



```the resulting **debian/control** file looks like this
```

Source: custom-partition
Section: debian-installer
Priority: extra
Maintainer: Sylvain Dansereau <sylvain@unknown>
Build-Depends: debhelper (>= 7)
Standards-Version: 3.8.1
Homepage: <insert the upstream URL, if relevant>

Package: custom-partition
XC-Package-Type: udeb
Architecture: all
Depends: ${misc:Depends}, cdebconf-udeb, di-utils (>= 1.66)
XB-Installer-Menu-Item: 4100
Description: Custom partition udeb
 Custom partition udeb that aplies a list of commands from a file in the order tahat one would do in manual partitioning

```and the **debian/rules** file like this
```

#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1





configure: configure-stamp
configure-stamp:
    dh_testdir
    # Add here commands to configure the package.

    touch configure-stamp


build: build-stamp

build-stamp: configure-stamp  
    dh_testdir

    # Add here commands to compile the package.
    #$(MAKE)
    #docbook-to-man debian/custom-partition.sgml > custom-partition.1

    touch $@

clean: 
    dh_testdir
    dh_testroot
    rm -f build-stamp configure-stamp

    # Add here commands to clean up after the build process.
    rm -f debian/custom-partition.postinst
    #$(MAKE) clean

    dh_clean 

install: build
    dh_testdir
    dh_testroot
    dh_prep  
    dh_installdirs

    # Add here commands to install the package into debian/custom-partition.
    install -m755 partition.sh debian/custom-partition.postinst
    #$(MAKE) DESTDIR=$(CURDIR)/debian/custom-partition install


# Build architecture-independent files here.
binary-indep: install
    dh_testdir
    dh_testroot
    dh_install
    dh_installdebconf
    dh_fixperms
    dh_installdeb
    dh_gencontrol
    dh_builddeb

# Build architecture-dependent files here.
binary-arch: install

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure

```I then copy the iso, the udeb, my preseed file and a partitionning file to the / of the usb media and boot the installation 

The preseed file installs the udeb as follows
```


# custom partitioning replacing partman
d-i preseed/early_command string cp /hd-media/custom-partition_1_all.udeb /tmp/custom-partition_1_all.udeb ; udpkg --unpack /tmp/custom-partition_1_all.udeb


```The partitioning file is named custom-partition.txt
Each command will be read and executed in the same order it apears in the file.
I can specify the logical volumes that I want added to my system, the mountpoints I want for the installation and if they should be formatted or not

It contains
```


# lvm
# lv <vg_name> <lv_name> <size>
lv VMLinuxVG VMUbu910LV 3G

# filesystems & mounts & format
# fs <type> <device> <fstype> <mountpoint> <method>
fs lvm /dev/mapper/VMLinuxVG-VMLinSwapLV swap swap format
fs lvm /dev/mapper/VMLinuxVG-VMUbu910LV ext4 / format
fs disk /dev/sda2 ext4 /boot keep


```The disk partitions never change on my system, only Locigal volumes are added and removed as i install new distros. I use the same swap and boot partitions for all of them.
This partitioning file seems easier for me to maintain than a recipe file needed by partman as I never know what logical volumes exists on my system when I decide to reinstall one of my scripted installations.


Hope this helps someone as much as the Matthew Johnson post helped me

---


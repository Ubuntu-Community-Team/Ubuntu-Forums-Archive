---
title: "Creating a MultiBoot Live CD / DVD"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by pbotros1234 on 2008-09-12
I have been trying to make a live CD or DVD that has a GRUB and can boot in to one of the multiple distros on the CD. After searching a lot over the internet, I could not find any tutorials or much help on this. My main goal is to eventually make a Live DVD that will boot Ubuntu, KUbuntu, XUbuntu, GParted Live, Puppy, Backtrack, and eventually (doubt it though) a WinXP install.

So far, I have just been trying one distro at a time, making it an iso with a boot-table, and then using qemu to try it out. As of now my folders look this:
```
~/MultiBootDisc
    /BOOT
        /isolinux
            /isolinux config stuff (isolinux.bin, .cfg, etc)
    /xubuntu
        /the entire xubuntu livecd
```


So, all I'm pretty much doing is seeing if you can boot a ubuntu distro from its own folder instead of having it in the cdrom root.

My isolinux is configured to boot from /xubuntu/casper/vmlinuz, and the initrd is /xubuntu/casper/initrd.gz. Everything boots up fine, and vmlinuz and initrd.gz are good. But the startup crashes when it starts the scripts. As soon as the init process starts and the scripts begin, this is what happens:
```
Begin: Running /scripts/init-premount
Done.
Begin: Mounting root file system... ...
/init: .: 159: Can't open /scripts//xubuntu/casper
[   19.514473] Kernel panic - not syncing: Attempted to kill init!
```
And then it stops booting.

Any ideas how to fix this, or just on a MultiBoot LiveDVD in general? Do I have to go in and manually edit the initrd.gz and change all the references to /casper to /xubuntu/casper? Maybe a QEMU problem?

:confused: Thanks

---

### Post by pbotros1234 on 2008-09-12
Anyone?

---

### Post by Keen101 on 2008-09-13
try looking into this:

[http://linux.wareseeker.com/System/gparted-clonezilla-2.0.zip/334923](http://linux.wareseeker.com/System/gparted-clonezilla-2.0.zip/334923)

seems to be a multi-boot cd running off grub. Maybe you can figure out how it works.

I am also looking to create a multiboot cd. I want a super grub disk/gparted live-cd.

---

### Post by Keen101 on 2008-09-13
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted)

---

### Post by ddbekesi on 2009-02-19
Hi, I've done (in fact I am doing right now) a multiboot DVD. Untill now I have successfully integrated:
Damn Small Linux
Fedora
SLAX
Ubuntu
Zenlive

I have the following directory structure:

/boot
           /isolinux (inside I have isolinux.cfg, vesamenu.c32 and a kernel - forgot it 
[INDENT][/INDENT]there and later i didn't bother to move it and a isolinux.bin file)
           /dsl     -inside I've put linux24 and minirt24.gz files from the /boot [INDENT][/INDENT]directory of Damn Small Linux iso 
           /fedora  - vmlinuz0 and initrd0 from the isolinux directory of the fedora iso 
           /slax - vmlinuz and initrd.gz from the boot directory of slax iso
           /zenlive - vmlinuz and initrd.gz from the boot directory of zenwalk live iso
/fedora - there are the following files: livecd-iso-to-disk, osmin.img and squashfs.img from LiveOS directory of fedora iso
/dsl -  file KNOPPIX from Knoppix directory of damn small iso
/slax - the content copied entirelly from the slax directory from slax iso
/ubuntu
             /.disk the directory copied with its contents from the root dir of the ubuntu iso
             /casper directory copied with all its contents from the root of the ubuntu iso
/zenlive directory copied with its contents from the zenlive dir of the zenwalk iso

Then, the isolinux.cfg from the /boot/isolinux directory looks like this

DEFAULT /boot/isolinux/vesamenu.c32
PROMPT 0
TIMEOUT 300
TOTALTIMEOUT 450
####
MENU BACKGROUND /boot/isolinux/splash.png
MENU TITLE Super-Disc  **  09Mar07 Edition
####
####  The 1st byte of the fgnd color is brightness.
####                                    blue
MENU COLOR title        1;36;44    #ff0000ff   #00000000   std
####                                    blue
MENU COLOR unsel        37;44      #ff0000ff   #00000000   std
####                                   white
MENU COLOR sel          7;37;40    #c0ffffff   #ff000000   std
####                                     red
MENU COLOR hotkey       1;37;44    #ffff0000   #00000000   std
####                                   green
MENU COLOR hotsel       1;7;37;40  #ff00ff00   #ff000000   all
####

LABEL dsl
MENU LABEL ^1  **** Small Linux 3.2
KERNEL /boot/dsl/linux24
APPEND ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=/boot/dsl/minirt24.gz dma acpi nomce noapic quiet knoppix_dir=dsl BOOT_IMAGE=knoppix


Label SLAX
MENU LABEL ^2 SLaX
KERNEL /boot/slax/vmlinuz initrd=/boot/slax/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;telinit~4 changes=/slax/

Label UBUNTU
MENU LABEL ^3 Ubuntu

KERNEL /ubuntu/casper/vmlinuz 
append  file=/cdrom/ubuntu/casper/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz

LABEL Zenlive
MENU LABEL ^4 Zenlive
kernel /boot/zenlive/vmlinuz
append max_loop=255 initrd=/boot/zenlive/initrd.gz init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6666 root=/dev/ram0 rw vga=791 splash=silent keyb=us lang=en_US autologin

LABEL Fedora
MENU LABEL ^5 Fedora
KERNEL /boot/fedora/vmlinuz0  
append initrd=/boot/fedora/initrd0.img root=CDLABEL=MYDVD rootfstype=iso9660 ro 

***** at Fedora above I've used under the name MYDVD the label I'm using for my DVD

Then, some of the initrd file have to be extracted and modified, extraction explained very well [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=703905&page=3") (in fact I've used for almost all my distros the advices from there)
Fedora - extracted initrd0.img and the i modified the /sbin/real-init file, replacing all references to LiveOS directory to fedora, EXCEPT 
/squashfs/LiveOS/ext3fs.img
Ubuntu - extracted the /ubuntu/casper/initrd.gz file and I've modified the using the advices from the link above.
These all work. I'll try now Linux Mint, Mandriva and Opensuse


I almost forgot: some ideeas and the menu ideea was from [COLOR="Red"][here]("http://www.msfn.org/board/index.php?showtopic=94398&st=0&start=0")[/COLOR]

---

### Post by ddbekesi on 2009-02-19
Linuxmint works same as Ubuntu (no wonder, it is based on this), same modifications required. 
I'll try now with Mandriva

in isolinux.cfg I've used:

LABEL Linux Mint
MENU LABEL ^6 Linux Mint
kernel /linuxmint/casper/vmlinuz 
append  file=/cdrom/preseed/mint.seed boot=casper initrd=/linuxmint/casper/initrd.gz

---

### Post by ddbekesi on 2009-02-19
Mandriva:
I had some problems with an error like this:
Kernel Pannic - not syncing VFS : Cannot open root device when I tried to boot the mandriva from my multiboot DVD. The solution:

isolinux.cfg had this for launching Mandriva:

LABEL Mandriva
MENU LABEL ^7 Mandriva
kernel /boot/mandriva/vmlinuz    
append initrd=/boot/mandriva/initrd.gz splash=silent vga=788 

I've made a /boot/mandriva directory with vmlinuz and initrd.gz files in it, copied from the /boot/cdrom and /boot directories of the mandriva iso.
Then, I made a mandriva directory in the root of my compilation's directory (c:\mydvd) and I copied there the distrib-lzma.sqfs file from the /loopbacks directory of the mandriva iso.

Then, i unzipped with gzip -d the initrd.gz file and I mounted it in a directory (cpio doesn't work -it gives an "header has reverse byte-order" error) with the command mount -o loop initrd /tempdir. From the tempdir I edited the linuxrc file by modifying the LABEL statement from LABEL=MandrivaOne to LABEL=MYDVD and I modified the path /live/media/loopbacks/distrib-lzma.sqfs to /live/media/mandriva/distrib-lzma.sqfs. This is the only path which has to be modified!
And then I mkisofs'd it (sounds funny this expression) and voila, it works.
Next I'll try Opensuse.

---

### Post by ddbekesi on 2009-02-19
Another one :), this time Opens SuSE

I added to isolinux.cfg this:

LABEL OpenSUSE
MENU LABEL ^8 OpenSUSE
kernel /boot/opensuse/linux
append initrd=/boot/opensuse/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent

I made the /boot/opensuse directory and there I copied the linux and initrd files from /boot/i386/loader directories of the OpenSuSE iso
then I made the opensuse directory in the root of my compilation directory where I copied the openSUSE-gnome-11.1-read-only.i686-2.7.0 and config.gnome.isoclient files from the root of the OpenSUSE iso. I renamed the config.gnome.isoclient to config.isoclient and I edited it adding opensuse/ before opensuse/openSUSE-gnome-11.1.i686;2.7.0.

Then, I extracted the initrd with gzip and cpio and I edited the linuxrc and init files. In both I changed the line
export LIVECD_CONFIG="/cdrom/config.isoclient" 
to
export LIVECD_CONFIG="/cdrom/opensuse/config.isoclient"

and the 
imageName="/cdrom/$imageName-$imageVersion"
to
imageName="/cdrom/opensuse/$imageName-$imageVersion"
then, cpio and gzip back to initrd and it's working!

Dan

---

### Post by ddbekesi on 2009-02-20
I tried knoppix, too, but I did not use the knoppix_dir and knoppix_name variables as suggested in one link I gave. Instead I modified the file init from the minirt.gz. The modifications was changing the knoppix_dir="KNOPPIX" variable to point to my location (knop).

---

### Post by theozzlives on 2009-02-20
Why???

---

### Post by ddbekesi on 2009-02-20
Only for fun

---

### Post by maybeway36 on 2009-02-20
This might help you out:
[http://ubuntuforums.org/showthread.php?t=703905&page=3](http://ubuntuforums.org/showthread.php?t=703905&page=3)

---

### Post by konnorrigby on 2009-07-30
i have successfully done this, its simple as long as your folders are right...
heres mine

/boot
/ubuntu
/kubuntu
/edubuntu
-----------------
you can add what ever you want...
in boot you have isolinux/ then find isolinux.cfg
```

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

```

then menu.cfg
```

menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include text.cfg
include amdtext.cfg
include gtk.cfg
include amdgtk.cfg
menu begin advanced
    menu title Advanced options
    label mainmenu
        menu label ^Back..
        menu exit
    include stdmenu.cfg
    include adtext.cfg
    include adamdtext.cfg
    include adgtk.cfg
    include adamdgtk.cfg
menu end
label help
    menu label ^Help
    config prompt.cfg

```

and finally text.cfg
```

default ubuntu
label ubuntu
  menu label ^Ubunutu
  kernel /ubuntu/casper/vmlinuz
  append  file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz quiet splash --
label kubuntu
  menu label ^Kubuntu
  kernel /kubuntu/casper/vmlinuz
  append  file=/cdrom/kubuntu/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/kubuntu/casper/initrd.gz quiet splash --
label edubuntu
  menu label ^Edubuntuubuntu
  kernel /edubuntu/casper/vmlinuz
  append  file=/cdrom/edubuntu/preseed/edubuntu.seed boot=casper only-ubiquity initrd=/kubuntu/casper/initrd.gz quiet splash --

```

thats my dvd and works fine...
hope i helped

--konnor

---

### Post by shikima on 2009-09-09
I can see in the code that you write in edubuntu (initrd=**/kubuntu/**casper/initrd.gz quiet splash --, Is this correct??? can u copy this code again, just to check...I'm really noobie :-(

I'm looking for the files in a .rar without the distros of course, if anyone  can help me, 

default ubuntu
label ubuntu
  menu label ^Ubunutu
  kernel /ubuntu/casper/vmlinuz
  append  file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz quiet splash --
label kubuntu
  menu label ^Kubuntu
  kernel /kubuntu/casper/vmlinuz
  append  file=/cdrom/kubuntu/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/kubuntu/casper/initrd.gz quiet splash --
label edubuntu
  menu label ^Edubuntuubuntu
  kernel /edubuntu/casper/vmlinuz
  append  file=/cdrom/edubuntu/preseed/edubuntu.seed boot=casper only-ubiquity initrd=/kubuntu/casper/initrd.gz quiet splash --

---

### Post by shikima on 2009-09-30
I'm already got this, but I'm still getting problems to get submenus :(

I'm got working the next live cds
Debian 
ubuntu
kubuntu
mint
xubuntu

but I don't know how to put edubuntu, cause is a addon...maybe if I'm install it on ubuntu then use Ubuntu customization kit to get that addon installed with the ubuntu live cd...what do you think???

---

### Post by 4llf0rn0t on 2010-06-15
> Another one :), this time Opens SuSE

I added to isolinux.cfg this:

LABEL OpenSUSE
MENU LABEL ^8 OpenSUSE
kernel /boot/opensuse/linux
append initrd=/boot/opensuse/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent

I made the /boot/opensuse directory and there I copied the linux and initrd files from /boot/i386/loader directories of the OpenSuSE iso
then I made the opensuse directory in the root of my compilation directory where I copied the openSUSE-gnome-11.1-read-only.i686-2.7.0 and config.gnome.isoclient files from the root of the OpenSUSE iso. I renamed the config.gnome.isoclient to config.isoclient and I edited it adding opensuse/ before opensuse/openSUSE-gnome-11.1.i686;2.7.0.

Then, I extracted the initrd with gzip and cpio and I edited the linuxrc and init files. In both I changed the line
export LIVECD_CONFIG="/cdrom/config.isoclient" 
to
export LIVECD_CONFIG="/cdrom/opensuse/config.isoclient"

and the 
imageName="/cdrom/$imageName-$imageVersion"
to
imageName="/cdrom/opensuse/$imageName-$imageVersion"
then, cpio and gzip back to initrd and it's working!

Dan


Hi ddebekesi.

I was trying to add opensuse 11.2 to a multiboot dvd but encountered a problem. The directory structure looks like this:
```

suse
|-- boot
|   |-- grub
|   `-- i386
|       `-- loader
|           |--initrd
|           `--linux
`-- opensuse
    |-- config.isoclient
    `-- openSUSE-11.2-GNOME-Reloaded-LiveCD-read-only.i686-0.0.1

```
```

  #======================================
  # Exports (Configuration)...
  #--------------------------------------
  export systemIntegrity=clean
  export LIVECD_CONFIG="/cdrom/**opensuse**/configisoclient"
  export LIVECD="/livecd"
  export LOCAL_BOOT="no"

  imageReadOnly="$imageName"
  imageReadOnly=`echo $imageReadOnly | sed -e s@.$ARCH@@`
  imageReadOnly="$imageReadOnly-read-only.$ARCH-$imageVersion"
  imageName="/cdrom/**opensuse**/$imageName-$imageVersion"
  gzippName=$imageName.gz
  imageMD5s="$imageName.md5"


```

[/CODE]
and **config.isoclient**
```
IMAGE=/dev/ram1;**opensuse/**openSUSE-11.2-GNOME-Reloaded-LiveCD.i686;0.0.1
UNIONFS_CONFIG=/dev/ram1,/dev/loop1,clicfs
```

If I try to edit init and linuxrc and append a prefix directory such as 'opensuse' in the LIVECD_CONFIG and imageName like in your example,then cpio'd and gzip back to initrd and then test the iso image, it spills a kernel panic init not found.

Thanks in advance for any help.

---

### Post by myrosia on 2010-12-30
> **4llf0rn0t said:**
> Hi ddebekesi.

I was trying to add opensuse 11.2 to a multiboot dvd but encountered a problem. The directory structure looks like this:
```

suse
|-- boot
|   |-- grub
|   `-- i386
|       `-- loader
|           |--initrd
|           `--linux
`-- opensuse
    |-- config.isoclient
    `-- openSUSE-11.2-GNOME-Reloaded-LiveCD-read-only.i686-0.0.1

``````



This is obviously two years late, but I found this thread very helpful, so I thought I'd post a solution for people who may be googling. I was able to get OpenSuse 11.3 live CD and Gparted running, and without the need to modify initrd, but that required several modifications to the procedure, mainly due to the way that OpenSuse 11.3 behaves.

There were three issues for me with OpenSuse 11.3:
First, it needs to know where the image lives and have the correctly configured isoclient file.
Second, it does some fancy checking for boot device, which relies on the file /boot/grub/mbrid being there and matching the MBR. Else it can throw errors about not finding the USB stick.
Finally, it tries to re-size the partition where it lives on the first reboot, and falls over if it is vfat.


Here's how I solved these. For resizing, turned out that it really wants the ext file system. So instead of formatting your stick to FAT32, format it to ext2 and use extlinux. The menu format stays exactly the same as the syslinux menus presented here, but the menu file is called extlinux.conf. You install exlinux on a mounted partition, using the command [CODE]extlinux --install /mnt/usbdisk
```(or wherever your disk is mounted). You make the disk bootable by running 
```
dd conv=notrunc bs=440 count=1 if=/usr/share/syslinux/mbr.bin of=/dev/sdb
parted /dev/sdb set 1 boot on

```For mbrid, after the disk was formatted and mbr installed, the command that matches OpenSuse 11.3 is
```
 mkdir -p  /mnt/usbdisk/boot/grub/
dd if=/dev/sdb bs=1 count=4 skip=$((0x1b8))|hexdump -n4 -e '"0x%x"'>/mnt/usbdisk/boot/grub/mbrid

```I found the right command in the searchBIOSBootDevice function, "compare ID with MBR entry" section, in the "include" file that comes out of unpacked OpenSuse LiveCD initrd. 

For getting the image location right, I needed two modifications: specify livecd_config in the menu file, and modify the isoclient.config. The opensuse lives in "opensuse" directory on my usb stick. It contains config.isoclient boot directiories copied from the live CD. The menu entry for syslinux/extlinux is:

```
 label openSUSE_Live_(KDE)
  menu label openSUSE Live
  kernel opensuse/boot/i386/loader/linux
  append initrd=opensuse/boot/i386/loader/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent quiet preloadlog=/dev/null livecd_config=cdrom/opensuse/config.isoclient showopts 

```The config.isoclient was modified to change IMAGE=/dev/ram1;openSUSE-kde-11.3-livecd-kde.i686;2.8.0 to

```
IMAGE=/dev/ram1;/opensuse/openSUSE-kde-11.3-livecd-kde.i686;2.8.0
```This was enough to get OpenSuse running as part of a multi-boot stick on my EEEPC 901

GParted was much simpler. It only required a menu entry (assuming it lives in the gparted directory)
 
```
label GParted Live
  MENU LABEL GParted Live (Default settings)
  kernel gparted/live/vmlinuz1
  append initrd=gparted/live/initrd1.img boot=live live-media-path=/gparted/live config  noswap  ip=frommedia  nosplash
```

---

### Post by asteriks on 2011-01-09
there would be less questions about this topics all over internet IF people who succeeded to create DVD iso image, upload it anywhere and share download link with the rest of us :popcorn:
there are upload servers where you can host files up to 5GB, for free, but I don't want to make advertisement here. 
what kind of DVD should be made? well, the best is to create it for beginners who can't do it alone, beginners usually need to try several major distros. it means ubuntu, fedora, debian, opensuse, slackware, mandriva, pclinuxos, centos, gentoo... other distros are derivatives, so, the basic is the same. 

I need DVD image with next distros:

ubuntu studio 10.10
kubuntu 10.10
*The (Amnesic) Incognito Live System 0.6.1 (based on debian)*
fedora 14
knoppix 6.2.1
ubcd 5.0.3 (Ultimate Boot CD)
ophcrack xp live cd 2.3.1
cd100627.iso (Offline NT Password & Registry Editor)
eventually and mandriva one 2010.2

update: done:) [http://ubuntuforums.org/showthread.php?t=1667160](http://ubuntuforums.org/showthread.php?t=1667160)

---


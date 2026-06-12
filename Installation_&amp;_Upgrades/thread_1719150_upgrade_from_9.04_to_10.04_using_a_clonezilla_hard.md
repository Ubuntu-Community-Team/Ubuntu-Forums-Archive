---
title: "upgrade from 9.04 to 10.04 using a clonezilla hard drive partition"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by flash007 on 2011-04-01
I'm trying to "upgrade" from ubuntu 9.04 to ubuntu 10.04.2 via a clonezilla (using a maverick usb clonezilla software with it's vmlinuz and initrd.img).  but this clonezilla is not from a bootable usb flash drive, usb drive or CD, it's from the hard drive.  
Here's what I have:

1) one 500gig drive with a primary partition under LVM.  this partition has a 490gig root partition (ubuntu-root) and a 10 gig swap partition (ubuntu-swap_1).  It has an extended partition (/dev/sda2) that's not under LVM consisting of one logical drive (/dev/sda5) that is the /boot partition.
2) I've upgraded the grub to grub2 (version 1.96) which has better features
3) I've deleted the swap and reconfigured this partition with a name of (livehd) and it has an ext3 filesystem.  I've copied the clonezilla software to this partition which also has the ubuntu 10.04.2 image that I want to restore to the root partition
4) I've modified the existing grub2 using the 40-custom file so that the grub menu has the "Clonezilla Ubuntu 10.04.2 upgrade" entry in it.
5) the initrd.img from clonezilla has LVM support since I opened up the image to a directory using "gzip -d -c /boot/initrd.img|cpio -i" to check it
6) grub2 sees the (ubuntu-root), (ubuntu-livehd), (hd0,1), (hd0), and (hd0,5) devices and can list (ls) their directories

Here's what I want:

1) to make the new LVM "livehd" partition bootable
2) to use grub2 to some how chainload up and then use the "bootable" partition to boot clonezilla software to "restore" the new 10.04.2 image to the root partition and ultimately do this in a batch process

Here's what I get:

errors  not finding the root partition.  this is I believe after it loads the initial ramdisk (initrd) and loads the initial kernel (vmlinuz) and then it tries to load the read only copy of a root file system  (kind of like a mini root).  Can any one clever enough help me out here?

here is the data:
# fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1b70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60756   488022538+  8e  Linux LVM
/dev/sda2           60757       60786      240975    5  Extended
/dev/sda5           60757       60786      240943+  83  Linux

# parted -l
Model: ATA ST3500514NS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags    
 1      32.3kB  500GB  500GB  primary                boot, lvm
 2      500GB   500GB  247MB  extended                        
 5      500GB   500GB  247MB  logical   ext2                  


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-livehd: 10.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  10.1GB  10.1GB  ext3              


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 490GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  490GB  490GB  ext3              


# lvdisplay -v
  --- Logical volume ---
  LV Name                /dev/ubuntu/root
  VG Name                ubuntu
  LV UUID                8qMa59-KvmF-noql-NrMf-XWyE-Sl54-rxty8s
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                456.01 GB
  Current LE             116738
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/ubuntu/livehd
  VG Name                ubuntu
  LV UUID                b0I5oh-LO9g-2AC1-A1tE-63n5-qfCT-TPUmQb
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                9.37 GB
  Current LE             2398
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
# dpkg --get-selections |grep grub
grub                        deinstall
grub-common                    install
grub-pc                        install
grub2                        install
# aptitude show grub2
Package: grub2
State: installed
Automatically installed: no
Version: 1.96+20080724-12ubuntu2.1
Priority: extra
Section: universe/admin
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 102k
Depends: debconf (>= 0.5) | debconf-2.0, grub-pc
Description: GRand Unified Bootloader, version 2 (dummy package)
 This is a dummy transitional package to handle GRUB 2 upgrades.  It can be
 safely removed.
Homepage: [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

# cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file is an example on how to add custom entries
menuentry "My Clonezilla, Ubuntu 10.04.2" {
    set root=UUID=00df4d70-d48e-49f7-a310-9d7955126276
    chainloader +1
    linux    /live/vmlinuz subdir=live root=UUID=00df4d70-d48e-49f7-a310-9d7955126276 ro  quiet splash
    initrd    /live/initrd.img
}


And when the splash page (grub menu) comes up, I just type "c" to command line and do the following
for a manual boot:
grub> ls
(ubuntu-livehd) (ubuntu-root) (hd0) (hd0,1) (hd0,5)
grub> set root=(hd0,1)
grub> linux (ubuntu-livehd)/live/vmlinuz ro
  [Linux-bzImage, setup=0x3400, size=0x415210]
grub> initrd (ubuntu-livehd)/live/initrd.img
grub> boot


errors:

mount: cannot read /etc/fstab: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or diretory
mount: monting /sys on /root/sys fialed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
target filesystem doesn't have requested /sbin/init
no init found.  Try passing init=bootarg

/bin/sh:  can't access tty; job control turned off
(initramfs)_

---

### Post by zvacet on 2011-04-02
I never used or worked with LVM,so I will not get to the details.In general you can not skip versions if you want to upgrade ( exceptions are LTS relases,because you can upgrade from one LTS to another).In your case upgrade should look like** 9.04 > 9.10 > 10.04**

---

### Post by flash007 on 2011-04-04
This I know.  But it isn't really an upgrade.  it's a fresh install using a "fresh" clonezilla image.  The applications will be reinstalled and upgraded later against the new OS libraries.  In Ubuntu, it's all about the pkgs.  So I'm going from a 32 bit 9.04 ubuntu to 64bit 10.04.2 ubuntu.  You can't "upgrade" via normal upgrade procedures from 32bit to 64bit anyway.

---

### Post by psusi on 2011-04-04
I was confused at first by your question since clonezilla has nothing to do with upgrading.  What you really seem to want is to set up a clonezilla boot partition that contains an existing image of 10.04.2 to restore to the other partition, that just happens to already contain 9.04.

You are on the right track, you just forgot to pass any arguments to the kernel on the linux line.  You need to add root=/dev/ubuntu/livehd.

Also with grub2 you don't need a separate /boot partition; it can boot directly from LVM.

---

### Post by oldfred on 2011-04-04
I have not been a fan of LVM as it seems to add a layer of complexity. But I do have to reorganize partitions which can be a hassle. But if you only have one large LVM partition what is the advantage?

I also think system partitions should be small 10-25GB to keep the hard drive from having to search all over for commonalty used software. Let the data be in larger partitions as it is more random anyway.

---

### Post by flash007 on 2011-04-04
In this instance, for this client, there is no advantage of having just one partition.  In addition to the "upgrade" to 10.04.2 64bit, there will be additional partitions and file systems to optimize  the applications and to move them off of root.

---

### Post by flash007 on 2011-04-04
psusi:

I did try to pass parameters via the linux line.  no such luck.  And according to clonezilla, you should be able to boot directly from an iso in the local directory via loopback options:

menuentry "Clonezilla live" {
           set isofile="/home/isos/clonezilla-live-1.2.6-24.iso"
           loopback loop $isofile 
           linux (loop)/live/vmlinuz1 boot=live live-config noswap  nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\"  ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\"  ocs_lang=\"\" vga=788 ip=frommedia nosplash [COLOR=red]toram=filesystem.squashfs findiso=$isofile[/COLOR]
           initrd (loop)/live/initrd1.img
        }        

but I'm still not able to get this to work.  I'm getting some syntax errors I believe.

---

### Post by flash007 on 2011-04-04
looks like I will have to deploy the "grml" pkg to be able to use the loopback option.  I will try this out and see if this works...

---

### Post by psusi on 2011-04-05
> **oldfred said:**
> I have not been a fan of LVM as it seems to add a layer of complexity. But I do have to reorganize partitions which can be a hassle. But if you only have one large LVM partition what is the advantage?

I also think system partitions should be small 10-25GB to keep the hard drive from having to search all over for commonalty used software. Let the data be in larger partitions as it is more random anyway.

You might want to read the wiki entry I wrote about it for the long version:  [http://wiki.ubuntu.com/Lvm](http://wiki.ubuntu.com/Lvm)

The short version is that while you can use gparted to move and resize partitions on a single disk, there are a number of limitations and gotchas, and of course, you have to boot from a livecd and the process takes a long time.  With LVM, you can slice and dice partitions six ways to sunday, be it on one drive, or across several, and all without rebooting.  You can even plug in a new drive and migrate the root partition of the system you are running over to the new drive without rebooting.  I've also been experimenting lately with using snapshots to be able to test upgrading to the development release, and roll back.

> **flash007 said:**
> psusi:

I did try to pass parameters via the linux line.  no such luck.  And according to clonezilla, you should be able to boot directly from an iso in the local directory via loopback options:

menuentry "Clonezilla live" {
           set isofile="/home/isos/clonezilla-live-1.2.6-24.iso"
           loopback loop $isofile 
           linux (loop)/live/vmlinuz1 boot=live live-config noswap  nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\"  ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\"  ocs_lang=\"\" vga=788 ip=frommedia nosplash [COLOR=red]toram=filesystem.squashfs findiso=$isofile[/COLOR]
           initrd (loop)/live/initrd1.img
        }        

but I'm still not able to get this to work.  I'm getting some syntax errors I believe.

That is radically different than what you were trying before.  What exactly happens when you try to use this stanza?  Also this is for booting from the iso image file, not a hd partition with the installed system on it like you were talking about before.

---

### Post by oldfred on 2011-04-05
I have not tried ISO boot of clonezilla, but you are missing which drive, partition your /home entry in in.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

This has to be 
loopback loop $isofile 
like this for your drive & partition:
loopback loop (h0,5)$isofile

---

### Post by flash007 on 2011-04-05
psusi:  yes it is different but I'm trying to get one of these to work.  I would prefer the original way which is just uses the clonezilla iso that's opened up to a directory and copied to the partition.  In this partition, I modify a few files such as the "/live/syslinux/syslinux.cfg" file so I can eventually make this a "batch" process to "restore" a 10.04.2 image to the lvm root partition.  With extra options, I can even have it run a script just before the restore and another one just after the restore.  I just need it to boot to the lvm partition that has clonezilla software installed.

---

### Post by flash007 on 2011-04-05
tried it.  no go.  Better yet, here is what I did at the grub prompt manually:

grub> insmod loopback
grub> set root=(hd0,5)
grub> set pager=1
grub> set vbe_mode=0x123
grub> set color_normal=cyan/black
grub> loopback loop (ubuntu-root)/usr..../isos/clonezilla-live-20110218-maverick.iso
grub> linux (loop)/live/vmlinuz root=(ubuntu-root) ro
grub> initrd (loop)/live/initrd.img
grub> boot


This just boots the system normally!  ugh!

---

### Post by flash007 on 2011-04-05
psusi:  I think that the use of snapshots is sweet!  I will certainly consider it after THIS upgrade.  but keep in mind, for now, I'm trying to move from a 32bit 9.04 release to a 64bit 10.04.2 release and I can't do a "normal" OS upgrade.  And restoring a 10.04.2 image partition to an existing 9.04 partition seems technically sound.

---

### Post by oldfred on 2011-04-05
Whenever I do not know exact settings i look in Ramesh & Sundar's MultiBootUSB.sh. While I have not directly used it as I created my ISO boots manually, it has many preset to auto install.
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

This would be from flash drive so (hd0,5) not required, but would be if from hard drive. And somewhere they set the {ISO} variable in the script.
```
    menuentry "Clonezilla" {
        loopback loop /boot/iso/${ISO}
        linux (loop)/live/vmlinuz root=(loop)/ rootfstype=loop findiso=/boot/iso/${ISO} quickreboot utc=no    boot=live union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
        initrd (loop)/live/initrd.img
    }

    menuentry "Clonezilla - To RAM" {
        loopback loop /boot/iso/${ISO}
        linux (loop)/live/vmlinuz root=(loop)/ rootfstype=loop findiso=/boot/iso/${ISO} quickreboot utc=no toram=filesystem.squashfs   boot=live union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
        initrd (loop)/live/initrd.img
    }

```

---

### Post by flash007 on 2011-04-05
I tried something very similar to this but without the variable (listed complete path) and without a couple of your linux line params that I think was not necessary and got the errors:

unable to open device /dev/sda
unable to open device /dev/sda
about 20 times.  


I will try it again using all of your params and "set root=(hd0,5)"...

---

### Post by psusi on 2011-04-05
If you extract the files to a fs in that partition, then you don't want to use loopback.  Once again, you got the kernel arguments wrong.  You loaded the kernel from the iso image, but told it to mount your hard disk as the root instead of the iso image.

Go back to the stanza you had originally and add the missing root option as I said before.

Also, modifying the syslinux files won't do you any good if you are using grub.

---

### Post by flash007 on 2011-04-08
Just want you to know that I did manage to get it to work!  But in order to do that, I had to reduce the options in the 40_custom file stanza.  Of course, I had tried various combinations in addition to the "missing" root option.  so here's what go it to work using the clonezilla software in a separate ext2 filesystem:

#!/bin/sh
exec tail -n +3 $0
menuentry "Clonezilla test" {
    set root=(ubuntu-livehd)
    linux /live/vmlinuz root=/dev/ubuntu/livehd ro toram=filesystem.squashfs boot=live union=aufs live-config noswap nolocales ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8"
    initrd /live/initrd.img
}


Now I will automate this by setting the clonezilla set up with options and the partition image to batch mode.  Thanks psusi and oldfred for the collaboration and all your help!  I had this fixed Wed so sorry i didn't reply sooner

---


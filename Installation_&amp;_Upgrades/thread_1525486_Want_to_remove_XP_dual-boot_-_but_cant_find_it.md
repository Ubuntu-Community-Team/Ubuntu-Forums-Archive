---
title: "Want to remove XP dual-boot - but cant find it?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by sav25 on 2010-07-06
Hi

I have a dual boot setup where I get the option @ boot to choose either XP or Ubuntu. If I choose XP, it crashes before it loads and restarts the computer - oh how happy I am that I've moved over to Linux!

Now - I dont care about this, as I actually want to remove the XP installation.

I have tried to find the XP drive system location through Ubuntu but it's not showing up anywhere...yet XP is still showing as an option on boot?

Does anyone know where my XP install might be lurking? Is there a way to ignore XP and get the PC to automatically select Ubuntu for me?

---

### Post by wilee-nilee on 2010-07-06
From a live Ubuntu cd you should see the ntfs partitions in gparted. If you could give us a post of the boot script in my signature in code tags to confirm the whats loaded where that would be helpful.

---

### Post by sav25 on 2010-07-06
> **wilee-nilee said:**
> From a live Ubuntu cd you should see the ntfs partitions in gparted. If you could give us a post of the boot script in my signature in code tags to confirm the whats loaded where that would be helpful.

Thankyou for your offer of help...

OK here goes (i'm an extreme noob):

Boot script results: (not sure what code tags are but tried the button above?)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 107764020. According to the info 
                       in the boot sector, sda2 has 204812287 sectors, but 
                       according to the info from fdisk, it has 204812684 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   107,764,019   107,763,957  42 SFS
/dev/sda2         107,764,020   312,576,704   204,812,685  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,625,215    15,625,184   b W95 FAT32


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63    78,140,159    78,140,097   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       24eca565-2d5d-4aca-8341-b261180d4adf   ext4                                     
/dev/sda1        32F0F358F0F32131                       ntfs                                     
/dev/sda2        F2C87F1EC87EE071                       ntfs       Store                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        886C-9272                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1                                               vfat       STORAGE                       
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/886C-9272         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdg1        /media/STORAGE           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro  quiet vga=769  quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single  quiet vga=769
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro  quiet vga=769  quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single  quiet vga=769
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro  quiet vga=769  quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single  quiet vga=769
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32f0f358f0f32131
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc           proc  nodev,noexec,nosuid       0  0  
/host/ubuntu/disks/root.disk  /               ext4  loop,errors=remount-ro    0  1  
/host/ubuntu/disks/swap.disk  none            swap  loop,sw                   0  0  
/dev/fd0                      /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda2                     /media/sda2     ntfs  nls=iso8859-1,umask=000   0  0  

================= sda1/Wubi: Location of files loaded by Grub: =================


  15.5GB: boot/grub/grub.cfg
   7.0GB: boot/initrd.img-2.6.32-21-generic
   7.0GB: boot/initrd.img-2.6.32-22-generic
   7.2GB: boot/initrd.img-2.6.32-23-generic
   6.9GB: boot/vmlinuz-2.6.32-21-generic
    .5GB: boot/vmlinuz-2.6.32-22-generic
   5.8GB: boot/vmlinuz-2.6.32-23-generic
   7.2GB: initrd.img
   7.0GB: initrd.img.old
   5.8GB: vmlinuz
    .5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wilee-nilee on 2010-07-06
So you have Lucid inside of XP=wubi. If your removed XP now you would remove everything. Here is a tutorial by bcbc on how to migrate the wubi to a partition. Don't do anything without backing up what you want to save first.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Just post for more questions if you need.

If you have little or nothing to save in either XP or Ubuntu or you can just save it to a external. It might be quicker to just save it and install Lucid to the whole HD, personally I would want to save the XP though just in case of future needs, at the least a install disc.

---

### Post by bcbc on 2010-07-08
In reference to [http://ubuntuforums.org/showpost.php?p=9557900&postcount=7](http://ubuntuforums.org/showpost.php?p=9557900&postcount=7) , you could migrate wubi to an external drive and move all your data off your internal (/dev/sda), reformat and then move the migrated wubi back to it (moving an ubuntu install is pretty much the same technique as migrating a wubi install, except you don't have to remove lupin-support and the fstab is edited differently.)

That would achieve what you want - having a single partition on /dev/sda with just your current ubuntu.

It would be far simpler just to move your data from /dev/sda2 to an external backup, resize /dev/sda2 (if required), and then migrate your wubi to /dev/sda2. Then reformat and use /dev/sda1 as a separate data partition (reclaiming space if you resized /dev/sda2).

As an aside, I noticed on your boot info script results that fdisk sees your /dev/sda partitions as type SFS but blkid as ntfs. That might have something to do with the problems you're having getting XP to boot (not that it matters if you don't want XP anymore).

---

### Post by sav25 on 2010-07-08
Thanks for the replies guys.

OK so I have a friend bringing round his external hard drive for me on the weekend. As I mentioned before, i'm a noob, and i'm just a bit concerned that I will have problems doing this...so I have a few more questions if you dont mind...

The guide is for moving wubi over to a partition...so will I just follow this in the same way, but the partition will be my mates external HD right? 

He uses this HD with a windows system...it wont cause any problems for him will it? I mean, will my wubi install be like a folder or something next to his existing folders of music and pictures etc?

Once I've done this, How can I merge the partitions on my HD and wipe it clean? Is there software on ubuntu I can use for this?

Then I guess lastly, once I've merged my HD (somehow!?), do I just follow this guide again to take my wubi from my mates HD to my internal drive?


Appreciate you guys helping me here - cant thank you enough 

Rich

---

### Post by sav25 on 2010-07-08
Just to add  I just noticed this again on the guide:

[I]2. Format new partition if not done so already - make sure it's empty,  large enough and unmounted
[COLOR=Red]WARNING[/COLOR] -- the next command will wipe all  existing data on [COLOR=Red]/dev/sda5[/COLOR][/I] 


So I take it that I cant use my mates external HD without formating it first?

Also - is there any particular type of format I should go for? like NTFS or FAT etc?

thanks again!!!!!

---

### Post by sav25 on 2010-07-08
Sorry guys...but in the guide...what is a 'swap'?

It seems I have to make a choice with a 'swap' - but I havn't a clue what it is?

Rich

---

### Post by bcbc on 2010-07-08
> **sav25 said:**
> Sorry guys...but in the guide...what is a 'swap'?

It seems I have to make a choice with a 'swap' - but I havn't a clue what it is?

Rich

I'll look for some good guides for you - I probably won't get back to you until tomorrow. Don't feel like you have to rush in to this migration - the whole point of wubi is so that you don't need to worry about partitions etc.

---

### Post by sav25 on 2010-07-09
> **bcbc said:**
> I'll look for some good guides for you - I probably won't get back to you until tomorrow. Don't feel like you have to rush in to this migration - the whole point of wubi is so that you don't need to worry about partitions etc.
 
Thanks a lot :)
 
I guess I dont NEED to do what I plan on doing, but there are 2 main things that are bugging me that make me want to do it:
 
1) XP is installed on my drive and I dont want it there taking up the space
 
2) I'd like all my music and pictures on the same drive as the install - as it can get annoying having to manually select an alternative destination for CD rips etc, would be easier to just let stuff sit in the default 'music' and 'pictures' folders.
 
 
Thanks again mate

---

### Post by bcbc on 2010-07-09
> **sav25 said:**
> Just to add  I just noticed this again on the guide:

[I]2. Format new partition if not done so already - make sure it's empty,  large enough and unmounted
[COLOR=Red]WARNING[/COLOR] -- the next command will wipe all  existing data on [COLOR=Red]/dev/sda5[/COLOR][/I] 


So I take it that I cant use my mates external HD without formating it first?

Also - is there any particular type of format I should go for? like NTFS or FAT etc?

thanks again!!!!!

I'm going to supply instructions that don't require formatting the external drive. It will have to be already setup as ntfs though, in order to backup your root.disk file as fat32 only supports file sizes up to 4GB and wubi installs usually exceed this.
NOTE: don't copy your root.disk while it is in use - so you cannot boot wubi and copy it. As you are also not able to boot WindowsXP, please boot from a live CD and copy it that way.

> **sav25 said:**
> Sorry guys...but in the guide...what is a 'swap'?

It seems I have to make a choice with a 'swap' - but I havn't a clue what it is?

Rich

Swap is a special partition that the OS uses to swap out pages from memory when it becomes full. You need it if you want to hibernate from Ubuntu, or if you do memory intensive tasks. It should be at least as big as your RAM, but if you have a small amount of RAM I'd probably make it 1.5 x RAM. So 1GB RAM = 1.5GB swap.

Here's a guide to partitioning [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 


So, as I said, I'll supply instructions to achieve what you want, however, they're not straightforward. I actually recommend, backing up your data from /dev/sda2 and then using the script to migrate your wubi to /dev/sda2 and then just reuse /dev/sda1 later. That's way simpler.

But you can make that decision.

---

### Post by bcbc on 2010-07-09
I've modified my [manual]("http://ubuntuforums.org/showthread.php?t=1519354") wubi migration to support running off a live CD, using just the root.disk file - this file must be stored on a partition separate from the one you are migrating to (in your case, stored on external, migrating to internal). Since the migration is manual, you'll have to modify the commands to fit the partitions you'll be using.

WARNING. This process is not straightforward and carries a high risk e.g. if you don't backup all your data properly or enter the commands incorrectly.

I am assuming you have recreated your partitions on your internal drive after backing up, and before running this process. Your backup must include any data you want to keep from your internal drive as well as your wubi install root.disk.

Devices I used (all on external USB):
/dev/sdb3 partition containing my backed up root.disk
/dev/sdb11 ext4 partition for my new root partition 
/dev/sdb7 swap partition
/dev/sdb drive I installed the grub bootloader to

Devices you will probably use (depends how you partiton your hard drive, but e.g.):
/dev/sdb1 external usb drive partition containing backed up root.disk
/dev/sda1 root
/dev/sda2 swap
/dev/sda drive to contain grub bootloader

**NOTE **Do not paste to terminal and then try and modify the command - if you paste a linefeed the command will run before you get a chance to change it. Copy all commands to a text editor, change them there before cutting and pasting to terminal.

```
sudo -i
mkdir /media/backup
mount /dev/**sdb3** /media/backup
mount -o loop /media/backup/**root.disk** /mnt
[COLOR="red"]#next command will format the named partition[/COLOR]
mkfs.ext4 /dev/**sdb11**

mkdir /tmp/wubimove
mount /dev/**sdb11** /tmp/wubimove
rsync -av --exclude=/mnt/host --exclude=/mnt/mnt/* --exclude=/mnt/home/*/.gvfs --exclude=/mnt/media/*/* --exclude=/mnt/tmp/* --exclude=/mnt/proc/* --exclude=/mnt/sys/* /mnt/ /tmp/wubimove
chmod -x /tmp/wubimove/etc/grub.d/10_lupin

mkswap /dev/**sdb7**
echo "RESUME=UUID=$(blkid -o value -s UUID /dev/**sdb7**)" > /tmp/wubimove/etc/initramfs-tools/conf.d/resume

sed -i 's:/.*[\.]disk .*::' /tmp/wubimove/etc/fstab    
echo "UUID=$(blkid -o value -s UUID /dev/**sdb11**)    /    ext4    errors=remount-ro    0    1" >> /tmp/wubimove/etc/fstab
echo "UUID=$(blkid -o value -s UUID /dev/**sdb7**)    none    swap    sw    0    0" >> /tmp/wubimove/etc/fstab

for i in dev proc sys dev/pts; do mount --bind /$i /tmp/wubimove/$i; done
chroot /tmp/wubimove
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get -y remove lupin-support
update-grub
grub-install /dev/**sdb**
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys; do umount /tmp/wubimove/$i; done
rmdir /tmp/wubimove/host
umount /dev/**sdb11**
exit
exit

```

I'm attaching the terminal output from when I did the migration so you can compare (especially if you get any errors or think something is wrong). The difference in the rsync command (I dropped the verbose option) is to keep the output succinct.

---

### Post by sav25 on 2010-07-11
Hi again

I'm going to say thanks, but I have to unhappily report that I now hate Ubuntu. Well, no, that's a bit harsh. I love Ubuntu and NEARLY everything about it.

I've not been able to get online for the last 2 days because for some reason, Ubuntu likes to drop my connection before I can get past Google.

I dont know why, I cant seem to find out why (Google) and I haven't had much feedback from the forum.

So, for now, this is on hold while I painfully revert back to XP. I've overcome all of the other issues I had, some big some small, bu this one isn't looking good.

Mr Gates has me by the balls again....

Thanks for your help, and i'll post up again if I ever get the internet working *sigh*

---

### Post by alexshr on 2010-07-11
> Ubuntu likes to drop my connection before I can get past Google.

We are always here to help you, let us assist you.

> 
Mr Gates has me by the balls again Because you just ignore the problems, rather than to solve it.

Now, lets get to the actual question. It seems you haven't been able to solve your problem yet.

The bootloader for ubuntu is grub by default. The option you are looking forward is removing XP from the initial boot.

You have two options:
A. Increase time duration to have enough time to select menu option.
B. Remove XP totally from the boot options.


In both cases, you need to edit the grub.cfg file manually (although not recommended by officials), since this is generated automatically by system each time we use "sudo update-grub"
[b]
A. Increase time duration to have enough time to select menu option.[/b]
step 1. hit Alt+f2, and type "gnome-terminal" without qutoes
step 2. type "gksu gedit /boot/grub/grub.cfg" 
step 3. Find the line where it says 
```
 set timeout=10
``` and increase that to 60/120 whatever makes you happy.
```
 set timeout=60
```
step 4. to save the file hit Ctrl+S.
step 5. Close the Editor

Now, Next time you restart your system, you'll have enough time for yourself, so that you can select Ubuntu fair enough.
[b]
B. Remove XP totally from the boot options.[/b]
Step 1 & Step 2 are same.
Step 3. Find the entries that looks alike to the entries below.
```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2c36807f36804c30
	chainloader +1
}

```

And comment the whole code. So the code would look like
```

#menuentry "Windows 7 (loader) (on /dev/sda1)" {
#	insmod part_msdos
#	insmod ntfs
#	set root='(hd0,msdos1)'
#	search --no-floppy --fs-uuid --set 2c36807f36804c30
#	chainloader +1
#}

```
step 4. Save the file by hitting Ctrl+S
step 5. Close the Editor.

Now, the next time you boot the machine, the XP would have gone from the boot options. To get it back simply uncomment the lines.

with best regards,
alexshr

---

### Post by bcbc on 2010-07-11
> **sav25 said:**
> Hi again

I'm going to say thanks, but I have to unhappily report that I now hate Ubuntu. Well, no, that's a bit harsh. I love Ubuntu and NEARLY everything about it.

I've not been able to get online for the last 2 days because for some reason, Ubuntu likes to drop my connection before I can get past Google.

I dont know why, I cant seem to find out why (Google) and I haven't had much feedback from the forum.

So, for now, this is on hold while I painfully revert back to XP. I've overcome all of the other issues I had, some big some small, bu this one isn't looking good.

Mr Gates has me by the balls again....

Thanks for your help, and i'll post up again if I ever get the internet working *sigh*

In two days you go from removing xp and replacing with ubuntu to nearly hating ubuntu and reverting to xp... I think you need some time to figure out what you want :)

Anyway - I had some fun playing with the wubi migration... hope it was good for you too ;)

---


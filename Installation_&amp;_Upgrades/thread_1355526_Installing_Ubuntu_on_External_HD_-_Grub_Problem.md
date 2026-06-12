---
title: "Installing Ubuntu on External HD - Grub Problem"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by bigdiesel on 2009-12-15
Hi everyone,

I'm a noob to Ubuntu.  I decided to give it a try in VirtualBox but now I would like to have the real effect of installing Ubuntu on my external hard drive. (I can't install it internally, Vista will only allow me to shrink 2.3 GB)

I shrunk 20GB of my external HD, took the power cable off of my internal HD, rebooted with the CD and let Ubuntu install automatically by assigning the installer the free space.  The desktop loads and all is well.  I reboot and I get the:

[B]Grub loading.
error: unknown filesystem

[/B]I tried to follow steps on google but it seems everyone has a different method. In the installer it said that **dev/sde5** was Ubuntu and **dev/sde6** was the swap.

I reinstalled the same way, went into the terminal and tried looking for the menu.lst but it wasn't under the boot/grub/ folder, I don't even think it installed!

Anyways I removed that partition and I want to start from scratch again.  I really would like to run Ubuntu... but I need help, lol

Anyone wanna help out a noob :)

Thanks!! :)

---

### Post by Bartender on 2009-12-15
I'm just guessing here.  But I'm sure that GRUB error message is the key.  Just need to find someone who knows what that's telling us.

I'm not up to speed on GRUB 2.  Did you install 9.10?  I'm pretty sure, just from reading bits and pieces over the last couple of weeks, that menu.lst doesn't get you where you need to be anymore with G2.

I've only installed to externals by first formatting the entire disc to ext3 or 4, then letting GRUB have its way.  You said you made some room for GRUB on the disk.  What else is on there?  This is just a vague half-baked thought, but my understanding is even on an all-Linux HDD GRUB still builds an MBR (or the Linux equivalent of an MBR anyway) to the very beginning of the HDD.  If the leading edge of the HDD is already occupied by .jpg files or something similar, maybe GRUB wasn't able to install correctly?  That may be a monumentally incorrect supposition :D

Hopefully someone more knowledgable will show up, but my best suggestion right now is to try and slap together a test.  Borrow a spare HDD and a dock, or get another external drive; some way that you can format the entire HDD before installation as ext3 or 4 from front to back, then try again to install.

Of course, it could be something simple like a corrupted install CD.  Have you used the CD successfully before?

---

### Post by darkod on 2009-12-15
> **bigdiesel said:**
>  took the power cable off of my internal HD, rebooted with the CD and let Ubuntu install automatically by assigning the installer the free space.

I don't know for sure if this was your problem, but I never encourage unplugging drives, especially int drive when installing on ext. Remember, the OS you are installing needs to know what hardware you have present.
I wouldn't be surprised that the ext drive was labeled hd0 in grub, because it was the only one. After reconnecting the int drive it might take over the hd0 because it's internal. Automatically grub is looking at your int drive for ubuntu.

Since you are willing to reinstall, try with the int drive connected. Just make sur at the last screen, before clicking Install, click on Advanced button and check for grub2 to be installed on the ext hdd (if that's what you want). Or the int hdd, which ever way you wanted.

---

### Post by bigdiesel on 2009-12-15
I have no idea about Grub2, I've heard about it but never made anything of it.  Yeah it is Ubuntu 9.10, so it has Grub2?

So I leave my internal attached?  I don't want it having an effect on my Windows MBR.  Thanks for the input guys!

---

### Post by darkod on 2009-12-15
> **bigdiesel said:**
> I have no idea about Grub2, I've heard about it but never made anything of it.  Yeah it is Ubuntu 9.10, so it has Grub2?

So I leave my internal attached?  I don't want it having an effect on my Windows MBR.  Thanks for the input guys!

As long as you check where grub2 will be installed like I explained, you're ok. Besides, restoring windows mbr is easy too. IMHO, you can get into unneeded problems with detaching the int hdd.

---

### Post by Bartender on 2009-12-15
As darko says, if you try to install again with the internal connected be absolutely sure that you go into the "Advanced" button on the last window of the installation and tell GRUB to install to the correct drive.  GRUB uses different terminology than Linux to identify drives. Linux might say that you have sda inside and call the external sdb.  GRUB will probably call them hd0 and hd1.  From my experience, you'll see GRUB list hd0,1 and etc. also.  Those will be partitions.  You don't want to install GRUB to a partition, you want to install it to the root of the drive.  In your case, *probably* hd1.

Yeah, Ubuntu 9.10 will install GRUB 2 unless it sees that you're upgrading or dual-booting with the previous GRUB already in place.

Something we haven't touched on yet.  You'll need to decide how to set up your BIOS so that you can access the external.  The two obvious choices are use what I call the "quick-boot" function, where you tap a key during POST and pick a device to boot, or set up your BIOS so that USB is the first drive that the PC will try to boot.  That way you'll get Ubuntu with the external plugged in and Windows with the external unplugged.

---

### Post by darkod on 2009-12-15
> **Bartender said:**
>  In your case, *probably* hd1.


Not 100% sure but I believe the dropdown option for grub2 in Advanced use /dev/sdb (for example), not hd1.

---

### Post by bigdiesel on 2009-12-15
> **darkod said:**
> Not 100% sure but I believe the dropdown option for grub2 in Advanced use /dev/sdb (for example), not hd1.That's true I think I've seen it like that, but since I unplugged the internal, I saw it as /dev/sde.  Once you use the dropdown menu, hd0 wasn't selectable anymore.  So I saw dev/sde5, dev/sde6

I want to really be careful because I don't have a Vista CD to boot in case the MBR goes bad... I have that partitioned recovery.

I just don't want a situation like this occurring: [http://ubuntuforums.org/showthread.php?t=1353099](http://ubuntuforums.org/showthread.php?t=1353099)

Also, does dev/sd**e** mean external?

---

### Post by darkod on 2009-12-15
> **bigdiesel said:**
> That's true I think I've seen it like that, but since I unplugged the internal, I saw it as /dev/sde.  Once you use the dropdown menu, hd0 wasn't selectable anymore.  So I saw dev/sde5, dev/sde6

I want to really be careful because I don't have a Vista CD to boot in case the MBR goes bad... I have that partitioned recovery.

I just don't want a situation like this occurring: [http://ubuntuforums.org/showthread.php?t=1353099](http://ubuntuforums.org/showthread.php?t=1353099)

Also, does dev/sd**e** mean external?

No, it starts from /dev/sda, /dev/sdb, etc, /dev/sde, but that would mean you have 5 drives??? Also, in step 4, when it asks you where to install, you can note what it calls the ext drive. If it's /dev/sde, just watch out in Advanced options grub2 to be installed on /dev/sde too. Without a number, just /dev/sde.
Also, if you are worried about Vista MBR have this at hand:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

That is vista recovery cd image that can create recovery cd to repair the MBR. Not to install the full OS, just to repair existing install.

---

### Post by presence1960 on 2009-12-15
> **darkod said:**
> As long as you check where grub2 will be installed like I explained, you're ok. Besides, restoring windows mbr is easy too. **_*IMHO, you can get into unneeded problems with detaching the int hdd.*_**

yes, with the internal hard disk unattached during the install GRUB most likely used (hd0,Y) for the ubuntu partition. Now with the internal plugged back in the external becomes hd1 because the internal is hd0. So when you boot and GRUB comes up it is looking to the internal disk. There is no need to unplug drives when installing multiple OSs. It can get you into trouble. If you do your homework prior to installing there will be no fear or reason to unplug anything. IMHO that is the lazy person's way out.

---

### Post by presence1960 on 2009-12-15
Plug both drives in and boot from the Ubuntu 9.10 Live CD. Choose "try ubuntu without any changes", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo fdisk -l
```
That is a lowercase L in -l

Make note of your ubuntu root partition- it should be sdby- where y is the partition number. If it is not sdb use whatever fdisk says is the disk (sdc,sdd,sde, etc)

Now that you have that you want to reinstall GRUB to MBR of sdb. In terminal run this command ```
sudo mount /dev/sdby /mnt
```
Substitute the partition # for y (ex. sdb5 - 5 is the partition #)

Now run this command ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot. Boot into Ubuntu (no Live CD) and open a terminal and run ```
sudo update-grub
```
This will refresh your GRUB menu. 

You should be set now, but lets find out. Reboot & unplug the external disk to see if it boots right to windows. If it does you are good to go. When the external is unplugged Windows will boot. When the external is plugged in GRUB will take over.

If you don't boot right to windows with the external unplugged post back and we will tell you how to restore windows to MBR of external disk.

---

### Post by presence1960 on 2009-12-15
> **bigdiesel said:**
> That's true I think I've seen it like that, but since I unplugged the internal, I saw it as /dev/sde.  Once you use the dropdown menu, hd0 wasn't selectable anymore.  So I saw dev/sde5, dev/sde6

I want to really be careful because I don't have a Vista CD to boot in case the MBR goes bad... I have that partitioned recovery.

I just don't want a situation like this occurring: [http://ubuntuforums.org/showthread.php?t=1353099](http://ubuntuforums.org/showthread.php?t=1353099)

Also, does dev/sd**e** mean external?

bigdiesel download yourself an iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn it as an image to CD. This CD will then allow you to access Recovery Console ONLY for Vista. Keep it handy that way you don't have to restore your hard disk to factory image to fix MBR.

e designates the order fdisk recognizes the devices. The first is sda followed by sdb, sdc, sdd, etc.

---

### Post by bigdiesel on 2009-12-15
> **darkod said:**
> No, it starts from /dev/sda, /dev/sdb, etc, /dev/sde, but that would mean you have 5 drives???lol, that's thanks to HP and the media drive card slots for camera media!

With 10GB of free space how much should I allocate to the swap and logical partition for the root.  Also you mount the root as **/** EXT 3 and the logical partition I mount it as EXT3 **/home**?  And when it's time to mount the Grub, I mount it as **dev/sde**?

Thanks everyone!!

---

### Post by darkod on 2009-12-15
> **bigdiesel said:**
> lol, that's thanks to HP and the media drive card slots for camera media!

With 10GB of free space how much should I allocate to the swap and logical partition for the root.  Also you mount the root as **/** EXT 3 and the logical partition I mount it as EXT3 **/home**?  And when it's time to mount the Grub, I mount it as **dev/sde**?

Thanks everyone!!

You are not mounting grub, just check that the destination for it is /dev/sde in Advanced options.
You have only 10GB to dedicate? It will be tricky. The easiest way is to let ubuntu use Largest Available Free space, in other words the unallocated 10GB space. It needs to be unallocated though.
No need to create separate /home for now, especially not in 10GB. And I'm not sure how the automatic option will split the 10GB between / and swap, I assume it will make the best choice.
If creating the partitions manually, assign 1GB or max 2GB for swap, and the rest for /. Use ext4 for /.

---

### Post by bigdiesel on 2009-12-15
I'm in Ubuntu CD Mode... you guys were right, it's dev/sdb

I left my internal plugged in.  I see it as sda, I left it alone and gave 20GB on my external sdb.

** On Step 7, I clicked Advanced and it wanted to install the boot loader on (hd0).  I clicked the drop down menu and I see:

[html]dev/sda INTERNAL
dev/sda1 Windows Vista (Loader)
dev/sda2 Windows Vista (Loader)

dev/sdb EXTERNAL
dev/sdb1
dev/sdb2[/html]I guess I install the boot loader under: dev/sdb... correct?


[html]The partition tables of the following devices are changed:
 SCSI7 (0,0,0) (sdb)

The following partitions are going to be formatted:
 partition #5 of SCSI7 (0,0,0) (sdb) as ext4
 partition #6 of SCSI7 (0,0,0) (sdb) as swap[/html][B][COLOR=Red]

I'll be waiting for a response until I click install[/COLOR][/B] :)

---

### Post by darkod on 2009-12-15
Yes, /dev/sdb

---

### Post by bigdiesel on 2009-12-15
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      118991   955787056    7  HPFS/NTFS
/dev/sdb2          118992      121601    20964825    5  Extended
/dev/sdb5          118992      121487    20049088+  83  Linux
/dev/sdb6          121488      121601      915673+  82  Linux swap / Solaris
```I checked sudo fdisk -l.  Does this look ok on dev/sdb?  You think once I reboot that grub2 will be working on the external HD and the Windows MBR will work on the internal?

---

### Post by darkod on 2009-12-15
> **bigdiesel said:**
> ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      118991   955787056    7  HPFS/NTFS
/dev/sdb2          118992      121601    20964825    5  Extended
/dev/sdb5          118992      121487    20049088+  83  Linux
/dev/sdb6          121488      121601      915673+  82  Linux swap / Solaris
```I checked sudo fdisk -l.  Does this look ok on dev/sdb?  You think once I reboot that grub2 will be working on the external HD and the Windows MBR will work on the internal?

Yes, looks fine. One bigger ntfs partition, and your / and swap for ubuntu. You can't see if grub2 is present with this command, but if you selected /dev/sdb, it should be fine.
It will show up during boot only if USB HDD is set before HDD in BIOS in boot order.

---

### Post by bigdiesel on 2009-12-15
Windows MBR works great.  I made the External the primary one in BIOS, I load it up and like before:
[B]
Grub loading.
error: unknown filesystem

--------------------------------------------------

Now I see it as SDF??!!

[/B]```
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f35b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      118991   955787056    7  HPFS/NTFS
/dev/sdf2          118992      121601    20964825    5  Extended
/dev/sdf5          118992      121487    20049088+  83  Linux
/dev/sdf6          121488      121601      915673+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt

```
So I guess I got to install GRUB2 to dev/sdf because sdb doesn't exist?

---

### Post by bigdiesel on 2009-12-15
Anyways I try this:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdf5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ dev/sdf
grub-probe: error: Cannot stat `dev/sdf'
Invalid device `dev/sdf'.
Try ``grub-setup --help'' for more information.

```

What am I doing wrong? :(

---

### Post by darkod on 2009-12-15
Jumping around as sdb, sde, sdf can be a problem. Presence has more experience than me so maybe will think of something.

You could open the device.map file inside /boot/grub. From Places just open your / partition (you can do that from LiveCD) and see in /boot/grub open the device.map file.
I'm curious how all these drives are mapped.

---

### Post by bigdiesel on 2009-12-15
Under Device Map, I see:

[B](hd0)    /dev/sda
(hd1)    /dev/sdf[/B]

Which makes sense, but I can't find menu.lst

---

### Post by darkod on 2009-12-15
OK, can you post the content of /boot/grub/grub.cfg here? Please wrap it in CODE tags (with the text sepected hit the # button in the toolbar above).

---

### Post by bigdiesel on 2009-12-15
I checked /boot/grub/grub.cfg under the filesystem.  It wasn't there.  I did a search and found it in the filesystem.  The location was:** /media/43279dc7-53d4-4109-bbb1-922ec4b33720/usr/share/doc/grub-pc/examples**

This is what it said in it:

```
#
# Sample GRUB configuration file
#

insmod biosdisk
insmod pc
insmod gpt

# Boot automatically after 30 secs.
set timeout=30

# By default, boot the first entry.
set default=0

# Fallback to the second entry.
set fallback=1

# For booting GNU/Hurd
menuentry "GNU (aka GNU/Hurd)" {
    set root=(hd0,1)
    multiboot /boot/gnumach.gz root=device:hd0s1
    module /hurd/ext2fs.static --readonly \
            --multiboot-command-line='${kernel-command-line}' \
            --host-priv-port='${host-port}' \
            --device-master-port='${device-port}' \
            --exec-server-task='${exec-task}' -T typed '${root}' \
            '$(task-create)' '$(task-resume)'
    module /lib/ld.so.1 /hurd/exec '$(exec-task=task-create)'
}

# For booting GNU/Linux
menuentry "GNU/Linux" {
    set root=(hd0,1)
    linux /vmlinuz root=/dev/sda1
    initrd /initrd.img
}

# For booting FreeBSD
menuentry "FreeBSD (or GNU/kFreeBSD), direct boot" {
    set root=(hd0,1,a)
    freebsd /boot/kernel/kernel
    freebsd_loadenv /boot/device.hints
    freebsd_module /boot/splash.bmp type=splash_image_data
    set FreeBSD.vfs.root.mountfrom=ufs:ad0s1a
}
menuentry "FreeBSD (or GNU/kFreeBSD), via /boot/loader" {
    set root=(hd0,1,a)
    freebsd /boot/loader
}

# For booting NetBSD
menuentry "NetBSD" {
    set root=(hd0,1,a)
    netbsd /netbsd
}

# For booting OpenBSD
menuentry "OpenBSD" {
    set root=(hd0,1,a)
    openbsd /bsd
}

# For booting Microsoft Windows
menuentry "Microsoft Windows" {
    set root=(hd0,1)
    chainloader +1
}

# For booting Memtest86+
menuentry "Memtest86+" {
    set root=(hd0,1)
    linux16 /memtest86+.bin
}

# Change the colors.
menuentry "Change the colors" {
    set menu_color_normal=light-green/brown
    set menu_color_highlight=red/blue
}
```

---

### Post by darkod on 2009-12-15
No, this is example file. The same spot you found device.map, grub.cfg should be there. Maybe that's part of the problem too.

---

### Post by bigdiesel on 2009-12-15
nope, menu.lst or grub.cfg aren't in /boot/grub/

I think I might have to re-install grub2.  But I wonder why when I installed it, it was sdb and now it's sdf.  sdf should be permanent because I restarted and everything was the same

---

### Post by darkod on 2009-12-15
The thing is, without grub.cfg the reinstall of grub2 takes few more commands. Look here under 2) Using Ubuntu 9.10 cd. Do all the commands from both code sections because the second code section is needed for missing grub.cfg. And before executing them check if the drive is still /dev/sdf with sudo fdisk -l.
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Hope that works.

---

### Post by presence1960 on 2009-12-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external HDD plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bigdiesel on 2009-12-15
Thanks presence, here you go:

fdisk told me it was sdb before installing, after installing it tells me it is sdf

**EDIT: GParted sees my external disk as dev/sdb**

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   951,288,974   951,288,912   7 HPFS/NTFS
/dev/sda2         951,288,975   976,768,064    25,479,090   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f35b0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,911,576,159 1,911,574,112   7 HPFS/NTFS
/dev/sdb2       1,911,590,415 1,953,520,064    41,929,650   5 Extended
/dev/sdb5       1,911,590,478 1,951,688,654    40,098,177  83 Linux
/dev/sdb6       1,951,688,718 1,953,520,064     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1EFC8D61FC8D33D5" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="1A6898196897F22D" LABEL="PhlexFiles" TYPE="ntfs" 
/dev/sdb5: UUID="43279dc7-53d4-4109-bbb1-922ec4b33720" TYPE="ext4" 
/dev/sdb6: UUID="39762c36-7f9b-4432-9a4b-313533254f69" TYPE="swap" 

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
/dev/sdb5 on /media/43279dc7-53d4-4109-bbb1-922ec4b33720 type ext4 (rw,nosuid,nodev,uhelper=devkit)


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=43279dc7-53d4-4109-bbb1-922ec4b33720 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=39762c36-7f9b-4432-9a4b-313533254f69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 978.7GB: boot/initrd.img-2.6.31-16-generic-pae
 978.7GB: boot/initrd.img-2.6.31-16-generic-pae.new
 978.7GB: boot/vmlinuz-2.6.31-16-generic-pae
 978.7GB: initrd.img
 978.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

EDIT: Here is my latest fdisk:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59215   475644456    7  HPFS/NTFS
/dev/sda2           59216       60801    12739545    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f35b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      118991   955787056    7  HPFS/NTFS
/dev/sdb2          118992      121601    20964825    5  Extended
/dev/sdb5          118992      121487    20049088+  83  Linux
/dev/sdb6          121488      121601      915673+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by presence1960 on 2009-12-15
> **bigdiesel said:**
> Thanks presence, here you go:

fdisk told me it was sdb before installing, after installing it tells me it is sdf

**EDIT: GParted sees my external disk as dev/sdb**

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   951,288,974   951,288,912   7 HPFS/NTFS
/dev/sda2         951,288,975   976,768,064    25,479,090   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f35b0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,911,576,159 1,911,574,112   7 HPFS/NTFS
/dev/sdb2       1,911,590,415 1,953,520,064    41,929,650   5 Extended
/dev/sdb5       1,911,590,478 1,951,688,654    40,098,177  83 Linux
/dev/sdb6       1,951,688,718 1,953,520,064     1,831,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1EFC8D61FC8D33D5" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="1A6898196897F22D" LABEL="PhlexFiles" TYPE="ntfs" 
/dev/sdb5: UUID="43279dc7-53d4-4109-bbb1-922ec4b33720" TYPE="ext4" 
/dev/sdb6: UUID="39762c36-7f9b-4432-9a4b-313533254f69" TYPE="swap" 

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
/dev/sdb5 on /media/43279dc7-53d4-4109-bbb1-922ec4b33720 type ext4 (rw,nosuid,nodev,uhelper=devkit)


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=43279dc7-53d4-4109-bbb1-922ec4b33720 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=39762c36-7f9b-4432-9a4b-313533254f69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 978.7GB: boot/initrd.img-2.6.31-16-generic-pae
 978.7GB: boot/initrd.img-2.6.31-16-generic-pae.new
 978.7GB: boot/vmlinuz-2.6.31-16-generic-pae
 978.7GB: initrd.img
 978.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

CONFIRMED! You are missing grub.cfg- so try Darko's suggestions in post #27. If those instructions do not solve the problem then I would back up any files if possible from sdb1 to sda1, format the external HD and reinstall Ubuntu there. When you reinstall and get to the Ready to install window click the Advanced button and select /dev/sdb for GRUB install location.

It is sdb not sdf for the external disk.

You also have a problem with that NTFS partition on sdb. see the output here:

```

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by bigdiesel on 2009-12-15
I formatted my external, I'm back in live CD and GParted sees my external as dev/sdf1... why does it change from b to f? :(

Also: sudo fdisk -l says:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976758576    7  HPFS/NTFS

```

---

### Post by Bartender on 2009-12-15
I wouldn't sweat it too much.  I've done some experimenting with HDD's and saw the device name jump like that.  Everything still worked.

Since you're not afraid to format the external, I have a suggestion.  Kinda want to hear what the other guys think though.  What about setting up your Linux partitions first on that HDD, at the front of the drive, then setting up the rest of the drive as NTFS?

---

### Post by bigdiesel on 2009-12-15
> **Bartender said:**
> I wouldn't sweat it too much.  I've done some experimenting with HDD's and saw the device name jump like that.  Everything still worked.

Since you're not afraid to format the external, I have a suggestion.  Kinda want to hear what the other guys think though.  What about setting up your Linux partitions first on that HDD, at the front of the drive, then setting up the rest of the drive as NTFS?
You mean like installing Ubuntu on it and then putting files on it?  Do I partition with GParted or let the installer take its own 20GB?

---

### Post by presence1960 on 2009-12-15
> **Bartender said:**
> I wouldn't sweat it too much.  I've done some experimenting with HDD's and saw the device name jump like that.  Everything still worked.

Since you're not afraid to format the external, I have a suggestion.  Kinda want to hear what the other guys think though.  What about setting up your Linux partitions first on that HDD, at the front of the drive, then setting up the rest of the drive as NTFS?

I always set up my partitions beforehand even for Ubuntu. But either way will work. He can set up his NTFS and / and swap partitions then install Ubuntu using the manual option or just make an NTFS partition then install Ubuntu to unallocated space using the "use largest continuous free space" option.

Either way will work. That is what is so great about Linux-choices. Darko likes the unallocated space method and I like the setting up of partitions before hand. Both work well. For those unfamiliar with partitioning the method Darko recommends will yield the least amount of mistakes. For those familiar with partitioning that want greater flexibility and control the manual option I suggest is the route to go. There is a wrench for every nut!

---

### Post by bigdiesel on 2009-12-16
It didn't work, same old problem :( Ah well, looks like I won't be able to enjoy Ubuntu... I was really looking forward to it.

Thanks for all your patience and help guys! I don't know what else to do :(

---

### Post by bigdiesel on 2009-12-16
I have an idea, when it is time to install GRUB, instead of putting dev/sdb or dev/sdf, what if i replace (hd0) with (hd1)... you think it would work?

Because when I start up on the GRUB error, I enter ls and it shows me (hd0,1) (hd0,2).....  I see (hd0,5) and maybe it had to say (hd1,5).

Any ideas on this?

EDIT: I am looking at the GRUB root on Ubuntu on VirtualBox and I see (hd0,1) as the root, not dev/... whatever

---

### Post by Bartender on 2009-12-16
I'm kind of lost here.  You're right back to where you started?  You're getting the same GRUB error you reported in post #1?

Threads like yours make me want to spend some time in the shop with 3 or 4 HDD's and go thru the steps for myself.  

There are alternate methods that might work but don't get a lot of air time if you know what I mean.  For instance, there's GAG.  GAG looks to me like the Swiss Army Knife of bootloaders.  I'm thinking about downloading it and experimenting on a few HDD's.  I don't know about you, but reading is no substitute for "hands-on".

EDIT:  hd0,1 is GRUB-speak for the first partition on the first drive.  "hd0" means the first drive that GRUB recognizes and ",1" means the first partition on that drive.  Beyond that, I'm not feeling confident to say for sure what that means, but my guess is that what GRUB is telling you is that it's installed itself to the first partition on the first drive?  But that doesn't make sense because that's your NTFS-formatted Windows partition, right?

GRUB does not (unless this is a GRUB2 change?) refer to drives as dev/sda etc.  I think the developers added some code to that "Advanced" box in the installation to make things clearer for people, because it used to be strictly GRUB-speak in that "Advanced" box.  hd0, hd0,1, etc.

---

### Post by darkod on 2009-12-16
> **bigdiesel said:**
> I have an idea, when it is time to install GRUB, instead of putting dev/sdb or dev/sdf, what if i replace (hd0) with (hd1)... you think it would work?

Because when I start up on the GRUB error, I enter ls and it shows me (hd0,1) (hd0,2).....  I see (hd0,5) and maybe it had to say (hd1,5).

Any ideas on this?

EDIT: I am looking at the GRUB root on Ubuntu on VirtualBox and I see (hd0,1) as the root, not dev/... whatever

I'm also getting bit confused and don't even remember everything you tried. Did you set the ext drive as first in BIOS before installing ubuntu/grub? This might be very important potentially because with the ext hdd plugged in, you want it to be first choice for boot, so grub should use hd0 for it, and hd1 for the int hdd. But the option to be first drive in boot order has to be made before installing grub.

---

### Post by bigdiesel on 2009-12-16
Yeah, I did make it the primary boot.  I really don't know what to do, I installed and formatted my external HDD over and over.  The C: Partition will only let me shrink 124 mb, I don't know why.  Everything seems to be against me, lol

It would be easy on C: because I'd be able to use the default setting, right, dev/sda?

---

### Post by darkod on 2009-12-16
> **bigdiesel said:**
> Yeah, I did make it the primary boot.  I really don't know what to do, I installed and formatted my external HDD over and over.  The C: Partition will only let me shrink 124 mb, I don't know why.  Everything seems to be against me, lol

It would be easy on C: because I'd be able to use the default setting, right, dev/sda?

It allows you to shrink only 124MB because windows often can put files and even system files towards the end of the partition, and sometimes even defragmenting doesn't move them from there. And the built in tool to shrink doesn't seem to move files, so it only allows to shrink until it hits the first files (from the end).
That's why, even with vista and 7 having this shrink/expand tool, I prefer booting with ubuntu cd in Try Ubuntu and using Gparted. Gparted actually moves the data too so it will allow to shrink much more.
Defragmenting windows first is helping speed up the process. And watch out how much free space you have on C: at all. For example, if you have 25GB free space and want to shrink the partition by 23GB it will be very difficult if not impossible for Gparted to do that.
That's concerning the shrinking part. Note: If shrinking any version of windows with Gparted do NOT proceed to install ubuntu right away. Boot windows few times to make sure it's happy with the shrink and finishes its disk checks.
There is one more thing you haven't tried but I don't know if you're willing to. Don't have to install ubuntu on the windows drive yet, you haven't tried putting grub2 on that disk yet. I can't guarantee it will work, especially with the ext hdd name jumping around, but part of the issue might be calling grub2 from the ext hdd MBR. Putting it on int hdd MBR might solve the issue (or part of them). You can restore the windows MBR back any time if you feel like it.

---

### Post by bigdiesel on 2009-12-16
Is it possible to install Grub1 on Ubuntu 9.10?

Anyways I think I will back up my whole system, go into GParted and shrink the C: volume.  I have 248 GB free on the C: volume, so getting 20GB shouldn't be a problem, I hope

---

### Post by bigdiesel on 2009-12-16
Do you think this would work with Grub? [http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-fix-grub-boot-problem](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-fix-grub-boot-problem)

---

### Post by darkod on 2009-12-16
> **bigdiesel said:**
> Is it possible to install Grub1 on Ubuntu 9.10?

Anyways I think I will back up my whole system, go into GParted and shrink the C: volume.  I have 248 GB free on the C: volume, so getting 20GB shouldn't be a problem, I hope

I'm not experienced enough with Ubuntu to confirm if you can use grub1. You already have grub2 files installed in your / partition and I don't know how the "mix" will turn out.
Otherwise, if you can boot into your 9.10, I think the commands are:
sudo apt-get remove grub-pc (to remove grub2)
sudo apt-get install grub (to install grub1)

After that you should be able to do the steps for installing grub1 on the MBR.
And if you want to do the above from LiveCD you have to chroot into your 9.10, something like:
sudo mount /dev/sdf5 /mnt (or what ever your ext hdd will be called)
sudo chroot /mnt

Then you can remove grub2 and install grub1 as per above.

---

### Post by darkod on 2009-12-16
Look under number 11 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Looks possible.

---

### Post by presence1960 on 2009-12-16
> **bigdiesel said:**
> Do you think this would work with Grub? [http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-fix-grub-boot-problem](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-fix-grub-boot-problem)

That is for legacy GRUB 0.97 not GRUB2.

The only shortcoming with putting GRUB on MBR of the internal disk is that you will have to plug in the external everytime you boot. That is because GRUB will point to the external for grub.cfg or if you have Legacy GRUB installed menu.lst.

Since you are having problems installing to the external disk why don't you put it on the internal?

If you try that, as Darko points out about windows throwing files at the end of it'd partition you can try disabling System restore and page file until after Ubuntu is installed successfully. After disabling those files defrag windows at least once or twice and then try shrinking with windows disk management utility.

If you want to install Legacy GRUB 0.97 (truthfully that won't make much of a difference because your external designations switching drom sdb to sdf have nothing to do with GRUB) see [here]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy").

---

### Post by Bartender on 2009-12-16
I'm tinkering with a mess of HDD's, cables, and a dock, trying to set up a testbed similar to yours.

Can you tell me for sure how the external is partitioned?  A screenshot from the Ubuntu LiveCD would be wonderful...

EDIT:  And do you have a Windows OS on the external, or just a big NTFS data partition?

---

### Post by bigdiesel on 2009-12-16
Thanks for everything guys.  I got fed up and installed Ubuntu on my laptop with no problems.  I still would like it on my external, and I will still be tinkering with it.  My external is 931GB with 20GB partitioned for Ubuntu and the rest is for media, files, etc.  Ubuntu was set up in sdb5 and 6.  My problem was that it was reverting back to dev/sdf at times.

I'll try a whole bunch of things with it.  Now I gotta solve how to make my wireless network work on my Ubuntu laptop

---

### Post by Bartender on 2009-12-16
Well, bigdiesel, I didn't get anywhere close to helping you with my tinkering.  I learned a few things, at least until I lose my notes, but mostly I learned that I need to start over again with what I thought I knew about GRUB and etc.  

First things first - I was wrong about the menu in the "Advanced" tab - it's much clearer than it used to be and as long as a person had a basic understanding of his or her drives and partitions I have to admit that it's probably best to leave your internal drives plugged in, although I'd suggested unplugging them plenty of times in the past.

So I tried installing Ubuntu to a drive - let's call it Drive 2 - in my Vantec dock but it was taking an excruciatingly long time.  I bailed and installed directly from the SATA bus.  Told GRUB to install to the drive, which was recognized as sda (!) in the dock, but sdb from the motherboard.  I don't know why it was sda in the dock, something having to do with the weird way this ASUS board has always recognized drives undoubtedly.  Since the existing internal drive was in the #1 SATA port it makes sense that the second drive became sdb when plugged directly into the board.

Anyway, when I was done, I could tap the F8 key during boot and get the "quick-boot" menu.  When I chose Drive 2, I was expecting it to just boot to Ubuntu, but instead I got a GRUB screen.  Drive 1, the internal before this experiment started, has OpenSUSE installed.  The GRUB screen listed Ubuntu, Ubuntu fail-safe, memtest, and it listed OpenSUSE!  I'd heard something about the new GRUB probing for other OS'es but still this surprised me.  I chose Ubuntu and it started up.

I rebooted and this time touched nothing.  OpenSUSE came up just like before the experiment. 

Rebooted again, tapped F8, chose OpenSUSE from the Drive2 GRUB menu described above, and OpenSUSE booted again.

Turned it off, unplugged Drive 2, dropped it in the Vantec dock, started the dock, started the PC, tapped the F8 key, chose Ubuntu, got an error message: "no device found" with a long alpha-numeric code after that.  

Well, damn.

Restarted, went into OpenSUSE, it saw Drive 2.  When I clicked on it, Drive 2 was identified by the same long alphanumeric code that was in the error message.  I don't know if this is a UUID or what.

So I apologize if I muddied up your thread instead of helping.  No advice is better than bad advice.

---

### Post by bigdiesel on 2009-12-16
Thanks for trying man... what if I installed GRUB to /dev/sda/ and then I would need the external every time to start the PC.  If it would work I can then boot to Vista and download an application (I forgot the name) that will overwrite the MBR and from there you can choose Windows or Linux, maybe that way I wouldn't need the external just to go into Windows.  What do you think?

---

### Post by Bartender on 2009-12-17
> **bigdiesel said:**
> what if I installed GRUB to /dev/sda/ and then I would need the external every time to start the PC.  If it would work I can then boot to Vista and download an application (I forgot the name) that will overwrite the MBR and from there you can choose Windows or Linux, maybe that way I wouldn't need the external just to go into Windows.

Eh, I don't know.  Depends on whether you're prepared to fix the Vista MBR, because I'm thinking you'd tire of having to spin the external every time you want to use the PC.

Oh, I forgot to mention that last night I tried GAG.  I feel like I was lead down the rosy path.  I kept pushing buttons, thinking this isn't too hard, then right at the most critical spot I could not for the life of me figure out how GAG was identifying the existing HDD's, or if it was at all!  I ended up installing GAG to Drive 1 but all that did was break OpenSUSE.  I put the OpenSUSE DVD in, it has an interesting "repair" feature, and the utility recognized that the bootloader was screwed up but couldn't fix it.

Or I didn't know how to do it would probably be more accurate.

Anyway, GAG was a flop for me and I ended up reinstalling OpenSUSE from scratch.

The only thing that worked for me for sure after all the screwing around yesterday was to confirm that when GRUB is installed entirely to the same drive that has the Linux install, then I can use F8 to choose which OS to boot.  That worked.  But I already knew that.

I was surprised to see that even though I told GRUB to install itself to Drive 2 when installing Karmic, GRUB saw OpenSUSE and added it to the grub list.  This didn't botch anything up, just gave an extra option if you know what I mean.  What I mean is, even though I chose Drive 2 by using the BIOS "quick boot" function (F8 key during startup) GRUB 2 gave me the option of going **back** to Drive 1.

I just want to confirm - are you still getting the original error when trying to access the external?  That grub error about the file system?

---

### Post by bigdiesel on 2009-12-17
Yeah, same old.  I got my Vista Repair CD and I think I will try today.  I'm also thinking of resizing my internal HDD with GParted and then using that Vista repair cd to fix the mbr, I have to do that because Windows will not allow me to shrink vista more than 122mb.  On the other hand, on my laptop, it allowed me to shink up to 80gb.

---

### Post by Bartender on 2009-12-17
Are you thinking of starting over with a fresh install of Vista, or just repairing?
If you're thinking of reinstalling, even with a recovery disc instead of a genuine Vista disc, you could try something that's worked for me.  Boot from a GParted LiveCD (link under my sig), wipe out all partitions so that the drive shows as one big unallocated space, then create a primary NTFS partition at the "front" (left-hand side of the partitioning map; that's where GParted is going to want to start anyway) the size that you want for Vista.

There's one little trick to GParted - you can tell it to do something, and it will add that task to the list at the bottom of the screen.  It won't actually do the task until you hit the "Apply" button.  Apply each step as you go, don't let the tasks stack up in the list. 

Then get out of GParted LiveCD and fire up your Vista disc.  It should see the NTFS partition.  You can install to just that partition, leaving the rest of the drive free and saving yourself the hassle of shrinking/defragging. etc.

An Ubuntu LiveCD would do the job too, I just like the dedicated GParted CD better.

---

### Post by darkod on 2009-12-17
> **Bartender said:**
> 
An Ubuntu LiveCD would do the job too, I just like the dedicated GParted CD better.

And it makes you burn one more CD. :) I bet you're connected to the CD manufacturing industry. :)

Shrinking vista and trying to install Ubuntu on your int hdd sounds like a good plan, if you're willing to do it. I guess you have all you need, Vista Repair cd, Ubuntu cd, our great discussion here... :)
Just don't ask us anything else, I guess you figured out we're useless by now. :)

---

### Post by bigdiesel on 2009-12-17
Wow, this is weird... GParted can't change my sda1 drive at all, not even the installer. I'm beginning to think that my PC is very anti-Ubuntu.  I don't want to re-install Vista, just to reinstall everything again.  Looks like I gotta test the external again, lol

BTW, thanks for everything guys, you're all awesome!

EDIT: This is the info I get from GParted on my c: drive

---

### Post by darkod on 2009-12-17
When you say it can't do anything, the installer, you're not trying to make changes literary with the installer right? It depends what you want to do. For example, if deleting partition, you better use Try Ubuntu and Gparted from there. The installer process is designed NOT to change anything until you reach the final step 7. So if you plan to delete partition and see that change going forward/back in the installer, most probably it won't work/show.

PS. Wow. Can you boot vista to run the chkdsk /f it's suggesting?

---

### Post by bigdiesel on 2009-12-17
I updated my post, check the screenshot of GParted's info on my drive

---

### Post by darkod on 2009-12-17
Yeah, I updated mine too. :) Can you boot vista and do the check with the command it suggests?

---

### Post by bigdiesel on 2009-12-17
lol!  Anyways I did the chkdsk f/, it ran and it told me that there were no problems, the test was completed and as I was about to read the results, it closes on me!!

---

### Post by darkod on 2009-12-17
> **bigdiesel said:**
> lol!  Anyways I did the chkdsk f/, it ran and it told me that there were no problems, the test was completed and as I was about to read the results, it closes on me!!

Hm, I guess this is a good moment to say: Just what you can expect from Windows. :)

I have no clue what to do next. Expecially since I think it's not wise to try to repair ntfs partition from ubuntu. On the other hand, vista says all is good...

---

### Post by bigdiesel on 2009-12-17
I'm going to try on my external again... this time instead of putting dev/sdb or dev/sdf, I'm just going to put (hd1), replacing the original 0 with a 1.  When I installed Ubuntu on my laptop, I didn't have to specify the GRUB where to install, so I'm hoping hd1 can be linked as the external HDD.  I hope it works!!! :)

Hmm... /dev/sdf1/ is where I have my media files and stuff on my external.. What if I install the GRUB on /dev/sdf5/ where Ubuntu will be installed?

---

### Post by Bartender on 2009-12-17
bigdiesel, I'm gonna have to go in for counseling before this is over.  I've never seen anything like that GParted error screen you posted.

Maybe this is a dumb question, but are we **sure** your CD is good?

Right along with that would be questions about the optical drive.  After all, we're talking millions of bytes of data, and they all gotta be in the right place...

Your last post is kind of scaring me a little.  When I just start trying things without a pretty clear idea of what's going on behind the curtains it usually ends in disaster.

---

### Post by bigdiesel on 2009-12-17
> **Bartender said:**
> bigdiesel, I'm gonna have to go in for counseling before this is over.  I've never seen anything like that GParted error screen you posted.

Maybe this is a dumb question, but are we **sure** your CD is good?

Right along with that would be questions about the optical drive.  After all, we're talking millions of bytes of data, and they all gotta be in the right place...

Your last post is kind of scaring me a little.  When I just start trying things without a pretty clear idea of what's going on behind the curtains it usually ends in disaster.With that CD I installed Ubuntu on my laptop with no problems.  I also used that CD drive and CD to install Ubuntu on VirtualBox, and that worked fine.

I know, it's killing me to know why this computer rejects Ubuntu... BTW I get the blue screen of death when I open Ubuntu VirtualBox now, it was running fine, lol!!! :P

BTW, I read on howtogeek.com that Vista puts the MFT information right at the end of the partition, even after fragmenting... which I have done as well.  The partition is completely empty in the middle but there's still stuff at the end of the partition, like this example.

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/08/image43.png[/IMG]
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Bartender on 2009-12-17
Yeah, looks like another facet of Microsoft's plan to keep you from messing with their computer.  You didn't think it was *your* computer, did you??  :(

How old is your PC?  Does it act squirrely often, like something will work one day, then not the next?

---

### Post by bigdiesel on 2009-12-17
I got my PC exactly one year ago, it has been working great.  Anyways I was looking at the external HDD and I discovered Disk Utility in Ubuntu.  Here is the screenshot and all those usb ports take dev/sdb/sdc... and the external HDD takes /dev/sdf/.

As you can see, the 21GB partition for Ubuntu isn't bootable, when I installed I chose (hd1) to install the grub, now I will choose to install the grub on /dev/sdf5/ not just /dev/sdf/.  I'll give it a shot, lol (nm, that failed too)


EDIT: Hey guys, check out this site relating Ubuntu 9.10 and Grub2 on the external:  

[http://osdir.com/ml/ubuntu-users/2009-10/msg01413.html](http://osdir.com/ml/ubuntu-users/2009-10/msg01413.html)

And

[http://www.linuxquestions.org/questions/linux-software-2/configuration-problem-of-grub2-installed-in-ext.hdd-748620/](http://www.linuxquestions.org/questions/linux-software-2/configuration-problem-of-grub2-installed-in-ext.hdd-748620/)

---


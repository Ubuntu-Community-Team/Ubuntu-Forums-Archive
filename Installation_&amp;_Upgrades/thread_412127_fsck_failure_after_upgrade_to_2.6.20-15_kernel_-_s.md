---
title: "fsck failure after upgrade to 2.6.20-15 kernel - solved"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by moschops on 2007-04-17
I thought I'd share a problem I had after upgrading to 2.6.20-15 that I have now fixed.

The problem was my machine would boot just fine with Feistly 2.6.20-14 kernel but after the update manager added 2.6.20-15 it would fail every time during boot saying stuff like 

```
fsck.ext3: No such file or directory whilte trying to open /dev/hdc7
```

and  

```
/dev/hdc7:  The superblock could not be read or does not describe a correct ext2 filesstem.  If the device is valid and it really contains...  try e2fsck -b 8193 <device>
```

Unfortunately this error occured at the weekend just when other people were having problems wit the latest kernel upgrade and also I fixated on the second error about the superblock not being readable.  I assumed the worst and that my /dev/hdc7 partition was trashed.  Fortunately it only contained /home not /.  I was able to boot from a gparted boot disk and verify the partition was okay and then that 2.6.20-14 still booted just fine.

Eventually five days later I figured it out..

The problem was that while repartitioning my drive to move all my stuff into a single extended partition I had changed /etc/fstab to use /dev/hdcX instead of the UUID=<big long unique identifier> syntax (because it was quicker to type and figure out).  Unfortunately it seems that as of the 2.6.20-15 kernel it insisted my IDE drive partitions were no longer accessible as /dev/hdcX but only /dev/sdaX - if I'd been paying attention to the first error about "No such file or directory" I might have figured that out sooner.    The root partition mounted just fine because that comes from the grub menu.lst and the kernel update had already inserted the correct UUID based reference to my root drive insead of the old /dev/hdcX based one.

So I just edited /etc/fstab to put in the correct UUID=<....> references (by looking at the output of 

```
ls -l /dev/disk/by-uuid
```

and all was well.  I think most people haven't encountered this problem because the Feisty updates long ago changed their fstab to use only UUIDs - but if they have recently edited fstab to remove them and went to 2.6.20-15 kernel then they are probably stuck mounting non-root partitions like I was.

PS. Like many others I'm finding there is a significant delay in booting after moving to 2.6.20-15 - its a good 30 seconds slower at the start and I haven't figured out why yet.

---

### Post by captain.kipper on 2007-04-21
I Have a similar problem - my /home partition isn't found during boot by fsck, with a similar error message. 

I can boot into my older edgy kernel no problem, thankfully.

"ls -l /etc/disk/by-uuid" doesn't work (- No such file or directory). Can you go through more exactly for us noobs  what to do. My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /E              vfat    defaults,umask=0000        0       0
/dev/hdb1       /J              vfat    defaults,umask=0000        0       0
/dev/hdb8       /K              vfat    defaults        0       0
/dev/hdb7       /home           ext3    defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1 	/media/ipod 	vfat u	ser,noauto,umask=000 	0 	0
/dev/hda1	 /WindowsC 	ntfs 	ro,nls=utf8,umask=0222 	0 	0



and mtab like this:

/dev/hdb5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hda2 /E vfat rw,umask=0000 0 0
/dev/hdb1 /J vfat rw,umask=0000 0 0
/dev/hdb8 /K vfat rw 0 0
/dev/hdb7 /home ext3 rw 0 0
/dev/hda1 /WindowsC ntfs ro,nls=utf8,umask=0222 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdc /media/cdrom0 udf ro,noexec,nosuid,nodev,user=chris 0 0

and /dev/.udev/db/%2fblock%2fhdb%2fhdb7 is:

N:hdb7
S:disk/by-id/ata-IC35L120AVV207-0_VNVD00G4CGEG1D-part7
S:disk/by-path/pci-0000:00:1f.1-ide-0:1-part7
S:disk/by-uuid/a68f5940-be66-46ea-8bab-71691862e6c5
M:3:71
E:ID_TYPE=disk
E:ID_MODEL=IC35L120AVV207-0
E:ID_SERIAL=VNVD00G4CGEG1D
E:ID_REVISION=V24OA66A
E:ID_BUS=ata
E:ID_PATH=pci-0000:00:1f.1-ide-0:1
E:ID_FS_USAGE=filesystem
E:ID_FS_TYPE=ext3
E:ID_FS_VERSION=1.0
E:ID_FS_UUID=a68f5940-be66-46ea-8bab-71691862e6c5
E:ID_FS_LABEL=
E:ID_FS_LABEL_SAFE=

:KS Please help - I'm sure there are other crippled Ubuntu computers out there which need sorting out. 

Thanks

#### Solved ####

If you have this problem, boot into festy, then control-d (or type reboot) to get to login screen. At this point type control-alt-F1
At the prompt type 
sudo blkid

You should see that the partitions listed here. If, like me, you previously had your partitions as listed as something like hda1, hdb3 etc , you will note that they are now listed as sda1, sdb3, etc.  

Note down the drive details if you want to be careful. With me I found it was a simple change from hdb7 to sdb7 for home partition, for example. 

Restart by  typing 
sudo reboot

And boot into a previous working kernel (probably the last edgy ditro). In a terminal type:
cd /etc
sudo cp fstab fstab_backup
sudo cp mtab mtab_backup

(This just gives you a backup to go back to if things go wrong). Then type:
sudo gedit fstab

and change all "hda1" entries to "sda1", "hdb3" to "sdb3", etc. Save and exit , then type:
sudo gedit mtab

and do the same.

Restart you computer, and things should now work.

(If you have problems and need to revert to the original settings do  ctrl-alt-F1 and type:
sudo cp /etc/fstab_backup fstab
sudo cp /etc/mtab_backup mtab
sudo reboot
)

Hope this helps!

---

### Post by gmalac on 2007-04-21
Hi, same problem here and my second hard disk with /home (hdb1) was not recognised with same error, fsck and superblock...)
What I did was modify /boot/grub/menu.lst and put 2 as default so the system boots with previous Linux kernel (2.17 I guess? - I am no longer at my Ubuntu box sorry).
Anyway it works, all disks are recognised no problem.
Hope this help
Guy

---

### Post by captain.kipper on 2007-04-21
Yes, but if you want to use the new ubuntu version "Feisty Fawn" you will need to sort this out.

---

### Post by moschops on 2007-04-23
Sorry about that, it was a typo on my part, it should have read

```
ls -l /dev/disk/by-uuid
```

But it sounds like you got it fixed with the blkid program instead - that's a new one for me, thanks for sharing.

---

### Post by MasterOfMuppets on 2007-04-26
Thanks guys, this works!
Now Feisty loads up, but just to a command line... when I tried to kate something it says "can't connect to X server"...
When I try startx, I just get a non-responsive black screen. The only thing that makes any change at all as far as I can see, is CTRL+ALT+DEL which restarts the box.
I think this is a diffrent problem, but since we had the first initial problem, maybe you guys know what to do.
Thanks again!

---


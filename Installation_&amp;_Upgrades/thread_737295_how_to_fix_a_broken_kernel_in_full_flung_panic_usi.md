---
title: "how to fix a broken kernel in full flung panic using a live cd??????"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by donadam on 2008-03-27
Hi all,

Could anyone help me with a step by step guide of how to rewrite a damaged kernel using a live cd. 

Normal boot produces the following error:

Kernel panic - not syncing : VFS: unable to mount roof fs on unknown-block (0,0)

The only explanation I can think of is that last night I rushed out, and without checking the progress of upgrade installation I turned off my laptop.

Using Ubuntu 7.10 gutsy

Progress:

checked RAM - no prob
Downloaded live cd on my girlfriend's computer and got to work following Ubuntu threads
Mounted hard drive using graphical interface
opened terminal:

sudo chroot /media/disk
update-initramfs -u

Result - 100s of steps looking like this:
/usr/sbin/mkinitramfs: 235: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 236: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/apparmor: 21: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/brltty: 20: cannot create /dev/null: Permission denied

also tried:
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US                         
17% [Release gpgv 1757] [Connecting to es.archive.ubuntu.com (150.214.5.135)] [Connecting to archive.canonical.com (91.189.9gpgv: Signature made Tue Oct 16 01:53:09 2007 CEST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Get:1 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy Release.gpg [191B]                                                                 
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) gutsy/main Translation-en_US                                                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                       
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                            
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:4 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]
97% [Waiting for headers]FATAL -> Could not set non-blocking flag Bad file descriptor
E: Method http has died unexpectedly!

To no avail!!!!

How can I give myself permission to do this, OR
If anyones got a better idea how can I repair a broken Kernel using a live cd - get into my original computer and fix the prob - synaptic - fix broken dependencies would be ideal!!!! 

Hope to hear from you soon - otherwise I've got a funpacked weekend reinstalling and reconfiguring ubuntu - gotta love it eh!!!

Cheers

---

### Post by talsemgeest on 2008-03-27
I would suggest compiling the kernel. Check here: [http://linuxplanet.com/linuxplanet/tutorials/202/1/](http://linuxplanet.com/linuxplanet/tutorials/202/1/)

---

### Post by Herman on 2008-03-27
> Kernel panic - not syncing : VFS: **unable to mount roof fs on unknown-block (0,0)**
> If anyones got a better idea how can I repair a broken Kernel using a live cd - get into my original computer and fix the prob - synaptic - fix broken dependencies would be ideal!!!! 
Hope to hear from you soon - otherwise I've got a funpacked weekend reinstalling and reconfiguring ubuntu - gotta love it eh!!!
:) I think I might have a better idea.
Don't bother doing anything to your kernel, just run a file system check from your live CD. I think you have a file system problem.

Boot your Ubuntu Live CD and run 'sudo fdisk -lu' to check which partitions you have. 
If your Ubuntu partition is /dev/hda2 then run this,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```
Maybe that command will fix it or maybe it will give you some comments and tell you what to do next. Maybe it will tell you something like' Can't find superblock, if this is really an ext3 file system then run 'e2fsck -b 32768' to correct the problem'.

If it says that then run '[FONT=Bitstream Vera Sans Mono]sudo parted /dev/hda p' [/FONT]to verify that it is an ext3 file system, ```
sudo parted /dev/hda p
```
If it is an ext3 file system then you can replace the superblock with a backup supreblock. There are lots of backups of the superblock, to see where they all are, run '[FONT=Bitstream Vera Sans Mono]sudo dumpe2fs /dev/hda6 | grep -i superblock'
[/FONT]```
sudo dumpe2fs /dev/hda2 | grep -i superblock
```
Okay, noe, using one of the numbers from the output of the above command, just replace your superblock with a backup copy, like this, ```
sudo e2fsck -b 32768 /dev/hda2
```Replace '32768' with a number from the previous command's output.
That should fix your file system.
I don't think you will have anything wrong with your Linux kernel.
I think it's just your file system, it proabably was damaged from having the laptop run out of batteries during an update, so the hard drive was stopped in the middle of some 'write' operations, so it didn't get time to tidy up the file system first.

Regards, Herman :)

---

### Post by donadam on 2008-03-27
Herman,

Hmmm interesting diagnosis this is the readout:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50e8e8db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75216329    37608133+  83  Linux
/dev/sda2        75216330    78140159     1461915    5  Extended
/dev/sda5        75216393    78140159     1461883+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  169837 inodes used (3.61%)
    4593 non-contiguous inodes (2.7%)
         # of inodes with ind/dind/tind blocks: 10999/714/0
 8355414 blocks used (88.87%)
       0 bad blocks
       2 large files

  137043 regular files
   16612 directories
     132 character device files
      26 block device files
       2 fifos
     472 links
   16006 symbolic links (14138 fast symbolic links)
       7 sockets
--------
  170300 files
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/hda6 | grep -i superblock
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/hda6
Couldn't find valid filesystem superblock.
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i superblock
dumpe2fs 1.40.2 (12-Jul-2007)
  Primary superblock at 0, Group descriptors at 1-3
  Backup superblock at 32768, Group descriptors at 32769-32771
  Backup superblock at 98304, Group descriptors at 98305-98307
  Backup superblock at 163840, Group descriptors at 163841-163843
  Backup superblock at 229376, Group descriptors at 229377-229379
  Backup superblock at 294912, Group descriptors at 294913-294915
  Backup superblock at 819200, Group descriptors at 819201-819203
  Backup superblock at 884736, Group descriptors at 884737-884739
  Backup superblock at 1605632, Group descriptors at 1605633-1605635
  Backup superblock at 2654208, Group descriptors at 2654209-2654211
  Backup superblock at 4096000, Group descriptors at 4096001-4096003
  Backup superblock at 7962624, Group descriptors at 7962625-7962627
ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

and thats where it ended... sda1 being the biggest block must be ubuntu. You ould be right you know, I'm going to try sudo e2fsck -b 32768 /dev/sda1 again and see what happens, then turn restart and see if it makes any difference. 

Cheers man, people like you make ubuntu worthwhile!!!

by the way the fiddling i did earlier made a difference, the kernel seems to have calmed down but now the boot script is a bit bemused:
> /init: /init: 152 /sbin/usplash_write: not found

I'll keep you posted.

---

### Post by donadam on 2008-03-27
Aha!!!!

Seemed to have stopped, but...... this is what it waas up to (first part missing due to over sized process)> 
Free inodes count wrong for group #283 (16384, counted=13662).
Fix<y>? yes

Directories count wrong for group #283 (0, counted=19).
Fix<y>? yes

Free inodes count wrong for group #284 (16384, counted=15852).
Fix<y>? yes

Directories count wrong for group #284 (0, counted=159).
Fix<y>? yes

Free inodes count wrong for group #285 (16384, counted=15779).
Fix<y>? yes

Directories count wrong for group #285 (0, counted=22).
Fix<y>? yes

Free inodes count wrong for group #286 (16384, counted=15210).
Fix<y>? yes

Directories count wrong for group #286 (0, counted=81).
Fix<y>? yes

Free inodes count wrong (4702197, counted=4532371).
Fix<y>? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 169837/4702208 files (2.7% non-contiguous), 8355414/9402033 blocks
yyyyyyyyyyyyyyyyyyyubuntu@ubuntu:~$ 


Going for a quick restart back in a sec!!!

---

### Post by donadam on 2008-03-27
doesn't seem to have worked, I can feel a new install coming on in the form hardy.

Just one thing though: how can I get permissions to access the ubuntu partition tried copying to lacie drive and apparently I don't have permission to do so.  

Reminds me of earlier attempt to run update-initramfs -u

How can I solve this?

cheers

---

### Post by Herman on 2008-03-27
You probably need to chmod the mount point, here's a link, [File Ownership and Permissions]("http://users.bigpond.net.au/hermanzone/p10.htm#File_Ownership_and_Permissions") - fix read, write, execute and ownership issues.
```
sudo chmod 751 /media/mountpoint
```

Regards, Herman :)

---


---
title: "Can't boot Ubuntu after upgrade to 9.10"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by coolmod_200 on 2009-12-19
Hi,
I've searched threads for help with no luck. I'm a newbe with Ubuntu.

Here's my problem:
I upgraded from 9.04 to 9.10. During restart I get to the Grub Load Stage1.5 menu (dual-boot with Vista). No matter what version of Ubuntu I select ("recovery mode" or "Generic") I get the same results.  I tried the live version of 9.10 CD but it won't recognize any Linux partition in "Places" (tried sudo mount /dev/sdb1 /mnt but it keeps asking for a file system).  After the Grub menu selection, the Ubuntu logo with moving bar comes on the screen.  Next, the graphics disappear and I get the folowing text on a black screen:

init: ureadahead main process (2833) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2834) terminated with status 1
General error mounting filesystems.
A maintenance shall will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

Using Control-D gives the same info except the "main process number" chanes (i.e., 2866, 2867, 2875, etc).  I've pressed Control-D about 60 times with no luck.

If I type my password I get:

root@Don-linux:~#

None of the commands I've written down from other threads work at this prompt.

I'm really loving Ubuntu but am having trouble with the command line structure of it.

Can anyone help me with this?

Thanks in advance,
coolmod_200

---

### Post by phillw on 2009-12-19
Hi,

If I were faced with that.... After calming down, I'd re-install Grub2. It seems to be the route of least pain for you, as it appears pretty messed up.

You need to know the partition that Ubuntu is on - That is covered in drs's excellent How-To

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

You want to be heading for Section 12.

If those instructions don't work, he points you towards [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):

For a more involved method. One of those two will get you up & running.

If, after getting Ubuntu back, you Win area has vanished, there's a How-To for that, as well --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  

Remember - you're in Grub2, not Grub Legacy.

Regards,

Phill.

---

### Post by coolmod_200 on 2009-12-19
Thanks for the reply Phill.

I booted with the 9.10 CD and tried reinstalling GRUB2 as per the instructions from your link [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) and it would not let me mount the drive.

I found the drive using "sudo fdisk -l"

When I entered "sudo mount /dev/sdb1 /mnt" it said I need to include the filesystem.

sdb1 is my boot for Linux (Ubuntu).  I tried "sudo mount /dev/sdb1 /mnt/boot" but that didn't work either.

Is there another command I need to enter to mount the hard drive (i.e. correct syntax)?

I hate to be a pain but I really want to learn this.

Thanks again,
Don

---

### Post by utnubuuser on 2009-12-19
If you can get as far as a recovery console, that means you can also access grub-command-line, and if you can get at grub, it's probably fixable.

It doesn't sound at all like a grub issue. - I had the same problem with my desktop when newer kernels were installed.  ie. the kernel went from 2.6.31-14 to 2.6.31-16 and became unusable with the same type of messages you're seeing.

The only way I was able to fix it was by mannually booting a working kernel in grub and removing the newer kernels once I managed to actually boot.

The info I used to get at a working kernel is the grub2 wiki - resue section> [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by darkod on 2009-12-19
> **coolmod_200 said:**
> Thanks for the reply Phill.

I booted with the 9.10 CD and tried reinstalling GRUB2 as per the instructions from your link [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) and it would not let me mount the drive.

I found the drive using "sudo fdisk -l"

When I entered "sudo mount /dev/sdb1 /mnt" it said I need to include the filesystem.

sdb1 is my boot for Linux (Ubuntu).  I tried "sudo mount /dev/sdb1 /mnt/boot" but that didn't work either.

Is there another command I need to enter to mount the hard drive (i.e. correct syntax)?

I hate to be a pain but I really want to learn this.

Thanks again,
Don

I didn't understand. If you have a separate /boot partition that you have created and that's /dev/sdb1, and your root partition is for example /dev/sdb2, you need to use:
sudo mount /dev/sdb2 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdb

---

### Post by darkod on 2009-12-19
Further more, the best would be to download the script from my signature, move it on desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about the boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by coolmod_200 on 2009-12-19
Thanks Darko,

```
I didn't understand. If you have a separate /boot partition that you have created and that's /dev/sdb1, and your root partition is for example /dev/sdb2, you need to use:
sudo mount /dev/sdb2 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdb
```I got to the recovery prompt when 9.10 didn't boot.  I tried your commands but they didn't work.

sudo mount /dev sbd2 /mnt  returned the response of "you must specify the filesystem type".

sudo mount /dev/sbd1 /mnt/boot  returned the response that it was already mounted.

sudo grub-install --root-directory=/mnt/ /dev/sdb  returned the response "mkdir: cannot create directory '/mnt/ /boot':  Read-only file system.

Dumb question:  Is there any easy way to undo the upgrade and go back to 9.04 other than a clean install?  I'd hate to lose my files/emails/etc.

Thanks for helping a newbe,
Don

---

### Post by darkod on 2009-12-19
Hold on, not the recovery prompt. That will load your system from hdd, I guess that's why it says it's mounted. I thought you will bot with the ubuntu cd, Try Ubuntu option.
No, I don't think there is easy way to downgrade to 9.04 now.
You didn't provide results of the script so I don't know for sure if you have boot partition at all. You didn't confirm either. Note in the commands to reinstall grub2 that you do not execute the command to mount boot unless you have it as separate /boot partition.
For executing the script I was also talking once booted with the Try Ubuntu option.
It's best to run the script, we need to see what we are dealing with.

---

### Post by coolmod_200 on 2009-12-19
Darko,

Here's what I got from running your script:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swsupend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsupend'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xddb5ddb5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   488,375,999   385,977,690   f W95 Ext d (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sda6         204,796,683   307,194,929   102,398,247   7 HPFS/NTFS
/dev/sda7         307,194,993   471,041,864   163,846,872   7 HPFS/NTFS
/dev/sda8         471,041,928   488,375,999    17,334,072   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0da49985

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    37,431,449    37,431,387  83 Linux
/dev/sdb2          37,431,450    39,102,209     1,670,760   5 Extended
/dev/sdb5          37,431,513    39,102,209     1,670,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="965464E85464CC95" LABEL="Wicks_AMDX2" TYPE="ntfs" 
/dev/sda5: UUID="E0C01090C0106F52" LABEL="Data" TYPE="ntfs" 
/dev/sda6: UUID="CA4448B74448A7D1" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda7: UUID="F438021F3801E18A" LABEL="Games" TYPE="ntfs" 
/dev/sda8: LABEL="XPRESSRECOV" UUID="E4CB-4FC3" TYPE="vfat" 
/dev/sdb5: UUID="13d34dad-8b94-4557-8e46-d603c5baa02d" TYPE="swsupend" 

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
/dev/sda8 on /media/XPRESSRECOV type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=10 
default=c:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 
```Does this help?

Thanks,
Don

---

### Post by darkod on 2009-12-20
Of course it will give an error. Look here:
[COLOR=Red]=> Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]

And then look what it can see on that first partition of sdb:
[COLOR=Red]sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
[/COLOR] 
It can't see you ubuntu root partition at all, the boot files, anything. It doesn't mean they are missing, something is wrong with recognizing the partition.

First thing to try:
Boot again with the cd, Try Ubuntu option (not from your hdd!!!). Open terminal and run a check on your /dev/sdb1 with:
sudo fsck /dev/sdb1

See if that helps.

Also, on another note. Was the vista upgrade from XP? On /dev/sda1 you have both boot files from XP and Vista. I guess it should work but it's just confusing.

---

### Post by coolmod_200 on 2009-12-20
Darko, 

I ran the command "sudo fsck /dev/sdb1" and this was the result:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb1: clean, 246441/2342912 files, 2156891/4678923 blocks
ubuntu@ubuntu:~$
```I tried booting 9.10 normally (via the GRUB) and it still didn't work.  Any other ideas / advice?

Don

p.s., Yes, I did upgrade from XP to Vista (i.e., no clean install)

---

### Post by darkod on 2009-12-20
I was hoping fsck to repair it. Sorry, but you'll have to wait for someone more experienced to help. I don't know linux enough for this. You root partition seems unrecognized somehow.

---

### Post by coolmod_200 on 2009-12-20
Darko,

I tried the command "sudo fsck /dev/sdb1" and this was the result:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb1: clean, 246441/2342912 files, 2156891/4678923 blocks
ubuntu@ubuntu:~$
```I then tried booting 9.10 normally via the GRUB menu with the no luck.  Any other ideas /advice?

Thanks,
Don

p.s., I did *upgrade* from XP to Vista.

---

### Post by coolmod_200 on 2009-12-20
Oops,

Ignore my duplicate response above (must have been a delay in the server posting so I thought I forgot to hit the "Submit Reply" button).

Darko, thanks for all your help!  If I don't receive any other advice I guess I'll just try to do a clean install from the Live CD and hope I can still get access to Vista.

Thanks again,
Don

---


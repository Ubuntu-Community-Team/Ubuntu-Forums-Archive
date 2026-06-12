---
title: "Failed Ubuntu 14.04 Upgrade - Need Help Using BusyBox (initrd.img) to rescue disk."
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by Marcus Aurelius on 2014-11-29
Hello,

I have Ubuntu 12.04 LTS and I tried to Upgrade to 14.04 LTS.  The upgrade seemed to work.  But then after a few reboots, I could not get to the desktop anymore.  Now I have the whole disk encrypted as well as the home folder.  I was able (after the crash) to upon reboot select from these options.  

Ubuntu, with Linux 3.2.0-72-generic
Ubuntu, with Linux 3.2.0-72-generic (recovery mode)
>> Under Previous Linux Versions <<
Ubuntu, with Linux 3.2.0-70-generic 
Ubuntu, with Linux 3.2.0-70-generic (recovery mode)

After selecting, I go in and enter my encryption passphrase, which begins to unlock the drive.  
One of the first error messages that comes up is:
"The link /dev/computer1/root should have been created by udev but it was not found... Falling back on direct link creation."
Then errors something like....
ata2.00: Status {DRDY ERR}
ata2.00: Status {UNC}
Failed command: Read FPDMA queued
A whole slew of short paragraph like somewhat similar and repeating errors appeared until.....

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
(initramfs)

I hit "ls" at the prompt and get:

dev lib64 lib etc sbin conf var proc
root run scripts init bin usr sys temp

Now I know that a bunch of files are missing and most notably "initrd.img" which is necessary to load.

Now I have an identical harddrive for this laptop and so I loaded Ubuntu 14.04 successfully onto this new drive and installed it on my laptop.  This is how I posted this today.  However, I still have the other harddrive laying around that will not load, with all my data on it.  I need to recover this data.  

I copied onto a USB stick the initrd.img file from the running 14.04 LTS which I want to transfer onto the 12.04 LTS.  However, inside Busybox, I can not change to the USB drive which is [SDB] attached SCSI removable disk.  I also think there is another partition on the same corrupted disk (that actually works and is not the corrupted partition) with Grub/local in it.  I could transfer the files there, if that is easier than using the USB stick, but I still don't know how to switch between partitions.

I'm somewhat new to all this, and do not know how to switch using Busybox to the flashdrive to copy the files into the 12.04 LTS root area.  Thus I can not add the files in that need to be there to load.  

Do you have any suggestions as to how this might be accomplished, and what other files I may need to transfer to that directory to boot up?

Incidentally, I tried to access the corrupted drive by attaching it in a USB docking station.  I was able to enter the encryption password but the drive would not load.  It kept saying that I was not able to mount the corrupted partition with the files, but I was able to mount the grub/local partition.  

I'd really need to access this drive, so any help is appreciated.  Thank you.



UPDATES:

Most recently I tried mounting the disk in the USB docking station and ran sudo e2fsck /dev/sdb2 and got back....

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

THEN:
~$ sudo fdisk -l|grep Linux|grep -Ev 'swap'
Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
Disk /dev/mapper/luks-59fa901d-ba51-4141-ab3a-712da3e1e406 doesn't contain a valid partition table
Disk /dev/mapper/computer1-root doesn't contain a valid partition table
Disk /dev/mapper/computer1-swap_1 doesn't contain a valid partition table
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda5          501760   625141759   312320000   83  Linux
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb5          501760   625141759   312320000   83  Linux

THEN:
~$ sudo dumpe2fs /dev/sdb2 | grep superblock
dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Couldn't find valid filesystem superblock.



FYI

---

### Post by oldfred on 2014-11-30
If you are going to use encryption, you must have very good backup procedures. The entire purpose of encryption is to prevent access. And then any drive issue may prevent passphrase from working.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---


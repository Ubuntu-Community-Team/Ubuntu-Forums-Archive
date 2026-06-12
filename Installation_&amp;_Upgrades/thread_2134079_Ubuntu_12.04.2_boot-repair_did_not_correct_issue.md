---
title: "Ubuntu 12.04.2 boot-repair did not correct issue"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by smsinf on 2013-04-10
I've run into the same problem many times, and so far I have just given up and reinstalled. I am running into an issue when I am accessing, either saving to or moving filles from an external usb hdd the internal hdd switched over to read only, then on a restart the system fails to load, I have tried boot-repair in the past and now but it says completed but it does not allow me to boot back into Ubuntu from the hdd, I am currently running it from the live cd. I am tired of this happening, and do not want to reinstall, the issue will occure next time I am reading from or writing to the hdd, it does not happen instantly. At first I thought it was related to the updates, so I tried not updating after a reinstall the error still occure, I thought it was from restarting with the external hdd attached on restart, the error still happened even after safely removing the external hdd. I have tried running sudo update-grub before every restart, this work for about a week, then I was moving backed up files from the external hdd, and the system went to read-only and now once again I can not get back into Ubuntu, the issue happens in 10.04, 11.04, 12.04, and 12.10, I have looking for other options but now I'm getting tired of this happening over and over again. This is on a Toshiba Satellite.  And the external hdd is a WD "My Passport" 1 tb.

The line from boot-repair gave me the most recent time was [http://paste.ubuntu.com/5694741](http://paste.ubuntu.com/5694741)

Any suggestions or helpful ideas would be much appritiated thank you so much.

---

### Post by The Cog on 2013-04-10
What are the symptoms, error messages etc. when the OS fails to load? 

Have you tried running ```
sudo fsck /dev/sda
``` from a live cd? This is the Linux equivalent of windows chkdsk.

---

### Post by smsinf on 2013-04-10
The system starts to load goes for a little bit, in either the recovery mode or regular mode, and for either kernal installed, the caps lock light starts to blink, and the system has text on the screen but tried running the comand output of 

sudo fsck /dev/sda

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 25690144 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? no

Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

Inode 7995678 was part of the orphaned inode list.  FIXED.
Inode 7995737 was part of the orphaned inode list.  FIXED.
Inode 7996279 was part of the orphaned inode list.  FIXED.
Inode 7996294 was part of the orphaned inode list.  FIXED.
Inode 7996352 was part of the orphaned inode list.  FIXED.
Inode 7996363 was part of the orphaned inode list.  FIXED.
Inode 7996507 was part of the orphaned inode list.  FIXED.
Inode 7996701 was part of the orphaned inode list.  FIXED.
Inode 7996714 was part of the orphaned inode list.  FIXED.
Inode 7997636 was part of the orphaned inode list.  FIXED.
Inode 7997692 was part of the orphaned inode list.  FIXED.
Inode 7997732 was part of the orphaned inode list.  FIXED.
Inode 7997733 was part of the orphaned inode list.  FIXED.
Deleted inode 7997740 has zero dtime.  Fix<y>? no

Inode 7997741 was part of the orphaned inode list.  FIXED.
Extended attribute in inode 8126476 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126541 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126564 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126585 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126601 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126614 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126834 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126845 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126862 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126927 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126947 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126964 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8126981 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8127052 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388832 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388847 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388851 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388859 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388865 has a value size (0) which is invalid
Clear<y>? no

Extended attribute in inode 8388893 has a value size (0) which is invalid
Clear<y>? no

Error reading block 88080451 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (22020608): Can't read next inode

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********

e2fsck: aborted

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********



I did not try to let it correct any errors, I did not want to make the problem worse. Should I let it correct the erros?

Thank you for the help.

---

### Post by oldfred on 2013-04-10
Do you  have good backups, it seems like you are getting a lot of issues. 

I normally suggest this which is an auto yes on repairs. Only run on ext2, ext3, or ext4 formatted partitions. Use chkdsk on NTFS partitions from Windows.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by smsinf on 2013-04-10
Thanks oldfred, the second command fixed issues on the drive yet, i still can not get into linux, when i try loading either the new kernel or the old kernel I get a message on the screen saying

Target filesystem doesn't have /sbin/init, not sure if there was another / after since i had to had write it down.

Right now linux is the only OS, I hate Windows so it will never be on my machine, I don't have any backups, I'm wondering if I should reinstall, or is there still a chance I might be able to recover, from the LiveCD I still have full access to most the file system, there are somethings I would need to back up first, but otherwise, I do not have much on the computer since the I keep having the os switch the main hdd to read only, also wondering if there is a way to keep the system from switching to read-only, or recovering from read-only with out restarting since that is when it seems to create the issues I'm experiancing.

I just ran boot repair again after the above sugestion. Will try restarting again.

Thank you for your help!

---

### Post by oldfred on 2013-04-10
Is drive ok?
You can use Disk Utility, click on drive and on the right side is Smart Data. All I know is green is ok. But it can run tests or show tonnes of detail.

I do not normally suggest it. There is a "dirty" install where you preserve most of your data and it only overwrites the system files. If you have made custom settings they would get overwritten.
       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by smsinf on 2013-04-11
Thank You oldfred, I tried the Disk Utility and it did not have errors, just a few bad sectors, so I used your method, I ended up upgrading to 12.10 since that was on my usb and running at the time and not the 12.04.2 cd.

I saw in another forum that to fix the issue of the hdd swithing to read only requires kernel 3.8* instead of 3.5 so I am going to see about following the steps to upgrade the kernel to see if that will fix the main problem I have.

---


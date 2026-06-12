---
title: "Failed to mount NTFS partition"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by farmgirl14 on 2015-11-05
I have recently updated my Ubuntu...I guess I should've left it alone.  :(  Now, I've tried to access one of my "Folders" and got this message:

Error mounting /dev/sdb1 at /media/rhonda/New Volume: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/rhonda/New Volume"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I'm NOT tech savvy...but, I need to know what to do.  PLEASE help!!!  Rhonda

---

### Post by oldfred on 2015-11-05
If you had a hard shutdown and both Linux & NTFS partitions open you probably have to do repairs. 
But you should always have good backups as drives eventually totally fail.

For Linux you can run fsck on all the ext4 partitions.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You cannot do most Windows repairs from Linux. So you need your Windows repairCD or flash drive or installer to get into repair console and run chkdsk until no errors.
      
 Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

Best never to use power switch unless that is all you can do. Remember the elephants.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by coffeecat on 2015-11-05
@farmgirl14, I've moved your post and the reply to a new thread, and given the thread a relevant title. The thread you posted to has nothing to do with your problem. Please do not hijack others' threads but start your own.

---


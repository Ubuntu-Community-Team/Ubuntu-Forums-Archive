---
title: "Unable to mount external hard drive"
date: 2018-11-02
forum: MINT
---

### Post by copperplate30 on 2018-11-02
*I'm a complete newbie**

I'm running linux mint 18.1 on my laptop and was transferring files to my external hard drive. All was going smoothly until the power failed (ok there was no notice before the battery ran out and I hadn't plugged it in). 

Now I get an unable to mount error message:
Error mounting /dev/sdb1 at /media/hannah/Maxtor: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/hannah/Maxtor"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

This thread seems to be what I'm looking for: [https://ubuntuforums.org/showthread.php?t=1837950&highlight=Unable+mount+external+hard+drive](https://ubuntuforums.org/showthread.php?t=1837950&highlight=Unable+mount+external+hard+drive)

Basically - 
Answer: "Since it worked before this you can exclude the fakeraid possibility,  which leaves a hardware fault or filesystem inconsistency. Linux will  not mount a damaged filesystem as a  precaution against further damage. As NTFS is a Microsoft fileystem you  need to run chkdsk from a Windows system to repair it. The Linux utility  ntfsfix is not a viable alternative. You need a Windows system and  chkdsk."

Reply: "And that worked!  I was able to use a friend's Windows XP and ran chkdsk  /f on restart, restarted the computer, ran the chkdsk, restarted again,  and then tried the hard drive with my linux, and it worked."

My question is - Do I plug the hard drive into another laptop/PC with windows and run these commands on that to fix it then return the hard drive to my laptop. I know the hard drive works on a macbook, so confident that the hard drive is ok. I am a complete newbie to this so sorry if this is really obvious!

---

### Post by howefield on 2018-11-02
Thread moved to the "*MINT*" forum.

---

### Post by ajgreeny on 2018-11-02
It is certainly possible that the drive is unmountable in Linux because it was not removed (or unmounted) before your power failure.

Regrettably Linux is not capable when it comes to NTFS repair, so I think your first move is to connect it to a Windows computer (any version I think will do) and run chkdsk a couple of times to see if that solves the problem.

On a general point, if you do not own a Windows machine I would advise that NTFS is not an appropriate filesystem to use with Linux as it is almost unrepairable using Linux operating systems.

---

### Post by PJW9779 on 2019-10-09
**WARNING!**

Don't give up too soon!

I had the same problem using an external USB-HD on Kubuntu.
sudo ntfsfix /dev/sdb1 only ended in
> 
[I]Going to empty the journal ($LogFile)... OK
$MFTMirr does not match $MFT (record 3).
Remount failed: Input/output error[/I]


time and again.
Then at the about 10th time it suddenly worked and repaired the disk.

---

### Post by TheFu on 2019-10-09
+1 on not using NTFS unless there isn't any other choice. If this is a Linux external disk, NTFS isn't just more corruptible, but it is also slower and doesn't support normal Unix permissions.  Today, those other things might not seem important, but they are.  Why have a 30% slower disk for no good reason?

---


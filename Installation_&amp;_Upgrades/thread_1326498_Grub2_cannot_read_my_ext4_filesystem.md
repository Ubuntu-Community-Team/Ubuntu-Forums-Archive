---
title: "Grub2 cannot read my ext4 filesystem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by chila on 2009-11-14
Hello,

Here is the problem: 

Grub cannot read my ext4 filesystem, but can read all my other drives.

Here is all the back information:

I have two drives, one with Windows XP, and the other with Ubuntu. About two weeks ago I had a fresh install of Ubuntu 9.10 under ext4, everything went smoothly. Yesterday I did a fresh install of Windows XP on one of the drives. I was aware that grub was going to be overwritten, so after that was finished I booted into my Ubuntu 9.10 Live CD to reinstall grub2. I followed the directions [here]("https://help.ubuntu.com/community/Grub2") for reinstalling grub2. I used this code:
```

sudo grub-setup -d /media/XXXXX/boot/grub -m /media/XXXXX/boot/grub/device.map /dev/sdb

```
where XXXXX was the UUID of my drive. Ubuntu was installed on /dev/sdb, Windows is installed on /dev/sda. This did now work so I tried replacing /dev/sdb with /dev/sda in my code. Still no luck. Whenever I try to boot grub does not load correctly, and reads
```
 Grub Loading.
error: Unknown Filesystem 
```
with no error number. Grub rescue begins, but I can't do much with it. After booting into Ubuntu LiveCD again I made a grub image using grub-mkimage and then booted into that and got a grub command line. I used the root command to see if grub can read my disks (to read the filesystem) and my ext4 filesystem could not be mounted.

I'm trying not to reinstall Ubuntu but I cannot think of anything else to do. I'm not sure if I have a corrupted ext4 filesystem or if grub2 is just messing up. Any ideas?

Thanks for your time

Dan

---

### Post by oldfred on 2009-11-14
Herman has several posts with a similar issue.  I might try switching drive order in BIOS since you also installed grub to sdb or check the BIOS settings as Herman suggests.

 Computer won't boot to 9.10; No Grub Menu - continues to boot windows - Herman on reinstalling & drive map
[http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900)

---

### Post by chila on 2009-11-16
This did not work for me; I tried this a few times. I couldn't boot into anything (neither ubuntu nor windows). I have since given up and reinstalled ubuntu, this time under a different filesystem so that I 'could not' get the same error ever again. Thank you for your reply.

---


---
title: "Update windows registry using ubuntu"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by garvind25 on 2016-11-14
Hi,

  I have a dual boot system : Windows XP SP2 and Ubuntu 15.10. On updating the windows service pack to ver. 3,my pc is not booting in Windows. I require to update my windows registry. Is there any utility/ way in ubuntu to modify the windows registry.

Thanks,
Arvind Gupta

---

### Post by vasa1 on 2016-11-14
Is your Win OS legal? If I understand correctly, Microsoft doesn't support Win XP anymore.

Ubuntu 15.10 is end-of-life. You need to run 14.04 LTS or 16.04 LTS or 16.10.

And I doubt there's any software of the type you seem to want.

---

### Post by garvind25 on 2016-11-14
> **vasa1 said:**
> Is your Win OS legal? If I understand correctly, Microsoft doesn't support Win XP anymore.

Ubuntu 15.10 is end-of-life. You need to run 14.04 LTS or 16.04 LTS or 16.10.

And I doubt there's any software of the type you seem to want.



I had purchased Win Xp long time back. I dont want to spend any more on Windows, so didnt upgrade it. I had googled something like chntpw for Ubuntu 12.1 in the following link:

[http://askubuntu.com/questions/135200/is-there-a-way-to-edit-the-windows-registry-from-ubuntu](http://askubuntu.com/questions/135200/is-there-a-way-to-edit-the-windows-registry-from-ubuntu)

Is there anything equivalent for Ubuntu 15.10.

Thanks,
Arvind Gupta.[URL="http://askubuntu.com/questions/135200/is-there-a-way-to-edit-the-windows-registry-from-ubuntu"]
[/URL]

---

### Post by RobGoss on 2016-11-14
You won't find much help updating XP service packs it's has no more support what so ever 

Your best best is to use a LTS distribution of Ubuntu this way you won't have to worry about it for a few years.

---

### Post by vasa1 on 2016-11-14
See [http://manpages.ubuntu.com/manpages/wily/en/man8/chntpw.8.html](http://manpages.ubuntu.com/manpages/wily/en/man8/chntpw.8.html) for 15.10 and [http://manpages.ubuntu.com/manpages/xenial/en/man8/chntpw.8.html](http://manpages.ubuntu.com/manpages/xenial/en/man8/chntpw.8.html) for 16.04.

```
       chntpw is a utility to view some information and reset  user  passwords
       in  a  Windows  NT/2000 SAM userdatabase file used by Microsoft Windows
       Operating System (in NT3.x and later versions). This  file  is  usually
       located  at \WINDOWS\system32\config\SAM on the Windows file system. It
       is not necessary to know the previous  passwords  to  reset  them.   In
       addition  it  contains  a  simple registry editor and  ahex-editor with
       which the information contained in a registry file can be  browsed  and
       modified.
```

---

### Post by garvind25 on 2016-11-15
OK ... I tried to follow the instruction in the page below:

[http://mashtips.com/how-to-edit-the-windows-registry-using-ubuntu/](http://mashtips.com/how-to-edit-the-windows-registry-using-ubuntu/)

When I did step 3 to mount the drive, I got the error:


*********************
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


*********************


I have 2 queries:

1. How to find which partition sda1/2/3 etc has windows installation (I am assuming that default partition for windows is sda2)
2. How to overcome the error


Thanks,
Arvind Gupta.

---

### Post by garvind25 on 2016-11-16
Any updates on the matter pls.?

---

### Post by SeijiSensei on 2016-11-16
Run "sudo blkid -l" to get an inventory of the filesystems on your various partitions.

---

### Post by garvind25 on 2016-11-17
Thanks for the reply. Here is the output of sudo blkid (sudo blkid -l) did not work for me.

************************************

/dev/sda1: UUID="B82456A124566284" TYPE="ntfs" PARTUUID="d09ad09a-01"
/dev/sda5: UUID="404801CD4801C320" TYPE="ntfs" PARTUUID="d09ad09a-05"
/dev/sda6: PARTUUID="d09ad09a-06"
/dev/sda7: PARTUUID="d09ad09a-07"
/dev/sda8: UUID="be0b4ea3-4b59-4f52-87b3-ca60570a4ec1" TYPE="ext4" PARTUUID="d09ad09a-08"
/dev/sda9: UUID="89bf9163-f82b-4953-8ad9-42344e301b43" TYPE="swap" PARTUUID="d09ad09a-09"

******************************************

How to find out which of sda1/5 has windows installation. (and sorry for the goofup regarding sda2 :D)

Arvind Gupta.

---

### Post by yancek on 2016-11-17
If you created the directory mount point as instructed in your link (/media/windows) you could try this to mount it:

> sudo mount -t ntfs-3g /dev/sda1 /media/windows

Repeat the process for sda5 after first unmounting sda1.  If you get the same error then your proprietary ntfs partitions are messed up and can't be repaired from Linux.  You would need to somehow run chkdsk and maybe that would help.  It seems a little odd to me that your windows partition is on a logical (sda5) unless that is a data partition.

---

### Post by oldfred on 2016-11-17
Windows has to be in sda1, or at least the boot files.
Windows in BIOS boot mode, only boots from the primary NTFS partition with the boot flag.
Since your other NTFS partition is sda5, and then that is a logical, it cannot be the boot partition.

Windows 7 and later often has a 100MB boot partition and then the main install, but XP was in one larger partition.

---


---
title: "fsck died with exit error 8"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by NE Key on 2008-04-27
Dual partition laptop.

Result of messing about with putting another OS on the spare partition is a pause on boot;
--------------------------------------------------
fsck died with exit status 8 
Failed to open the device 'UUID=4d8e8e06-39e7-4e83-8aef-03149d1c717f': No such file or directory

log : var/log/fsck/checkfs
Please repair file system manually

Maintenance shell will start
Enter root password
Control D to continue boot
------------------------------------------------------------

The system boots fine but the spare partition is not mounted at start up.


Now I can see that the spare partition, hda3, where I tried another distro has been re-named in some way so that it is not recognised by the main OS on boot.
(I first came across this when I had Ubuntu in the spare partition. I liked it so much that I installed Ubuntu on my main partition. Now when I tried to put 8,04 into the spare area to test it the same error comes up. The problem is caused by having two Ubuntu's on one disc.)

How do I manually repair this ? (The spare area has been re-formatted).

---

### Post by Pumalite on 2008-04-27
You have to edit the fstab of the OS you are trying to boot and change the wrong UUID to the correct one. The correct one is found in the fstab of the OS that owns the Grub.

---

### Post by NE Key on 2008-04-27
> **Pumalite said:**
> You have to edit the fstab of the OS you are trying to boot and change the wrong UUID to the correct one. The correct one is found in the fstab of the OS that owns the Grub.

Thank you.

Now let me work out the logic.

hda1 has my main and working Ubuntu 7.1. hda2 is now blank.
So if I install again to hda2 ..
but which OS owns the grub since I only have one OS and hda1 is the default..

I understand the principle of what you said ... I am just confused in the execution..but will work it out.

Thanks..


Uuuhm  ... fstab is in which folder ?

---

### Post by Pumalite on 2008-04-27
/etc/fstab
You can also use:
blkid

---

### Post by NE Key on 2008-04-29
Partial solution;

Edited /etc/fstab/ by putting a comment mark (#) at the start of the line that tries to mount the other partition.

Now a smooth boot but access to the other partition is difficult (though it is not normally needed).

Thanks.

---

### Post by Pumalite on 2008-04-29
You are welcome. Good luck

---

### Post by kirini on 2008-05-01
I have same problem
in ubuntu 7.10 all mounts worked in fstab
sda(3 partitoins+swap),sdb(1 partition),sdc(1partition)

when I ubgraded to hard(8.04)
first sdc1 line caused this "died with exit error 8"
I put that in comment, and it worked for few boots
now sdb1 started to do same
sdc1 is jfs and sdb1 is ext3

manualy mounting them causes no problem

so now I have those mount lines in rc.local

so far I have been dissapointed to hardy since gutsy was working ok.

---


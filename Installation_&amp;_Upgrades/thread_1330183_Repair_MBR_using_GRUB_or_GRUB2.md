---
title: "Repair MBR using GRUB or GRUB2"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2009-11-18
Hi,

I am writing some instructions (in Swedish) for how to repair the MBR when it has been overwritten by f.ex. the installation of Windows.

I used to have a page describing the traditional method using the
find, root & setup commands

Now that GRUB2 has come I will have to add information.

Here I can find information describing the "simple" and the "chroot" methods for reinstalling GRUB2:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

First of all I do not understand one part.
In the link, the instruction says:
```
#8 Chroot into your normal system device:
sudo chroot /mnt
#9 Reinstall GRUB 2:
Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 
sudo grub-install /dev/sdX
```
is this correct? If I chroot into an older system will not the OLDER GRUB (maybe GRUB Legacy) be reinstalled using this method? (The instruction says that GRUB2 will be installed.)


To my question:

Which method should I recommend to which user?

Are these reasonable recommendations?

1. If you have a Cd with GRUB Legacy and a system with GRUB Legacy, you can use these to repair according to the "find, root & setup commands"

2. If you have a Karmic CD and GRUB2 on your disk you can use either the the "simple" or the "chroot" method in the link. This will install GRUB2 on your MBR.

3. If you have a Karmic CD and GRUB Legacy on your disk, you can use the "chroot" method to reinstall GRUB Legacy on your MBR.


Thanks for advice.

---

### Post by darkod on 2009-11-18
Check here too:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Item number 13, Reinstalling Grub2 using LiveCD. Looks the same as yours, so I guess it's correct. I haven't needed to restore grub2 so far, thankfully. :)

---

### Post by yc2 on 2009-11-18
Thanks darkod, the instructions seem to be the same as in the link I quote.

However, I still want to verify _under which circumstances_ (which version of GRUB is on your disk and which is on your repair-Live-CD) _to use which method_, please?

---

### Post by forgewire on 2010-01-31
I've got grub corrupted for some reason and can't start Ubuntu anymore.
I followed all 3 ways to restore it (as described [http://ubuntuforums.org/showthread.php?t=42030](http://ubuntuforums.org/showthread.php?t=42030)) and can say that none of them worked
For example after grub-install /dev/sda it says:
'The file /boot/grub/stage1 not read properly'
And above mentioned page says nothing about how to fix it.
sudo grub-setup -d is not recognized at all.
Sick of it!

---

### Post by darkod on 2010-01-31
> **forgewire said:**
> I've got grub corrupted for some reason and can't start Ubuntu anymore.
I followed all 3 ways to restore it (as described [http://ubuntuforums.org/showthread.php?t=42030](http://ubuntuforums.org/showthread.php?t=42030)) and can say that none of them worked
For example after grub-install /dev/sda it says:
'The file /boot/grub/stage1 not read properly'
And above mentioned page says nothing about how to fix it.
sudo grub-setup -d is not recognized at all.
Sick of it!

You have to be careful whether you are using grub1 or the new grub2. You would have grub2 only with a clean install of karmic, otherwise 9.04 and earlier uses grub1. Also upgrade from 9.04 to 9.10 would leave grub1 unless specifically upgraded to grub2.

There are instructions here for both versions depending what you have:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by forgewire on 2010-01-31
Thanks for your reply
I've got this problem after using Windows Partition Magic (but I didn't mess with it, just checking partitions)
When I rebooted I've got an empty shell.
find /boot/grub/stage1 and root (hd<a>,<b>) and setup (hd0) worked there
I think it something to do with partition table or disk geometry affected by Partition Magic
I've solve the problem by restoring Windows MBR with Ultimate Boot CD
and then I rebooted with Ubuntu live CD and followed [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
(basically the same as [http://ubuntuforums.org/showthread.php?t=42030](http://ubuntuforums.org/showthread.php?t=42030)) to restore grub2
I'm running Ubuntu 9.10 and have grub2 but when it failed it seems fell back to grub1 on restart. Because I could run all commands there from 'How to restore the Ubuntu grub bootloader (9.04 and older)' part of your link [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by yc2 on 2010-02-04
> # To ensure that only the grub utilities from the LiveCD get executed, mount /usr

sudo mount --bind /usr/ /mnt/usr
# mount proc filesystem

sudo mount --bind /proc/ /mnt/proc
# Chroot into your normal system device:

sudo chroot /mnt
I am not sure if the instructions on
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
have been changed or if I read differently ;) Anyway that doesn't matter. But as I read the instructions for the chroot method my impression is now that it will install GRUB2 (chrooting into the Live CD) no matter what type of GRUB (Legacy or 2) you have on your hard disk.

It is important that we recommend the correct procedure to users. (I maintain a very simple page about GRUB-repair in Swedish).

Do you think these are the right recommendations?

> If you use GRUB Legacy (after install of earlier versions or upgrade to 9.10). use the old method (root, setup) from a Live CD 9.04 or earlier.
If you are using GRUB2 (after fresh install of 9.10), use one of the three methods in:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
(using Live CD 9.10)

---


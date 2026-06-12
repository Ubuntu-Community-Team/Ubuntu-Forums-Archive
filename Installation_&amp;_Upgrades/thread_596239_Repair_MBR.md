---
title: "Repair MBR"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by w116tjb on 2007-10-29
Okay, so I have 3 partitions plus a swap.
sda1 = Windows XP
sda2 = Ubuntu 7.10
sda4 = BackTrack2
sda5 = swap

I had Windows and Ubuntu installed previously and working fine. It used GRUB to choose the operating system at bootup. I then booted up into the BackTrack2 LiveCD and installed it to the sda4 parition and choosing to write the MBR file to the sda disk. Now when I start my computer it boots directly into BackTrack2. How do I recover my old MBR so I can choose between the 3 operating systems at bootup.

---

### Post by az on 2007-10-29
> **w116tjb said:**
> Okay, so I have 3 partitions plus a swap.
sda1 = Windows XP
sda2 = Ubuntu 7.10
sda4 = BackTrack2
sda5 = swap

I had Windows and Ubuntu installed previously and working fine. It used GRUB to choose the operating system at bootup. I then booted up into the BackTrack2 LiveCD and installed it to the sda4 parition and choosing to write the MBR file to the sda disk. Now when I start my computer it boots directly into BackTrack2. How do I recover my old MBR so I can choose between the 3 operating systems at bootup.

Use the live cd to boot.  

Mount the Ubuntu installation (sda2)
sudo mount /dev/sda2 /mnt


Chroot into it
sudo chroot /mnt

and run
sudo grub-install /dev/sda

Then reboot.

That will reinstall grub onto your MBR.

---

### Post by w116tjb on 2007-10-29
Everything works great until I try to use the grub-install command:

> 
root@ubuntu:/# sudo grub-install /dev/sda
/dev/sda: Not found or not a block device.


---

### Post by dutch1918 on 2007-10-29
> **w116tjb said:**
> Everything works great until I try to use the grub-install command:

I get the same here when I tried repairing my MBR after upgrading Xp to Vista

---

### Post by az on 2007-10-29
> **w116tjb said:**
> Everything works great until I try to use the grub-install command:

Well, if your ubuntu partition is on sda2, /dev/sda has to be a block device.  Are you sure you are typing it properly?  Unix is case-sensitive and those are slashes("/"), not backslashes ("\").

---

### Post by w116tjb on 2007-10-29
Well I'm copying and pasting straight from your directions... So it should work. I'm still getting that error message.

---

### Post by frozenjim on 2007-10-30
> **az said:**
> Use the live cd to boot.  

Mount the Ubuntu installation (sda2)
sudo mount /dev/sda2 /mnt


Chroot into it
sudo chroot /mnt

and run
sudo grub-install /dev/sda

Then reboot.

That will reinstall grub onto your MBR.

You don't have your /dev folder mapped from the liveCD.  In addition to simply chrooting into your old environment, you need to have the /dev directory included.  So here's a bit of an updated way to do it.

I don't use sudo, I just login as admin (so hit me).  Boot from liveCD of any sort (as outlined earlier in this thread), find a terminal and login.  Since I use the Ubuntu live CD to login, I find it easiest to simply use the "Terminal" program.

```

# mkdir /oldsystem
# mount /dev/sda2 /oldsystem
# [COLOR="Red"]mount -o /dev /oldsystem/dev[/COLOR]
# chroot /oldsystem
```

You should now be in your old Linux installation AND you should see all of your /dev devices listed.  From here you should be able to use grub-install.
```

# grub-install /dev/sda
```

Of course if you have toasted your MBR, like I have, then this appears to work but you just see the word "GRUB" when you reboot.  But that's for another thread I think. ;-)

---

### Post by w116tjb on 2007-10-30
I actually found this last night and it worked for me...

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair")

---

### Post by terjeloe on 2007-10-31
I got the same problem.. but when I do the mount -o line I get an error:

```

ubuntu@ubuntu:~$ sudo mount -o /dev /oldsystem/dev
mount: can't find /oldsystem/dev in /etc/fstab or /etc/mtab
```

---

### Post by terjeloe on 2007-10-31
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---


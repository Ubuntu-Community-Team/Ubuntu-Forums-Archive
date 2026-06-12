---
title: "Restore Ubuntu Server 10.04"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by ambre on 2013-03-01
Hi guys,

I have been backing up the whole of my home server (Ubuntu 10.04) every day using 'tar', so now that my server's hard disk has gone down I'm in good shape to recover my working system to a new hard drive from my latest backup, right?

Well all attempts so far have failed!

Can anyone show me a 'howto' to restore my system?

Many thanks,
Ambre

---

### Post by MAFoElffen on 2013-03-01
You know that "after" you unoack the tar archive back onto the new drive, that you have to install the grub bootloader right? Otherwise there is no bootloader in the mbr and it won't boot...

Many instructions (search) here to do that from the LiveCD...

Here's a howto. Skip to part 2:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by ambre on 2013-03-04
I was aware that I needed to reinstall GRUB.

That is the real sticking point.  I have two CD's with 10.04 on them, one the server version the other the desktop version.  They are proving to be useless.  Depending on what I do, and believe me I have tried everything I can find on the 'net, the boot sequence either just locks up, exits to an initramfs prompt or exits to a grub prompt.  I have even researched these options, but alas no joy.

My system has now been down for more than a week and still no sign of a recovery.

I really could do with practical advise from someone who has been in this situation.

Regards
Ambre

---

### Post by tgalati4 on 2013-03-04
If I understand correctly, your machine won't boot with either desktop or server 10.04 disk?  Perhaps it wasn't the hard disk that went bad but the motherboard or power supply.  For instance, you are getting some power to boot, but not enough to completely power the motherboard to complete the boot sequence.

Have you clean out the system and reseated everything?  How old is the computer?

---

### Post by ambre on 2013-03-04
It is not the machine.

I can re-install 10.04 server from the CD and it will boot up and run - no problem.  If I then recover my system from the tar backup, overwriting everything, it will no longer boot up and I am unable to repair GRUB.

---

### Post by darkod on 2013-03-04
Installing grub2 on the MBR is needed but it doesn't update grub.cfg. Your grub.cfg in the backup has the UUID of your old root partition, so it can't boot correctly. In my opinion this is the problem.

After unpacking the backup, chroot into the root partition and try updating grub and then installing it on the MBR. If you are not familiar with the chroot procedure, let us know which is your root partition (and whether you have separate /boot partition or not) and we can help.

---

### Post by arpanaut on 2013-03-04
Do your UUID's of your partitions match what is in your /etc/fstab?
If they don't match, what grub is trying to boot won't be found.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I don't know if that IS the problem but might be worth looking in to.

---

### Post by darkod on 2013-03-04
> **arpanaut said:**
> Do your UUID's of your partitions match what is in your /etc/fstab?
If they don't match, what grub is trying to boot won't be found.

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I don't know if that IS the problem but might be worth looking in to.

+1. Forgot to mention fstab too. You need to adjust the UUID in fstab but also in grub.cfg which is done automatically when running update-grub from chroot (running the command in terminal in live mode won't do it).

---

### Post by ambre on 2013-03-04
> **darkod said:**
> +1. Forgot to mention fstab too. You need to adjust the UUID in fstab but also in grub.cfg which is done automatically when running update-grub from chroot (running the command in terminal in live mode won't do it).

Thanks guys, I think you are close to the mark with your suggestions.  Unfortunately, this old duffer does not have the knowledge to do these things on his own.  Any chance of a step-by-step guide?

I can start again.  Do a fresh install of 10.04 server from the CD; restore my latest backup, then what?

Forgot to mention: root partition is the first partition on the first drive.  I did a simple install, no separate boot partition.

---

### Post by darkod on 2013-03-04
Why fresh install? If you copied ALL of the root partition, you only copy it back to /dev/sda1 (first partition on first disk), and it should be fine. But only if you have the whole root in the backup.

You will have to work from the live cd in live mode, because that allows you to boot the computer/server in live mode and work on it.
1. To get the UUID of the new /dev/sda1:
```
sudo blkid
```

2. After you copy the files to sda1, to edit fstab with the new UUID:
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab (that's for GUI, for editing in terminal you can also use: sudo nano /mnt/etc/fstab)
```
Replace the UUID string in the / line with the new UUID of sda1. Save and close the file.

3. For chroot to try updating grub2, if you mounted sda1 at /mnt as I wrote above, continue in terminal:
```
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation:
```
update-grub (inside chroot you are like root so you don't need sudo in front of commands)
grub-install /dev/sda (to add grub2 to sda MBR)
```

Exit chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Reboot and keep fingers crossed. :)

---

### Post by ambre on 2013-03-05
darkod,

I am following you instructions and have reached the point of running update-grub.  This is the output
-----
Searching for GRUB installation diectory ... found: /boot/grub
usr/sbin/update-grub: line 85: /usr/bin/awk: Permmision denied
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid fstab
usr/sbin/update-grub: line 85: /usr/bin/awk: Permmision denied
usr/sbin/update-grub: line 375: /usr/bin/awk: Permmision denied
-----

Stuck again, sorry.

---

### Post by darkod on 2013-03-05
You can see it's complaining about probable invalid fstab. Is your /etc/fstab correct? It seems you might have done some syntax error.

Also, the assumed device is /dev/hda1 which ubuntu doesn't use since ages. All disks are now /dev/sda1, doesn't matter IDE or SATA (earlier IDE disks were /dev/hdX).

PS. In the worst case you can always completely remove and reinstall grub2 including all packages. But that would be the last option.

---

### Post by ambre on 2013-03-19
Still fighting with Ubuntu, but making progress, slowly!!!!

My restored system will now boot up.  To make this happen I had to amend /etc/fstab and enter the correct UUID (as supplied by blkid) for both /dev/sda1 and sda5 (Swap partition).  I also had to amend /boot/grub/menu.lst and enter the new UUID for /dev/sda1.

However, I am still not 100% back together.  A lot of the startup processes fail with 'permission denied' errors.  Upon investigation I find that tar has not restored any symbolic links, e.g /usr/bin/awk links to an alternate directory but the restored /usr/bin/awk shows a zero length file with '----------' permissions.

I thought the default action of tar was to create and restore symbolic links!

I used 'tar cvpzf ...' and 'tar xvpzf ...' to create and extract the tarball.

Another little nudge might be all I need.

Thanks

---


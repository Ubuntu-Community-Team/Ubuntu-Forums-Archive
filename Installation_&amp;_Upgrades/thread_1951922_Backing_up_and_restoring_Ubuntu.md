---
title: "Backing up and restoring Ubuntu"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by razedafear on 2012-04-03
Hi 

Is there a way I can backup my Ubuntu 10.10 OS onto a external drive and then restore it like in windows? I have lots of stuff installed on Ubuntu and do not want to re-download all of that. 

Thanks

---

### Post by Mark Phelps on 2012-04-03
There are a number of Linux apps you can use for this, and everyone has their own preferences, but for what you want to do, I would recommend checking out Clonezilla.

Download the ISO file, burn it to CD.  Boot from that and use it to image your Ubuntu install to an external drive.

You can also install Clonezilla on your hard drive so you don't need the CD.  It's a fair amount of work to do that -- read the details at the Clonezilla website for instructions.

Unlike in MS Windows, however, you can't do an image backup while the OS  is running; instead, you will have to boot into Clonezilla to do that.

---

### Post by codemaniac on 2012-04-03
Here are some reads you might find helpful .
[http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895](http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895)
[http://www.linuxlinks.com/article/20090105114152803/Backup.html](http://www.linuxlinks.com/article/20090105114152803/Backup.html)

---

### Post by razedafear on 2012-04-03
> **Mark Phelps said:**
> There are a number of Linux apps you can use for this, and everyone has their own preferences, but for what you want to do, I would recommend checking out Clonezilla.

Download the ISO file, burn it to CD.  Boot from that and use it to image your Ubuntu install to an external drive.

You can also install Clonezilla on your hard drive so you don't need the CD.  It's a fair amount of work to do that -- read the details at the Clonezilla website for instructions.

Unlike in MS Windows, however, you can't do an image backup while the OS  is running; instead, you will have to boot into Clonezilla to do that.

pheww....that is quite a work to do. i'll better reformat. Actually i wanted to test Linux mint 12 using wubi on my separate win partition, however i figured out that wubi does not allow multiple installs, it pops up wubi uninstaller if i choose to install through "mint4win.exe" file in the ISO. Again there is a work around which is too hectic.

[HTML]http://ubuntuforums.org/showthread.php?t=849183

http://ubuntuforums.org/showthread.php?t=1793438[/HTML]

 so i thought i could backup Ubuntu for now and test mint for a while and then may restore it back if i plan to switch.
One more alternative is putting it in VM but i am looking to test all my drivers and hardware for my Hp Probook 4530s, whether it works or not, so that is again ruled out.
see the screen shots.

\m/ thanks for clonezilla, will try that out id i find patience. :)

---

### Post by razedafear on 2012-04-03
> **codemaniac said:**
> Here are some reads you might find helpful .
[http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895](http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895)
[http://www.linuxlinks.com/article/20090105114152803/Backup.html](http://www.linuxlinks.com/article/20090105114152803/Backup.html)

thanks. that is a lot of info there. i'll have to hone down to the best and simple one though

---

### Post by razedafear on 2012-04-03
guys i downloaded this - Source code (Linux): fwbackups-1.43.4.tar.bz2 from here [http://www.diffingo.com/oss/fwbackups/download](http://www.diffingo.com/oss/fwbackups/download)

gave me a tar package, i moved it to desktop, extracted the content and the though terminal cd into the folder, tried to run install-sh in the folder, it says ```
/home/razedafer/Desktop/fwbackups/install-sh: no input file specified.
```

Any idea?

---

### Post by shumifan50 on 2012-04-03
I used to use PING to backup ext3 file systems, but it does not work with ext4 file systems. I tried clonezilla and while it backed up fine it corrupted the restore to a bigger set of disks. So I reverted to using the old reliable tar.
1. Boot the Ubuntu CD and 'try Ubuntu'.
2. ls /dev/sd*(some desktops) or ls /dev/cciss(HP Proliant servers with raid). or ls -l /dev/disk/by-uuid
3. Mount the partitions found in (2).
4. tar each partition to its own file on the backup device.
When restoring:
1. VERY IMPORTANT: cp /boot/grub/* to backup device from target.
2. cp /etc/fstab to backup device from target.
These 2 steps are very important to ensure you cn boot after the restore.
3. Then mount the partitions and untar.

The above will backup/restore Linux and all packages/applictions/settings at the time of the backup. If your Linux gets corrupted, you can re-install from scratch then restore the tarball and you will be back to where you were before. Be careful not to restore to a different version of Linux.
It will allow changing ext3/ext4 and handle al disk size changes.

For the moment I have gone off clonezilla, PING and the like - it has cost me a lot of time.

---

### Post by bcbc on 2012-04-03
If you're using wubi, just back up the \ubuntu\disks directory outside of the \ubuntu directory (which is deleted when you uninstall). Then, when you're done playing, reinstall **the same release to the same drive**, and copy over the contents of \ubuntu\disks before rebooting.

---

### Post by razedafear on 2012-04-04
> **bcbc said:**
> If you're using wubi, just back up the \ubuntu\disks directory outside of the \ubuntu directory (which is deleted when you uninstall). Then, when you're done playing, reinstall **the same release to the same drive**, and copy over the contents of \ubuntu\disks before rebooting.
This Sounds AWESOME \m/ and simple. Hope this works..!

---

### Post by razedafear on 2012-04-04
> **shumifan50 said:**
> I used to use PING to backup ext3 file systems, but it does not work with ext4 file systems. I tried clonezilla and while it backed up fine it corrupted the restore to a bigger set of disks. So I reverted to using the old reliable tar.
1. Boot the Ubuntu CD and 'try Ubuntu'.
2. ls /dev/sd*(some desktops) or ls /dev/cciss(HP Proliant servers with raid). or ls -l /dev/disk/by-uuid
3. Mount the partitions found in (2).
4. tar each partition to its own file on the backup device.
When restoring:
1. VERY IMPORTANT: cp /boot/grub/* to backup device from target.
2. cp /etc/fstab to backup device from target.
These 2 steps are very important to ensure you cn boot after the restore.
3. Then mount the partitions and untar.

The above will backup/restore Linux and all packages/applictions/settings at the time of the backup. If your Linux gets corrupted, you can re-install from scratch then restore the tarball and you will be back to where you were before. Be careful not to restore to a different version of Linux.
It will allow changing ext3/ext4 and handle al disk size changes.

For the moment I have gone off clonezilla, PING and the like - it has cost me a lot of time.
Thanks,I am sure this would work. But I am newbie (2years) in Ubuntu, not vety flair with the command line.

---

### Post by ticket on 2012-04-06
Here's the method I have been using successfully for some time now:

[http://ubuntuforums.org/showthread.php?t=1679827&page=2](http://ubuntuforums.org/showthread.php?t=1679827&page=2)

I backup the OS disc onto a USB stick.  I can boot from the OS stick as well, and restore from it.

Complete backup of the OS takes about 19 minutes using the dd command.

All my data is held on another internal disc, and I use rsync to back that up onto an external USB hard disc.

---


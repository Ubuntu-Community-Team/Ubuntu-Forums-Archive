---
title: "Resizing the boot partition(s)"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by misterPhyrePhox on 2010-04-17
Hi there,

I recently dual booted with Ubuntu and Windows 7 on my new PC. I'm really enjoying the power of Ubuntu and the compatibility of having Windows!! However, I realize now that I allocated too much space for Ubuntu (I use it mostly for programming) and too little space for Windows (gaming takes up more space). I know I can use gparted to resize the partitions, however there's a warning that says if i resize an operating partition, the OS might not work. Can anyone tell me how to resize my partitions (to allocate more space for Windows) and have my operating systems work -- hopefully without having to reformat entirely?

Thanks!

---

### Post by oldfred on 2010-04-17
Moving the start of partitions may change locations of files essential to boot. Often reinstalling grub and checking that UUIDs still match in fstab is all that is required. Make sure you have a working liveCD and good backups just incase.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


List UUIDs:
sudo blkid

Then make sure they match in ( if from liveCD full path will have to include the mount of the root partition.)
gksudo gedit /etc/fstab

---

### Post by Herman on 2010-04-17
:) Resizing a Linux partition from the left, (start point), was once thought to be impossible, but now it can be done with GParted, however, it is an exceedingly slow process.
The last time I tried it, GParted did preserve the file system UUID numbers just fine.

The older way to accomplish something like this was to resize the Linux partition as small as possible, and use GParted to copy and paste it further down the hard drive. Files may need to be removed to allow for shrinking it small enough.

Another idea, (one that I use), is to remove files and resize the operating system as small as possible, then use a dd command to copy the entire operating system to some other disk, as a file. Delete the partition. Then resize the other operating system, create the partition again and dd the operating system back to the smaller partition. Resize to fill the partition. That process will also not change your file system UUID numbers.

It would be a good idea to run a file system check both before and again afterwards. :)

---

### Post by Herman on 2010-04-17
:) As for your Windows 7 partition, you should also run a file system check in it before resizing, no matter what partition editor you plan to use.

Windows 7's own inbuilt partition editor is reported to be useful for resizing Windows partitions, I have tried it our and found it to be very good at that, (although limited in many other respects).

If you decide to use GParted to resize a Windows7 or Vista partition, please remember to remove the check mark from the box for 'align partition on cylinder boundaries', because that's not what you want GParted to do to a Windows 7 or Vista partition.
Removing the checkmark is very simple and only takes a second and will speed the resizing process immensely, because then GParted doesn't think it needs to move the entire partition.
You will also avoid moving the boot sector and consequently the need for boot loader repairs. 

[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]



If you do it right (resizing the partition), you won't need to fix the boot loader in Windows 7.  :)

EDIT: It is normal to run a file system check again in your NTFS partition again after resizing with GParted.
If you don't run one yourself, manually, Windows will run one by itself on boot-up, because GParted sets the 'dirty' flag in the file system to induce a file system check on boot-up.
I like to run CHKDSK /R myself from the DOS command line before booting the OS.
Make sure you run CHKDSK from the same or a compatible version of Windows.

---

### Post by Herman on 2010-04-17
:) The usual warnings about having a backup of your files before using any partition editor still apply, of course. :)

---

### Post by oldfred on 2010-04-18
If you have to move a lot of data with gparted it can take a very long time. 

An alternative. 
When I installed Karmic I kept my Jaunty and created a new /home to move data out of the root partition. I then moved all my data to a separate /data partition. My root now uses about 5GB, my home is about 1GB and everything else is in /data.
So if root only has to be 10-20GB with /home still in it you can shrink your existing install by 20GB and do a new install. Copy over /home data and user settings and if you made any special system settings copy from /etc those settings. You then can totally delete your current install. I might suggest also adding a shared NTFS partition for data that you may want in both like firefox or thunderbird profiles since if using both it is a convience to have the same data in both.

---


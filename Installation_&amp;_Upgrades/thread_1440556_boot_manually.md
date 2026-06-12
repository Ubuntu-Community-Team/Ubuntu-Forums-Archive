---
title: "boot manually"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Linux Lover II on 2010-03-27
Is it possible to boot manually, for example /dev/sda6?


Thanks in advance!

---

### Post by Rocket2DMn on 2010-03-27
What is it that you are trying to achieve?  Is /dev/sda6 another OS installation?  All boot controls are handled through Grub - any existing installs should be available there.  If you are using Karmic (9.10) and it was a fresh install, you can access the Grub menu during boot, right after the BIOS finishes loading by holding down SHIFT.  Available OSes and kernels will be listed.

---

### Post by Linux Lover II on 2010-03-27
It says 'requested unavailable device'...

---

### Post by Rocket2DMn on 2010-03-27
Please be more specific - what is this error? Where did you see it and when? Have you made any changes to your computer recently?  I'm sorry, but you need to provide more information for us to help you - include anything that you think might be relevant.  Thanks.

---

### Post by Linux Lover II on 2010-03-28
> **Rocket2DMn said:**
> Please be more specific - what is this error? Where did you see it and when? Have you made any changes to your computer recently?  I'm sorry, but you need to provide more information for us to help you - include anything that you think might be relevant.  Thanks.

Excuse me!

It's says: error 12, more specifik:

Error 12: Invalid device requested on dev/sda6

Is this more clear?

Thank you very much for your help!

---

### Post by stlsaint on 2010-03-28
What data is suppose to be on that partition.
Ive seen that error before when i had data on a partition but then deleted the data but grub was still configured to boot from info from it.

---

### Post by Linux Lover II on 2010-03-28
> **stlsaint said:**
> What data is suppose to be on that partition.
Ive seen that error before when i had data on a partition but then deleted the data but grub was still configured to boot from info from it.

Supposed to be an ubuntu installation...

---

### Post by Rocket2DMn on 2010-03-28
Is this the only Ubunt installation you have on this computer?  What about other OSes (i.e. are you running a multiboot system)?  Are you able to boot using any of the other kernels listed in the Grub menu?

Finally, have you made any changes to your computer recently, like trying to install a new OS, putting in a new hard drive, or doing any major updates/upgrades?

---

### Post by Linux Lover II on 2010-03-28
Yes I did: I've tried to migrate my wubi installation into a full installation using LVPM, en now he lists netbootkinrev, en ubuntu on dev/sda6, however: the first gives error 15: file not found, the second one gives requested unavailable device (error 12)

Finally my win 7 happened to crash as well, so I recovered everything.

Now I have the original windows boot loader (no longer grub) with win 7 listed, as well as Ubuntu, Ubuntu, and Ubuntu (3 times!).
One is an usb version I installed, the other is the original wubi, however, when boting, they both start up my original wubi.

In short: now I have a working wubi, with lack of place: about 200 mb remaining.

I have a free partition i want to move my wubi install to. Right now, it is ntfs.

How can I solve these problems?


Thank you very much!

---

### Post by Rocket2DMn on 2010-03-28
I don't know if LVPM is still under active development, and may not be compatible with current Ubuntu versions.  Where did you follow instructions from?  BTW, Linux cannot be installed on a NTFS partition, you need to use a native file system, like ext4.

Since your attempt to migrate your partition has already failed once, it may be better if you simply do a fresh install of Ubuntu and move your files and settings over manually.  Most of this simply involves copying over your home directory to the new install.

---

### Post by Linux Lover II on 2010-03-28
> **Rocket2DMn said:**
> I don't know if LVPM is still under active development, and may not be compatible with current Ubuntu versions.  Where did you follow instructions from?  BTW, Linux cannot be installed on a NTFS partition, you need to use a native file system, like ext4.

Since your attempt to migrate your partition has already failed once, it may be better if you simply do a fresh install of Ubuntu and move your files and settings over manually.  Most of this simply involves copying over your home directory to the new install.

How do I perform this fresh install?

No live cd does start?

Thanks!

---

### Post by oldfred on 2010-03-28
I also believe LVPM does not work correctly with new versions. It will copy some data over but does not install grub legacy correctly. It may be repairable but it is better to do a new install and copy /home over.

If you want to know what is where this tool is the best for analyzing boot issues:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Rocket2DMn on 2010-03-28
As I understand it, Grub legacy does not play well (if at all) with the ext4 filesystem, which could be a problem if you are trying to trasnfer over a newer install.  Grub2 is default on Karmic installs (not upgrades).

If you are unable to load a LiveCD, you can install using the Alternate Install CD.  This uses a text based installer rather than a live session, but don't let the scare you away, it is actually quite easy to use.

Get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click "Alternative download options, including Ubuntu installer for Windows", then choose "Text-based installer".  It will have a link to a list of download locations - pick yours, choose Karmic, and scroll down to "Alternate install CD".  Choose either the 32 bit or 64 bit image.  (Geez, it used to be a lot easier to get the alternate cd from the download page...)

---

### Post by Linux Lover II on 2010-03-28
I'll try right now.

I'll let you know if it functioned.


Thanks to all for the great help!

Sorry for my bad English, I'm from Belgium :)

---

### Post by Linux Lover II on 2010-03-28
Can I use this one to boot without a cd drive, but with a virtual drive?
Or can I make a bootable usb with the image?

---

### Post by Rocket2DMn on 2010-03-28
You can burn the image to bootable USB device if you don't have a CD drive.

---

### Post by Linux Lover II on 2010-03-28
> **Rocket2DMn said:**
> You can burn the image to bootable USB device if you don't have a CD drive.

After some 24 hour trying, this finally works like a charm!

You're brilliant!


Another question: can I simply move my existing wubi install (with installed programs and documents) to the newly created OS?


Thanks again!

---

### Post by Linux Lover II on 2010-03-28
> **Linux Lover II said:**
> After some 24 hour trying, this finally works like a charm!

You're brilliant!


Another question: can I simply move my existing wubi install (with installed programs and documents) to the newly created OS?


Thanks again!


Sorry for bumping -- will my 'look' be conserved?

Can I simply copy-paste my 'home' folder and my 'usr' folder?

---

### Post by adam814 on 2010-03-28
Yes, a wubi install can be moved out to a partition if you decide it's really what you want.  It may be more trouble than a fresh install anyway.  A word of caution:  If it's already flaky it could still be just as flaky and you'll have wasted the time of moving it to have to do a clean install anyway.  That having been said if you want to try here's how:

Boot the LiveCD (or LiveUSB as your case may be) and use the "Try without installing" option.  Use GParted (under System > Administration) to make a suitable partition and filesystem to copy your wubi install into (it must be at least as big as your wubi disk and I suggest using ext4 as a filesystem).  Set up a swap partition too.

Now mount your Windows drive.  Mine was /dev/sda1, so this is how I did it:
```
sudo mkdir /windows && sudo mount /dev/sda1 /windows
```Now mount your wubi root.disk like this:
```
sudo mkdir /mnt/wubi && sudo mount -o loop /windows/ubuntu/disks/root.disk /mnt/wubi
```Mount your destination partition wherever you would like, I'll assume it's mounted under "/mnt/dest"
```
sudo rsync -avh /mnt/wubi/ /mnt/dest/
```After that finishes chroot into the copy like this:
```
sudo mount -o bind /dev /mnt/dest/dev && sudo mount -t proc /proc /mnt/dest/proc && sudo chroot /mnt/dest /bin/bash
```Fix your /etc/fstab by changing the "/proc/host/whatever" entries to the UUIDs of the new partitions (i.e. "UUID=ab43-786e", sudo blkid gives you the UUIDS to use).

Now update GRUB2, install it to your MBR, reboot and repeat this step:
```
sudo update-grub && sudo grub-install /dev/sd%
```where % completes your drive name (i.e. /dev/sda).  Get the right one, if you don't you won't be able to boot.

---

### Post by Linux Lover II on 2010-03-29
Right now I have my fresh installed 'basic' ubuntu install.

On my windows drive I have the ubuntu folder with wubi in it, but the one I'd like to have (installed programs etc.)

I can use the commands above to transform my fresh 'basic' ubuntu install into my personalized, wubi, one?
Thanks to all for the answers so far!

---

### Post by oldfred on 2010-03-29
All your settings are hidden files and folders (starting with .) in /home as are all the folders with your files. You can just copy the entire /home over.

Your programs can be listed from the wubi install and reinstalled easily:

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by Linux Lover II on 2010-03-29
> **oldfred said:**
> All your settings are hidden files and folders (starting with .) in /home as are all the folders with your files. You can just copy the entire /home over.

Your programs can be listed from the wubi install and reinstalled easily:

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)


Thanks, in the mean time, I customized my frsh installation again :p

It's beautiful and runs smoothly!

---


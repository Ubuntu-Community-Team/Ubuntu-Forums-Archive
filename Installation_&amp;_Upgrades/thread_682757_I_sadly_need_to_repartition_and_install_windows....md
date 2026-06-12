---
title: "I sadly need to repartition and install windows...but need a little help"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by djuniah on 2008-01-30
Hello, 
    Sadly I had to concede and install windows on my laptop.  I use it for DJing and i just cant get the DJ software i need to run well enough(it needs to be pretty much flawless) in either vmware, virtualbox, or wine.  Also, I need to use visual studio for a video game production class that I am in and for proper testing, I would like to be able to fully boot into windows for graphics reasons.  My problem is that I have my entire drive partitioned for ubuntu and ubuntu only.  Every time i search for a solution for this, i get the opposite.  I need to repartition my ext3 partition and create a small (~10-15GB) NTFS one for windows.  I assume i can just use the resize partition function of GParted to get that done.  
My issue is, once I install windows on that partition, how can i get GRUB back up and working? and also, are there any other special situations I should take note of when doing this?

Thanks for the help,
DJuniah

P.S. I hope you dont think from reading the above that i mean to remove ubuntu, because i dont.  I just need to run 2 apps in windows that I would rather not run in A VM or wine.

---

### Post by hums07 on 2008-01-30
> **djuniah said:**
> 
My issue is, once I install windows on that partition, how can i get GRUB back up and working? and also, are there any other special situations I should take note of when doing this?

Windows will write your MBR during installation but you can easily reinstall grub using the live CD:
```
sudo grub
find /boot/grub/stage1
root (hdx,y)  #change x,y with the result of the above instruction
setup (hdx)   #change x accordingly
quit
```

I hear people say that Windows like to be in the first partition. If that will be the case of your installation, you can fool Windows by mapping the partition where it resides as if it were the first partition. You will have to edit /boot/grub/menu.lst.

---

### Post by djuniah on 2008-01-30
Well, either way I plan on create a full disk image just in case something goes wrong

---

### Post by djuniah on 2008-01-31
Ok ran into an issue already.  I'm all backed up, the partitions are shrunk and moved.  I created an NTFS (primary) partition in the beginning of the drive (physically) and the windows installer cant see the NTFS partition to install in, the only option it gives me is the ubuntu partition (which it is calling C:)  Any idea why it wont see my new partition?

EDIT: tried flagging the partition as boot to see if that was the issue, and it didnt work

It would seem like windows needs to numerically be the first partition on the disk so i would have to change my linux partitions number and then let grub know what happened.  Any idea how to go about doing that?

EDIT2: It appears that grub has the ability to make the windows installer think that the open partition is hd(0,0) even though it is not.  However, I cant seem to figure out how to get grub to load from the install CD.

Basically i would need to make an entry in grub.conf (or menu.lst in this case) that would use the swap command to make it look like hd(0,2) was hd (0,0) and then load from the cd.  Does anyone know how to accomplish this?

---

### Post by logos34 on 2008-01-31
use gparted to delete the ntfs partition you just created.

Try windows install again--create ntfs partition in empty space and specify full format.  Any luck?

---

### Post by djuniah on 2008-02-01
sadly no, that was actually the first thing that I tried.  The install CD wont even show that there is empty space.  

All it shows is one partition (my 130GB linux one)

---

### Post by logos34 on 2008-02-01
It's not reading the partition table correctly.  You could try fixing it with TestDisk.  But be careful.  Might actually be better to just reinstall.  Windows first.

---

### Post by djuniah on 2008-02-02
IS there any way to back up the parition table beforehand? just in case

---

### Post by logos34 on 2008-02-02
dd if=/dev/hdx of=/path/to/image count=1 bs=512

---

### Post by djuniah on 2008-02-02
Ok, i backed it up, erased the partitions, created an NTFS one, installed windows, then was able to use testdisk to restore the linux partitions without having to use my backups whichsaved a lot of time.

BUT, now grub doesent want to install correctly

I do the usual 
root (hd0,1)
setup (hdo)
exit


from the boot disk, and it works.  BUT i keep getting error 17.  So I looked at my menu.lst file on my linux partition and its showing (hd0,0) as the root in each entry.  So i changed all of those to (hd0,1)  and also added an entry for the winXP partition, but when I reboot, the grub menu is unchanged (the winXP one does not show up, and error 17 is still there).  This leads me to believe that its not pulling the menu.lst file from my ubuntu partition.  Any idea why this might be?  (I even tried looking at the windows partition to see if it somehow magically put it there, but it all looked normal)

EDIT: I even tried the super grub disk, and it gave the same results

EDIT2: just for the heck of it, i tried editing it again and it seems to have stuck this time!  Testing the different boot options now

Here are the tasty bits of my menu.lst
> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1f4ae0a6-cb5f-4ef9-ba3d-344a9ab9cafa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1f4ae0a6-cb5f-4ef9-ba3d-344a9ab9cafa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1f4ae0a6-cb5f-4ef9-ba3d-344a9ab9cafa ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1f4ae0a6-cb5f-4ef9-ba3d-344a9ab9cafa ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,0)
makeactive
chainloader +1
quiet


EDIT3: Ubuntu runs like a charm, but when I tested XP I got a BSOD with an UNMOUNTABLE_BOOT_VOLUME error.  I saw somewhere that chkdsk /r from an XP recovery CD may fix it. so i'm going to try that.  If anyone else has any ideas,please let me know

EDIT4: chkdsk /r didnt work,  It said it was unrecoverable.  Also, i tried to see if i could just reinstall windows, but once again, the windows install CD only sees my linux partition and not the NTFS one at (hd0,0)

EDIT5:  tried fixboot from the windows disk.  Got the error: FIXBOOT cannot find the system drive, or the drive specified is not valid

---

### Post by logos34 on 2008-02-02
I'd wipe the whole freaking drive with [Darik's Boot 'n nuke]("http://dban.sourceforge.net/"), then reinstall everything.

---

### Post by djuniah on 2008-02-02
I may end up having to do that, thanks for all the help so far

---

### Post by djuniah on 2008-02-03
I'm so close now!!!

I removed the linux partitions again using gparted (which left just the NTFS one) and suddenly windows would boot just fine!  So instead this time, i repartitioned from within windows using partition magic.  Turns out that did the trick, windows boots, and i had my ext3 and swap partitions made.  I restored all the data to the ext3 partition, and updated the fstab file.  Both OS's now boot from grub, but ubuntu hangs at hte loading screen.

I assume this is due to the fact that /dev still thinks that hda1-3 exist, when in fact it should be hda5 for the root and hda6 for swap.  How can i either reassign or rebuild my hda entries in /dev.

edit, i'm trying to use MAKEDEV via the liveCD and it seems to have worked, but it put the devices in /dev/.static/dev.  i cant just cp the hda5 over to /dev/ because that would create an image of the drive.  how should i go about moving that?

---

### Post by cliaz on 2008-03-13
I'm trying to do the same thing, so a quick rehash of what appears to work...


Format disk
Install windows
Using Partition Magic, create another partition for Ubuntu.

I'm trying to install ubunto to said 'other' partition, will that work?
Or do I have to create a ext3 partition and a swap partition and image the data back across, like you did.

I'm just starting out with linux so go easy on me :P
-cliaz

---


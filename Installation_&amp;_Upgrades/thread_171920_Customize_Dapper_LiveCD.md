---
title: "Customize Dapper LiveCD?"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by palco on 2006-05-07
There is a good wiki on Hoary and Breezy CD Customization. Does any one know if there is a wiki of howto on customizing Dapper LiveCD? The filesystem or rather to say the archiving method for Dapper LiveCD is different to Hoary and to Breezy. something called squasgfs. I found squashfs-tools in repositories. Has any one used those. Any one made a custom Ubuntu 6.06 Dapper LiveCD? Any one tried? 
PLS give me any idea

---

### Post by BDembroski on 2006-05-31
I found this with a quick google:

[http://files.akl.lt/Linux/Ubuntu/custom-dapper-livecd.htm](http://files.akl.lt/Linux/Ubuntu/custom-dapper-livecd.htm)

I don't know how well it works, but it should be a start...

---

### Post by palco on 2006-05-31
Thank you, BDembroski. 
That is a good start and that is good news also, as I know someone customized it before. That's goood news. 
I already did a similar thing, some different, but same concept. Unfortunatly it didn't come out as a working system/CD. I was able to boot of it into the welcome screen of the CD. Then it started booting the system, you know, that beutiful uspalsh sceen, listing things it was doing, came to 'Configuring X' point.

And here out of nowhere it listed something like "Disabling update-notifier" and hang up at that point! I never saw it listed in the boot of the orignal CD. Most strange thing! 

I decided it was due to my customization. So I did all that again (uncompressed the squashfs.filesystem > compressed it back > put it into the iso > burnt to a CD) and booted of it. Same "Disabling update-notifier" thing! 
I wonder if any options should be added when compressing the folder, or what?! 

Here is what I did.

1.I burnt the LiveCD image to a CD
2.Booted from it
3.Formated my pendrive with casper-rw label (that didn't go on 6.06 beta since Gparted couldn't unmount it ever, but on 5.10 it went smoothly)
4.Rebooted with 'persistent' parameter and pendrive plugged
5.Customized desktop and installed some packages.
6.Rebooted (without persistance) and installed the system
7.Booted into installed system
8.Plugged the pendrive, copied the contents and cleaned it some
9.Mounted the CD
10.Mounted the the filesystem.squashfs file from CD to a folder in /media/ with command &sudo mount -t squashfs /media/cdrom0/casper/filesystem.squashfs /media/HDD1 -o loop
11.Copied the contents of the  filesystem.squashfs (everything that was in /media/HDD1) to  folder /media/HDD3/org
12.Copied contents of casper-rw pendrive into the same folder, replacing some files
13.Compressed the folder to a squashfs file with command &sudo mksquashfs /media/HDD3/org /media/HDD3/filesystem

        palco@palco-desktop:~$ sudo mksquashfs /media/HDD3/org /media/HDD3/filesystem
        Password:
        Creating little endian 2.1 filesystem on /media/HDD3/filesystem, block size 6553 6.
        .
           0 MB .......... .......... .......... .......... .......... ..........
          60 MB .......... .......... .......... .......... .......... ..........
         120 MB .......... .......... .......... .......... .......... ..........
         180 MB .......... .......... .......... .......... .......... ..........
         240 MB .......... .......... .......... .......... .......... ..........
         300 MB .......... .......... .......... .......... .......... ..........
         360 MB .......... .......... .......... .......... .......... ..........
         420 MB .......... .......... .......... .......... .......... ..........
         480 MB .......... .......... .......... .......... .......... ..........
         540 MB .......... .......... .......... .......... ......
        Little endian filesystem, data block size 65536, compressed data, compressed met adata, compressed fragments
        Filesystem size 602477.31 Kbytes (588.36 Mbytes)
                36.91% of uncompressed filesystem size (1632128.17 Kbytes)
        Inode table size 681197 bytes (665.23 Kbytes)
                33.31% of uncompressed inode table size (2045120 bytes)
        Directory table size 623623 bytes (609.01 Kbytes)
                40.85% of uncompressed directory table size (1526623 bytes)
        Number of duplicate files found 7926
        Number of inodes 82606
        Number of files 69181
        Number of fragments 8028
        Number of symbolic links  6419
        Number of device nodes 0
        Number of fifo nodes 0
        Number of socket nodes 0
        Number of directories 7006
        Number of uids 2
                root (0)
                unknown (999)
        Number of gids 2
                dhcp (101)
                lpadmin (106)
        palco@palco-desktop:~$


14.Renamed the file to filesystem.squashfs
15.Booted to Windows (I know same to me)
16.Customized the original LiveCD iso image to replace the original filesystem.squashfs file with mine
17.Burnt the iso to a CD
18.Booted of it
19.Everything was going ok (cept for the first boot window to become a bid slower loading, not too much) until it got to 'Disabling update-notifier' point. I never saw this part of boot process when booting from original CD. It actially never listed any other activities after 'Configuring X'. When now it showed some other 5 items after 'Configuring X' till it was getting to 'Disabling update-notifier' and hang up at that point.

20.I thought the bug was due to using a windows application to modify iso. So I made two copied of the iso, and copied the filesystem.squashfs file from one to other. Most simple modification to iso I could think of. Burnt the image to CD. Booted up from it. It worked. A little slower, but worked.

21.To make sure it is not my customization that is causing this, I booted into installed Ubuntu 6.06 and did same things as in the first place, but customized the extracted contents of the filesystem.squashfs file. So I didn't change it. Just mounted filesystem.squashfs file, copied files of it to a folder, ran &sudo mksquashfs /media/HDD3/org /media/HDD3/filesystem and put it back into the iso. Booted of it. It booted till 'Disabling update-notifier' and hang.

22.I tried the same compressing it with -2.0 parameter (as I do not know which version you use). Same thing.

---


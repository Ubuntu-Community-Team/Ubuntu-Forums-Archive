---
title: "Installation Fails!"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Caepio on 2006-08-16
I am just starting with Ubuntu. My laptop had W2k and was not running well. My idea was to install Ubuntu over the W2k (erasing and overwriting the W2k system). Didn't work - Linux - 386 "broke". Now I get a question mark on an otherwise black screen.

Perhaps foolishly, I tried to restore W2k, and it failed. Now I have neither system.

Ideally, I'd like to reformat the hard drive and try a fresh install of Ubuntu, but I cannot get a command screen or any DOS.

Any ideas greatfully accepted!

---

### Post by zxee on 2006-08-16
Probably providing some of your system specs will help. Also please be as specific as possible when describing a problem. "broke" doesn't convey a lot or give us anything to work with.
Ok-so what version of ubuntu did you try to install? If you have less than 256MB ram you may want to try the alternate cd-not the desktop. 
If you couldn't get the win restore disk to work is your cd rom having read problems?

---

### Post by ocusa on 2006-08-17
Ok, there is a very simple solution to get back to a dos prompt. 

First, go into your bios and set your first boot device to your floppy disk. To get into the bios depends on your brand of laptop, but is usually one of the F keys (F1, F2, F3...).

Download a windows 98 boot disk downloadable from [http://1gighost.net/dalehollow/boot98c.exe]("http://1gighost.net/dalehollow/boot98c.exe")

Run the file to extract the bootdisk onto your floppy disk. 

Stick the disk in your laptop, and switch it on.

This disk should get you back to a dos prompt. From there you can reformat your disk, by typing "format c:".

If you dont have the floppy disk, search google for a bootdisk cd. I've used a cd to boot to dos before, but its been over a year. If you can't find a free one, I can dig it out from my piles of rubbish cds.

---

### Post by ocusa on 2006-08-17
Once the format is complete remember to switch your bios back to having the cd-rom the first boot device. 

At this stage you can try to install Ubuntu again.

---

### Post by carontis on 2006-08-17
erased

---

### Post by carontis on 2006-08-17
Look at this: before installing any kind of OS, it's better if you format your hdd in low level mode, 'cause this will prevent every kind of error in the disk. You can use LLW.EXE (in windows) or Autoclave (in Linux). I think Autoclave is the better one, 'cause it erases all tables, but remember it will take a lot of time depending form the size of your hdd. After done you will have only to put you distro CD without going in the BIOS for changing boot order. This is the way I use always for not having troubles after or during installation, expecially 'cause the known NORTON (in windows) make some bad scaling in hdd and it's not enough the simple formatting. Try this way and let know.

bye

---

### Post by Caepio on 2006-08-17
Hey

I am totally overwhelmed by the help! Thank you all. I have now corrected the problem, and will apply your advice in future posts.

Thanks again!

---

### Post by ocusa on 2006-08-19
Can you tell us how you solved the problem?

---

### Post by Caepio on 2006-08-20
I wrote too soon. What I managed to do was to reformat and reinstall Windows 2000. The hard drive (20 GB) has been partitioned.

I tried again to load Ubuntu from the CD provided in the book I bought, and it failed again and again. It fails when it gets to the 'packages' part of the install. Then I get various errors. I tired to have the system check the integrity of the CD and it failed the test (the test is provided on the install CD), but the CD is new and has no marks or scratches.

My next try will be to download Ubuntu from this site, burn it to a CD, and then try again.

Gosh. I never thought it would be this difficult.

---

### Post by Jonie on 2006-08-20
You can clean the part of the disk, on which you want to install ubuntu. Boot linux off the cd into text mode, list your partitions f.ex. with parted

using /dev/hda
(parted)

type print

you'll something like this:

Disk geometry for /dev/hda: 0kB - ...
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    11GB    11GB    primary   ext2
2       11GB    11GB    403MB   primary   linux-swap
3       11GB    15GB    4294MB  primary   ntfs         boot
...

the one formatted with ext2 or ext3 will be the one of ubuntu.

notice the number,
quit parted and issue the command:

dd if=/dev/zero of=/dev/hdaX where X is the number of ubuntu partition.

If there is an error on disk, dd will complain with errors.

---

### Post by Caepio on 2006-08-30
OK, I tore down the laptop and reformatted the hrd drive. I succesfully installed Win2k, and that works fine.

Some have suggested that there is a bug in the 6.06 install which is corrected in version 6.06.1.

Before I tear up the computer one more time, can anyone confirm that a) this install works, and b) my laptop can boot from a *.iso file? That's the format of the new install CD.

Thanks.

---


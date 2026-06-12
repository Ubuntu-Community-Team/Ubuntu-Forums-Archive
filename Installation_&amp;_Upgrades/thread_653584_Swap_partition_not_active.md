---
title: "Swap partition not active"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by taseedorf on 2007-12-30
Hi all, got a pretty simple question...
Scenario - So I first installed Mandrake a long time ago, but it was annoying and hard to work with when I was young (like 14)....so after a long time of no Linux, I finally installed Ubuntu again.  My partition tables began Ubuntu, than the swap for Linux, than windows.
I deleted the windows partition because I loved Ubuntu so much, and was stuck with a bunch of un-used space.  I had to delete my swap partition so I could expand my Linux partition to use the newly freed space.  I than set up an extended partition, with a Linux swap space inside of it.  Roughly 3 gigs or so.  Trouble is, when I look at it with QT parted, it says none of it is in use and I don't believe it is on.  I used the QT parted boot disc to turn swap on, however I believe that is only a temporary fix.  I than edited the /etc/fstab file, but I don't believe it is working to keep that swap partition on.  it currently looks like this

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=b638028f-a0cf-4d00-a102-e8b3244c79a6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=5C049A3F049A1BD8 /media/hda2 ntfs defaults,umask=007,gid=46 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=c8ec6222-4246-979c-75a1-7094d0723b9f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
# my entry for swap partition
/dev/hda5              swap                    swap    defaults        0 0

Can anyone tell me what I'm doing wrong or what I need to change in the above file? Or if I can delete any of it?

Also, NONE of the partitions are active.  At least, QT parted says they aren't.  Does this matter? Will it affect anything if I make my Ubuntu partition active?  Thanks in advance guys!

---

### Post by PmDematagoda on 2007-12-30
Could you post the output of:-
```
sudo fdisk -l
```

---

### Post by taseedorf on 2007-12-30
this is what i got
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11728    94205128+  83  Linux
/dev/hda2           11729       12161     3478072+   5  Extended
/dev/hda5           11729       12161     3478041   82  Linux swap / Solaris
taseedorf@taseedorf-laptop:~$ 


I believe it is working now? I gave the command 'free' and it changed to show
           total       used       free     shared    buffers     cached
Mem:        904308     489984     414324          0      15764     252500
-/+ buffers/cache:     221720     682588
Swap:      3478032          0    3478032
taseedorf@taseedorf-laptop:~$ 

is that correct?

---

### Post by PmDematagoda on 2007-12-30
According to your fdisk -l output, this is what the fstab file should look like:-
```

# Entry for /dev/hda1 :
UUID=b638028f-a0cf-4d00-a102-e8b3244c79a6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5
[COLOR="Red"]**/dev/hda5 none swap sw 0 0**[/COLOR]
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
# my entry for swap partition
/dev/hda5 swap swap defaults 0 0
```

Edit your fstab file this way and see if that solves your problem.

---


---
title: "disk space requirements"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by Tonglebeak on 2005-06-17
How big should a partition for ubuntu? Unfortunately, all I got right now is 2.75 gigs left (should be able to free up more).

Another question: can ubuntu read from the windows partition, so I can transfer files and music?

---

### Post by Xian on 2005-06-17
2.75G is a little on the short end but you could probably do a minimal (maybe Xfce4 DE only) install onto that partition. You can read/write to your Windows directory if it is a FAT filesystem and read-only if it is NTFS, save that you might try some external applications that would possibly allow you to do this.

---

### Post by Tonglebeak on 2005-06-17
So basically, I can always copy files from win to linux, but not write to from linux to win if it's ntfs? Thanks.

---

### Post by Xian on 2005-06-17
With a default install you can do the following while logged into a Linux session:

* Read Windows Files
* Copy Windows Files To Linux 

You can not:

* Write Files to Windows
* Copy files to Windows

---

### Post by Tonglebeak on 2005-06-17
Cool. One more question before I forget:

When I once installed Mandrake Linux about a year ago (and I had to uninstall thanks to parents), I was given the mandrake bootloader, and had to end up reinstalling the windows bootloader after mandrake was uninstalled.

Is there anyway to keep the windows bootloader default, and to have it automatically boot windows unless there is some sort of key input to say otherwise to boot linux?

---

### Post by Xian on 2005-06-17
[QUOTE=Tonglebeak]Is there anyway to keep the windows bootloader default, and to have it automatically boot windows unless there is some sort of key input to say otherwise to boot linux?[/QUOTE]
Yes, you can boot into Linux by using the Windows MBR.
It is a more complex procedure and I've never cared do it.

Google around or search in here and you'll turn up the guidelines.

---

### Post by bloodpuppy on 2005-06-17
How do you view the windows partition? I haven't been able to figure that out. I've checked in places -> computer, but that only shows my linux partition, my floppy, and my CD and DVD drive.

and how come I only see one linux partition, I set up 3; /, /home and swap, I understand I won't see swap, but shouldn't / and /home be shown as separate partitions?

---

### Post by Xian on 2005-06-17
[QUOTE=bloodpuppy]How do you view the windows partition? I haven't been able to figure that out. I've checked in places -> computer, but that only shows my linux partition, my floppy, and my CD and DVD drive.

and how come I only see one linux partition, I set up 3; /, /home and swap, I understand I won't see swap, but shouldn't / and /home be shown as separate partitions?[/QUOTE]
You should be able to see /home mounted if it was done on a separate partition. Issue the command below to view all your mounted directories:

```
 $ mount
```

As for you your windows issue, my first thought is that it is not set up properly in your /etc/fstab file. You might want to post that and also let us know what filesystem it uses, as well as what partition is it located on (e.g., /dev/hda1).

---

### Post by bloodpuppy on 2005-06-17
[QUOTE=Xian]
As for you your windows issue, my first thought is that it is not set up properly in your /etc/fstab file. You might want to post that and also let us know what filesystem it uses, as well as what partition is it located on (e.g., /dev/hda1).[/QUOTE]


my windows partition is NTFS, in /dev/hda1
this is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Xian on 2005-06-17
[QUOTE=bloodpuppy]my windows partition is NTFS, in /dev/hda1[/QUOTE]
Enter what is listed below from a terminal.

```
$ sudo mkdir /ntfs
# sudo echo "/dev/hda1    /ntfs     ntfs    ro,users,gid=users,umask=0002,nls=utf8 0 0" >> /etc/fstab
$ sudo mount /ntfs
```
Edit: Your Windows partition will now be mounted in the /ntfs folder. You can change this anytime you want by just re-editing the fstab file and creating a new directory.

.

---

### Post by bloodpuppy on 2005-06-17
Thanks. that got it working.  \\:D/ 

I hope you don't mind, I have some more questions.  O:) 

I understand the first and last comand, but what was that echo comand?

if i do change the directory, will I have to unmount /ntfs first? and if I unmount /ntfs, will I still have the HD icon that was created in places -> computer?

---

### Post by Xian on 2005-06-17
[QUOTE=bloodpuppy]Thanks. that got it working.  \\:D/ 

I hope you don't mind, I have some more questions.  O:) 

I understand the first and last comand, but what was that echo comand?

if i do change the directory, will I have to unmount /ntfs first? and if I unmount /ntfs, will I still have the HD icon that was created in places -> computer?[/QUOTE]

The 'echo' command with '>>' appends a given file.

Yes, unmount ntfs first with '$ sudo umount /ntfs' and then make changes. 
You will need to use a text editor this time and create a new directory.
The HD icon will appear again when remounted.

```
$ sudo mkdir  <your_choice>
$ sudo gedit /etc/fstab
```

---

### Post by bloodpuppy on 2005-06-18
Wow, you know a lot about linux. Thanks for the help.  :grin:

---


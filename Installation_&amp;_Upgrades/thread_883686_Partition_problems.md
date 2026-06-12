---
title: "Partition problems"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by hofa on 2008-08-08
I have a weird thing going on with my partition size.

So I have a dualboot setup with windows, data, ubuntu and swap partitions (in that order)

A while ago I shrunk my data partition and gave the remaining space to mu Ubuntu partition. It's only just now that I found out that Ubuntu acts like it never happend.

I think I used gparted on a SysRescCd to resize my partitions

This is what ubuntu tells me
```
hofa@hofalaptop:~$ df -h /dev/sda1 /dev/sda2 /dev/sda3
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              69G   35G   34G  51% /media/windows
/dev/sda2              62G   20G   42G  32% /media/data
/dev/sda3              11G  4.9G  5.7G  47% /
```

This is what parted tells me
```
(parted) print                                                            

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  73.0GB  73.0GB  primary   ntfs         boot  (edit: /dev/sda1)
 2      73.0GB  139GB   65.7GB  primary   ntfs              (edit: /dev/sda2)
 3      139GB   159GB   20.3GB  primary   ext3              (edit: /dev/sda3)
 4      159GB   160GB   1020MB  extended               lba  
 5      159GB   160GB   1020MB  logical   linux-swap   
```

Can anyone tell me how I can get Ubuntu to recognize the new size of my paritions?

---

### Post by Herman on 2008-08-08
[What to do if your file system doesn't fit your partition]("http://users.bigpond.net.au/hermanzone/p10.htm#What_to_do_if_your_file_system_doesnt")

Boot your Ubuntu Live CD and open a terminal and,
```
resize2fs -p /dev/sda3
```Try that and see if it helps. :)

---

### Post by hofa on 2008-08-08
I saw your response, read it and thought to myself: "Allrighty I can fix it!".
I rebooted to a sysresccd and when I got to the prompt I realised that I didn't memorize or wrote down the command 

Had to boot up my gf's computer to come back here :-D

But it worked, Thanks!

---

### Post by Herman on 2008-08-08
:) Oh, okay good! Thank you for the feedback.
Sometimes the partition is resized, but the file system which lives inside the partition did not get resized for some reason. 
Some software, like the df -h command looks at the file system size, while other software, like Parted, looks at the size of the partition.

In the olden days, (so I am told), people used to use software (command line) for creating and resizing partitions, and then more (command line) software for creating or resizing the file systems inside their partitions. Everyone was used to using commands like mke2fs, e2fsck, resize2fs.
These days we are all soft and spoiled, we expect our hard disk partition editing software to do everything automatically, and normally it does. :)
Something must have gone wrong, but it's fixed now so that's okay.

More commonly this type of thing happens after restoring a file system from a backup with a 'dd' command or from a Partimage backup, it's a good idea to run resize2fs at times like that too.

Regards, Herman :)

---


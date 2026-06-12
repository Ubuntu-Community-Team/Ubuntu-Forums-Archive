---
title: "Dual boot partition size"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by 9x21 on 2010-02-18
First of all, excuse me for my bad english, but it is not my native language.

I must say that until now I have worked with Win2000/Xp. Long time ago I worked with Xenix and in the last 2 month sometimes with Ubuntu.

Now I have brought a new PC with 320Gb HD and 4 Gb RAM, and I wish to built a dual boot system, with Win7 and Ubuntu.

After doing some search on google and see some partitions scheme, I have thought the following schema:

[FONT=Courier New][SIZE=2][FONT=Lucida Console][SIZE=1]
[FONT=Courier New] ===================================================================================================
[SIZE=2] Primary part. 1:
[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New] Linux /boot, size 500 Mb, type   ext3     [/FONT][/FONT][/SIZE][/FONT][SIZE=2]
[/SIZE][/INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New] Primary part. 2         :
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New] Win7 disk C:\, size 80 Gb, type      NTFS; for OS and Win programs

[/FONT][/FONT][/SIZE][/FONT][/INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New] Primary part. 3         :
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]Reserved                 500 Mb      ext3; reserved for future /boot of another distro.

[/FONT][/FONT][/SIZE][/FONT][/INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New] Extended partition:
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]Logical part. 1:
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]Win7 disk E:\, size 60 Gb     , type NTFS;  Only data ( D:\ is CD )
[/FONT][/FONT][/SIZE][/FONT][/INDENT][SIZE=2]Logical part. 2:
[/SIZE][INDENT][SIZE=2]Space reserved       63 Gb                Reserved for E:\ or \home increment or another distro.

[/SIZE][/INDENT][SIZE=2]Logical part. 3:
[/SIZE][INDENT][SIZE=2]Linux /home            , size 60 Gb, type ext3     ; Only data ( and /usr/locale )

[/SIZE][/INDENT][/INDENT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]    Logical part. 4:
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]LVM volume, size 60 Gb so initially subdivided:[/FONT][/FONT][/SIZE][/FONT][SIZE=2] / 30 Gb, /tmp 15 Gb,  /var 15 Gb
[/SIZE][/INDENT][/INDENT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][FONT=Courier New]Logical part. 5:
[/FONT][/FONT][/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=2][FONT=Lucida Console][SIZE=1][FONT=Courier New][SIZE=2] /swap, size 6 Gb    , type: swap[/SIZE][/FONT] [/SIZE][/FONT][/SIZE][/FONT]
[/INDENT][/INDENT][FONT=Courier New][SIZE=2] 
[/SIZE][/FONT]
Note:
1) /boot is the first, so if I need to increment C:\, I have to move only E:\ and partition 3
2) Partition 3 may be user for another linux distro
3) About swap: I have followed the Red Hat rule ( if ram >= 4Gb then swap = 2 + RAM;
4) About /home: I want a partition that I can backup with an utility like Norton Ghost for example.
5) About /, /tmp, /var: I want separate the temporary files from real OS files. LVM should give me the
   possibility of change the partitions size when I will have more experience.


Can it work ?

What do you think about ?

Any suggestion will be highly appreciated.


Best regards,
Simone

---

### Post by oldfred on 2010-02-18
Today desktops do not need nor normally require separate partitions for system folders. Servers with defined application use may need separte partitions. Only older computers with BIOS limits need the /boot at the beginning of the drive.
.
If you are thinking of multibooting separate /boot and separate /home can create problems. Then you may want separate /grub and /data. From a grub partition you can boot anything. /data can be mounted into any system to share data, but /home is unique to each install.

Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by Herman on 2010-02-18
:D I agree with oldfred.

**For a personal laptop or desktop computer**, in my opinion it's much better to install in one large partition for everything. Some people like a separate /home.
Be aware that you will still need to keep a separate backup of your files even if you do have a separate /home partition. I prefer not to have any separate partitions at all, not even for swap, I use [dynamic swap space manager]("http://pqxx.org/development/swapspace/") instead, (just install it from the Ubuntu Software Center).
Advantages of installing in one big partition with directories for /bin / boot  /dev  /etc  /home  /lib  /lost+found  /media / mnt  /opt  /proc /root  /sbin  /selinux  /srv  /sys  /tmp  /usr  and /var,

[LIST]
[*]each directory is always as large as it needs to be - no need to resize with a partition editor if one directory grows too big
[*]no need for careful planning of partition sizes in advance before installing, everything will be okay
[*]no partition editing required each time a directory grows or shrinks, it takes care of itself automatically
[*]only one file system to take care of, you only need to run e2fsck once a month or so
[*]less complicated, less to go wrong, easier to fix if something does happen
[*]besides, you will have a backup made, and you just need to make one backup
[*]faster, simpler installation process
[*]one file system - one file system overhead - less wasted disk space
[*]only one file system to load at boot time - faster boot times
[/LIST]
**For a personal desktop computer - if multiple booting more then one Ubuntu or other GNU/Linux distro, **Advantages of installing with separate /home partition,

[LIST]
[*]You can save disk space by sharing the same /home (very convenient too),  and maybe the same swap area(s), (as long as you aren't planning on hibernating).
[/LIST]
 **For a computer you plan to share with other users, such as a**** server,** especially if you suspect that some of the other users may not be completely trustworthy.
Advantages of installing with separate partitions for each directory like /root /home /tmp /var and all the rest,

[LIST]
[*]if you can only get say 4GB hard disks or something like that you still install an operating system in a computer and use three or four small hard disks with one or two partitions on each one. That would have been useful in the old days when most people could not buy very big hard disks, but now we can buy 1 or 2 TB size hard disks
[*]you can arrange your partitions physically on the hard disk so the busiest ones are towards the outside circumference for faster reads and write speeds - especially effective with todays larger capacity HDDs see -[Short Stroking]("http://www.tomshardware.com/reviews/short-stroking-hdd,2157.html").
[*]useful for servers, especially in the old days when they used Unix in big old mainframe computers with a lot of users in a University campus or somewhere like that. May be useful even in these modern times for servers where they are anticipating the possibility of malicious users who might attack one directory and fill it up with large files to try to bring the system down - see [The Importance of Linux Partitions]("http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html") - Nixcraft.
[*]Different file systems can be used in different partitions and mounted with different file system options, eg. reiserfs is supposed to be faster for lots of small writes than other file systems, choose journaling or no journaling, encrypted or not-encrypted, etc.
[*]supposed to be easier to recover from a catastrophe of some kind by restoring one just one or two affected partitions, (presumably from a dd backup I suppose). In order to make it recoverable you will probably need to go to the work of making and keeping frequent backups of every partition in case something happens to one of them to avoid the need to re-install the entire system. That would have been important in the old days when hard disks\ technology was not so far advanced and hard disks were flaky compared with the hard disks we have now. Actually it only takes half an hour or so to perform a complete re-install nowadays since we have CD installers instead of tapes or punch cards. (We don't have to type the operating system in by hand or anything like that).
[*]You can learn how to maintain a complex system in case you decide to become a professional sys-admin some day in charge of complex equipment - practice borking your own system and getting it fixed again in the least possible time.
[*]If you use LVM you can resize your partitions easily as required and do other cool tricks like taking snapshots and more - requires slightly more advanced learning.
[/LIST]
 If you are really installing a server and you do insist on dividing your installation up into a lot of different partitions then I suggest you try using a Ubuntu 'alternate installation' CD and perform an LVM installation. With LVM you can take snapshots of your file systems and restore from the snapshots if things go wrong, you can resize your volumes when you need to and even replace a disk without shutting the system down, (useful for servers).
You will need to be willing to spend more time than the average user reading and learning how to install and then how to administer such an operating system.

---

### Post by 9x21 on 2010-02-19
Thanks to all have replied.

Bye
Simone

---


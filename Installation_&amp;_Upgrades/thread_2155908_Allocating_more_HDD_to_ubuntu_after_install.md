---
title: "Allocating more HDD to ubuntu after install"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by iamtheforger on 2013-06-19
Hello, this is about the fourth install of ubuntu ive had, never had any problems like this before, but while tring to speed through the installation of 13.04 I fuged up and only allowed around 8gigs for storage from my terrabyte I have I only realized this when I started to do alot on my computer. I do not want to have to delete ubuntu and reinstall because that would be a pain. Is there any way to transfer space? Thanks in advance :D

---

### Post by cincinnatus13 on 2013-06-19
Well, if you install Gparted, you can mess with the surrounding partitions.
Shrink the one next to it and then lengthen whatever one you want to lengthen.

Warning- this has the possibility of deleting your data on whatever you are shrinking so be sure to have a backup just in case.

---

### Post by oldfred on 2013-06-19
May be best to post screenshot from gparted (use go advanced and click on paperclip icon) or this:
       sudo parted /dev/sda unit s print

You cannot use gparted on mounted partitions, but need to use Ubuntu live installer or a separate liveCD with gparted. Even then you often have to click on swap and right click swap off as liveCD like to use swap to speed things up.

      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

      
 Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)


 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by iamtheforger on 2013-06-23
[IMG]http://i.imgur.com/bNQGWZw.png[/IMG]
here is the pic of the terminal I after entering that command, hope this helps

---

### Post by oldfred on 2013-06-23
Better just to post text rather than screen shot. Use screen shots for gui apps like gparted. You can also put text into code tags, use Go Advanced editor and click on # to enclose highlighted text in code tags automatically.

What is in sda5 and can you shrink it? I do not like moving partitions left, but you can, it just takes longer and any power failure corrupts partitions as it has to copy it sector by sector and if half copied it is damaged. Best to have good backups. But it normally works. In fact the only time it does not work is the one time you are in a hurry and do not do the backups. :)

Otherwise where due you have extra space? It may then be the old slide puzzle of moving things around to make space.

---

### Post by iamtheforger on 2013-06-23
```
matt@matt-Lenovo-V570:~$ sudo parted /dev/sda unit s print
[sudo] password for matt: 
Model: ATA WDC WD7500BPVT-2 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        411647s      409600s      primary   ntfs            boot
 2      411648s      1373401087s  1372989440s  primary   ntfs
 3      1373403134s  1434222591s  60819458s    extended                  lba
 5      1373403136s  1404329743s  30926608s    logical   ntfs
 6      1404329984s  1421815807s  17485824s    logical   ext4
 7      1421817856s  1434222591s  12404736s    logical   linux-swap(v1)
 4      1434222592s  1465149167s  30926576s    primary   ntfs            diag

matt@matt-Lenovo-V570:~$ 

[CODE]
```[/CODE]

---

### Post by oldfred on 2013-06-23
Either screen shot of gparted as it also shows an approximation of use or click on all your partitions to mount them as this command only shows mounted partitions.
df -h

And then where are you taking space from?

---

### Post by iamtheforger on 2013-07-02
Either my C drive or the D
Either one [IMG][Imgur]([http://i.imgur.com/uuqkD1i](http://i.imgur.com/uuqkD1i))[/IMG]
which ever partiton you think would be the best one

---

### Post by oldfred on 2013-07-02
Gparted did not mount your sda2, shows red icon. Is it hibernated or needs chkdsk? So cannot see how much room you have. Windows needs 30% free space to run well. At 10% it become very slow.

Bit difficult as you have to move several partitions around and that adds risk. Any power failure during partition editing or moving corrupts data. Usually it works but the one time you do not have a backup is the time power goes out. So good backups are important. 

If you have space in sda2 you can shrink it with Windows disk tools and reboot so Windows can run chkdsk and make other repairs.
Then with gparted from a liveDVD/Flash so all partitions are unmounted & you may have to click on swap and right click swap off as live installer likes to use swap to speed things up.
You can then move extended partition into the unallocated. move sda5 left & then move sda6 left, finally expand sda6. I prefer to not queue tasks but run each to make sure it works. The more data you have to move the longer it takes, but do not interrupt or that is the same as a power failure & corrupts data.

---

### Post by iamtheforger on 2013-07-02
I think it might just be easier to uninstall and reinstall with more space lol

---


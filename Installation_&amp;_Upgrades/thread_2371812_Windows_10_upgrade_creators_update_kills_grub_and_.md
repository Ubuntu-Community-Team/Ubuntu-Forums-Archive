---
title: "Windows 10 upgrade creators update kills grub and boot-repair info (EFI bios)"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by stevepates on 2017-09-19
i have a 16.04.03 installation of ubuntu, along a win 10 dual boot.

I tried to upgrade to the latest creators update, since win 10 was having issues. Suddenly, the pc restarted, and then i got into a grub rescue screen,


tried with boot repair, 

but no luck.

[http://paste.ubuntu.com/25565511/](http://paste.ubuntu.com/25565511/)

Also, the ls command, in the grub rescue screen, did not work for me:

[URL="https://www.youtube.com/watch?v=5M1ZpUKUgPA"]https://www.youtube.com/watch?v=5M1ZpUKUgPA

http://www.legendiary.at/2016/01/04/windows-10-update-changes-partition-table-and-breaks-grub/[/URL]

I do not care about win 10 at all, all i need, is to be able to enter ubuntu, since i have files in there i need.

---

### Post by Impavidus on 2017-09-19
It seems the Windows update has deleted your Ubuntu partition. It's a known issue with Windows 10. It's likely all data is still there. Your partition used to be in the front part of the extended partition /dev/sda4.

[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

---

### Post by oldfred on 2017-09-19
In addition to testdisk which does work for most, there is parted rescue.
And backup current partitions as a few have somehow damaged all the partitions with incorrect choices in testdisk. If you have backup then you can easily start over.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

Your missing partition is after the start of the extended (776,....) by 1 or 2 sectors and before the start of swap (959,....) by several sectors. Testdisk uses CHS which does not easily translate, but can be converted to sectors.

 /dev/sda4         776,966,142   975,849,471   198,883,330   5 Extended
/dev/sda5         959,111,168   975,849,471    16,738,304  82 Linux swap / Solaris 

Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[URL="http://ubuntuforums.org/showthread.php?t=2315405"]http://ubuntuforums.org/showthread.php?t=2315405
[/URL] Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by sadoy on 2017-09-21
dear oldfred, i know this is a noob question, i plan to use your suggestion, using parted. 
i face the exact same problem, with similar sector numbers.
i plan to first run parted
od dev/sda4:

/dev/sda4         776,966,142   975,849,471

[LEFT][COLOR=#000000][FONT=Ubuntubeta]*unit s*[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]*rescue*[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]*input start & end and see if it finds partition*[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]*so i should run parted twice, one with start *[/FONT][/COLOR][/LEFT]
776,966,143, and end something like 959,100,000?

then the same with what sectors for getting back the swap?

Can i delete entirely the swap, and in the end make a swap file?

I do not have the luxury to make an image of my disk, so i need your exact advice, thank you

What i do not understand, is the overlapping of sectors, of swap and the linux partition...

---

### Post by oldfred on 2017-09-21
I thought parted rescue auto scanned, like testdisk does to find the partition. 
You need to give it the start & end sectors to search but do not think it has to be exact. And if too large or too small it just will not give you new partition.
Start of actual partition has to be one or two sectors after start of extended partition.
And end of partition will be before the start of swap if you have the ext4 first in extended & swap last.
I believe partitions have to have at least one sector between them.

You should not need to delete swap, and need to know its start sector. But can easily recreate a new swap but must then update fstab with its new UUID. Or use a swap file like the new default with 17.04.

---


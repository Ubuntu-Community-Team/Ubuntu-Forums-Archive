---
title: "The boot selection failed because a required device is inaccessible"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by aab001 on 2013-06-25
Hi,


[COLOR=#000000][FONT=times new roman][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]After installing ubuntu 13.04 [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]I[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3] [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]couldn’t[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3] boot any operating  system and [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]I[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3] got the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]message[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3] "[/SIZE][/FONT][/COLOR]The boot selection failed because a required device is inaccessible" 

then  I used the boot repair disk and  I got the grub menu and i can boot the  ubuntu but I cannot boot the windows and I have the same message when I  tried to boot the windows.[COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]"[/SIZE][/FONT][/COLOR]The boot selection failed because a required device is inaccessible"
The bootInfo URL is paste.ubuntu.com/5764282


[COLOR=#000000][FONT=times new roman, new york, times, serif][SIZE=3]many thanks in advance[/SIZE][/FONT][/COLOR]

[/FONT][/COLOR]
 
Ahmad

---

### Post by MidnightGrey on 2013-06-25
Ah i am sorry to be the bearer of bad news but it appears you've deleted your windows partition.

---

### Post by aab001 on 2013-06-25
no it is there

root@aab-HP-Compaq-Elite-8300-SFF:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa82447e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000    98680831    48828416   83  Linux
/dev/sda3        98682878   499070975   200194049    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5        98682880   108445695     4881408   82  Linux swap / Solaris
/dev/sda6       108447744   499070975   195311616   83  Linux

---

### Post by MidnightGrey on 2013-06-25
I'm not sure what is a good website to explain how windows OS uses partitions, but essentially it requires 2 partitions to boot up, one of which is missing (the main one).

if you look at your fdisk output.

> **aab001 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT

Start: 2048
End: 1023999
Blocks: 510976

each block is 1024 bytes, this means sda1 has a size of ~500 Mb which cant possibly be your windows partition.
Compare this to your swap partition (sda5) which has a block size of 4881408 (or approx. 5 Gb).

---

### Post by aab001 on 2013-06-25
[COLOR=#000000][FONT=times new roman][SIZE=3]Hi,


[FONT=times new roman, new york, times, serif]After installing ubuntu 13.04 [/FONT][FONT=times new roman, new york, times, serif]Couldn’t[/FONT] [FONT=times new roman, new york, times, serif]boot any operating system and I[/FONT] [FONT=times new roman, new york, times, serif]got the message[/FONT] [FONT=times new roman, new york, times, serif]"[/FONT]The boot selection failed because a required device is inaccessible" 

then I used the boot repair disk and I got the grub menu and i can boot the ubuntu but I cannot boot the windows and I have the same message when I tried to boot the windows.[FONT=times new roman, new york, times, serif]"[/FONT]The boot selection failed because a required device is inaccessible"
The bootInfo URL is paste.ubuntu.com/5764282
[/SIZE]
[SIZE=3]the following information is from my terminal[/SIZE]
[/FONT][/COLOR]
   

[COLOR=#000000][FONT=times new roman]root@aab-HP-Compaq-Elite-8300-SFF:~# fdisk -l [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman] [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]Disk /dev/sda: 500.1 GB, 500107862016 bytes [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]Units = sectors of 1 * 512 = 512 bytes [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]Sector size (logical/physical): 512 bytes / 4096 bytes [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]I/O size (minimum/optimal): 4096 bytes / 4096 bytes [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]Disk identifier: 0xa82447e9 [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman] [/FONT][/COLOR]
 [COLOR=#000000]   [FONT=times new roman]Device Boot      Start         End      Blocks   Id  System [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]/dev/sda2         1024000    98680831    48828416   83  Linux [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]/dev/sda3        98682878   499070975   200194049    5  Extended [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]Partition 3 does not start on physical sector boundary. [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]/dev/sda5        98682880   108445695     4881408   82  Linux swap / Solaris [/FONT][/COLOR]
 [COLOR=#000000][FONT=times new roman]/dev/sda6       108447744   499070975   195311616   83  Linux [/FONT][/COLOR]



[COLOR=#000000][FONT=times new roman][SIZE=3][FONT=times new roman, new york, times, serif]many thanks in advance[/FONT]



Ahmad[/SIZE]
[/FONT][/COLOR]

---

### Post by carl4926 on 2013-06-25
Looks like you have lost your actual windows install

sda1 is just the windows boot partition, given it's size anyway....

---

### Post by MidnightGrey on 2013-06-25
aab001 did you make a 2nd post because you didn't like my answer?
[http://ubuntuforums.org/showthread.php?t=2157399](http://ubuntuforums.org/showthread.php?t=2157399)

---

### Post by carl4926 on 2013-06-25
> **MidnightGrey said:**
> aab001 did you make a 2nd post because you didn't like my answer?
[http://ubuntuforums.org/showthread.php?t=2157399](http://ubuntuforums.org/showthread.php?t=2157399)

Now confirmed at the mouth of two witnesses

[COLOR=#000000]aab001 you'll live and learn.[/COLOR]

---

### Post by oldfred on 2013-06-25
Threads merged. Please do not post duplicate threads on the same topic.
We all are volunteers and need to know what else has been posted to avoid duplicate effort.

---

### Post by aab001 on 2013-06-26
> **carl4926 said:**
> Now confirmed at the mouth of two witnesses

[COLOR=#000000]aab001 you'll live and learn.[/COLOR]

   I posted again because I believed that I have posted in the wrong section, also your first answer shows that you are not confident with it (Ah i am sorry to be the bearer of bad news but it _appears_ you've deleted your windows partition) and you didn't give a solution. In fact,  I am really in a bad situation so I tried to find any one who can fix this problem.
 Sorry for any convenient I may did
 cheers

---

### Post by carl4926 on 2013-06-26
> **aab001 said:**
> I posted again because I believed that I have posted in the wrong section, also your first answer shows that you are not confident with it (Ah i am sorry to be the bearer of bad news but it _appears_ you've deleted your windows partition) and you didn't give a solution. In fact,  I am really in a bad situation so I tried to find any one who can fix this problem.
 Sorry for any convenient I may did
 cheers

OK, so it's a sad situation.
If you don't have a windows DVD, you might try and borrow one. Else buy one.
Or just live without windows

---


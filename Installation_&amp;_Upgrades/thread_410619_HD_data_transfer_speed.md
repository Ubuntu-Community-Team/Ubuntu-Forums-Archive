---
title: "HD data transfer speed"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by solracarevir on 2007-04-15
Hi guys, i upgraded to feisty a few days ago and im having the following issue, data transfer from the hard disk to another device is incredibly slow, I noticed it today when i started to transfer music to my new ipod. I have to transfer 3000 songs(almost 12gb of music) I knew this would take a while, cause i have done it before, but i started the transfer 4 hours ago and it have transfered only 621 songs!!!! im using Kernel 2.6.20-15-generic, any help?
tell me what info you need to help me and i will give it to you

Thanks in advance

---

### Post by heimo on 2007-04-15
You could start by running command below on each of your hard disks (are those serial ATA or parallel ATA?)
```
sudo hdparm -tT /dev/sda

```On my hard disk, I get:
```
/dev/sda:
 Timing cached reads:   1994 MB in  2.00 seconds = 996.97 MB/sec
 Timing buffered disk reads:  256 MB in  3.01 seconds =  85.15 MB/sec
```

---

### Post by solracarevir on 2007-04-16
-I stopped the music transfer, i will try to solve this first-
Running  sudo hdparm -tT /dev/sda on my machine gets me

```

/dev/sda:
 Timing cached reads:   894 MB in  2.00 seconds = 446.65 MB/sec
 Timing buffered disk reads:   42 MB in  3.11 seconds =  13.49 MB/sec

```not so pretty numbers right?, im not sure but i think my latop is serial ATA

edited: also, my cpu gets mad when transfering the data. even tough the numbers i posted seems to be low comparing to yours, could it be the app im using?(rhythmbox)

---

### Post by heimo on 2007-04-16
Quick post: Check in BIOS / using hdparm the transfer mode of the disk (is DMA on?).

---

### Post by solracarevir on 2007-04-16
Yes DMA is on

```

$ sudo hdparm -d /dev/hda1

/dev/hda1:
 using_dma    =  1 (on)

```

```

$ sudo hdparm -tT /dev/hda1

/dev/hda1:
 Timing cached reads:   900 MB in  2.00 seconds = 450.11 MB/sec
 Timing buffered disk reads:   72 MB in  3.07 seconds =  23.46 MB/sec
carlos@snowy:~$ cd /

```

---

### Post by heimo on 2007-04-16
Transfer rates with laptop 2,5" disks is significantly slower than what my example disk (fast 3.5" disk) can do, I don't know about new laptops, but my oldish Thinkpad couldn't do over 20MB/s.

What's your approximate real world transfer speed? Try other applications, direct copying in nautilus or terminal (using cp and sync)  and compare. If possible, boot to older kernel and repeat. Remember that files get cached in memory.

---

### Post by WeAreMany on 2008-04-01
:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1254 MB in  2.00 seconds = 626.30 MB/sec
 Timing buffered disk reads:    2 MB in 13.57 seconds = 150.97 kB/sec

Are these speeds good for writes across a 10/00 network?

---


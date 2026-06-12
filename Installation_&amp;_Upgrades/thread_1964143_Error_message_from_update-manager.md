---
title: "Error message from update-manager"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2012-04-23
12.04-Beta, USB install, running update-manager gives the following Error message: 
> 
Package operation failed
The installation or removal of a software package failed.

Details:
installArchives() failed: 
Extracting templates from packages: 83%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': Input/output error

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB


I'm not sure if this is of any interest to developers.

---

### Post by matt_symes on 2012-04-23
Hi

Try running fsck on the partition from a LiveCD/USB.

Is the drive full up ?

Kind regards

---

### Post by Cariboo1938 on 2012-04-24
Hi and thanks for the response...> **matt_symes said:**
> 

Is the drive full up ?



I think so...I'm connected to the Forum and I'm writing this right now from an Ubuntu 12.04 Beta USB Drive installation.

> **matt_symes said:**
> 
Try running fsck on the partition from a LiveCD/USB. 
Sorry, but I don't exactly know what to do here..When I open a terminal as su and type '*fsck*' all I get is:> root@ubuntu:~# fsck
fsck from util-linux 2.20.1
root@ubuntu:~# 
 Does this make sense to you?:confused:

Kind regards

---

### Post by Cariboo1938 on 2012-04-24
More Info:

The screenshot shows what I want to do---install 36 updates on the USB drive.
 
I learned more about the fsck command [HERE]("http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm") and tried several options, but without success.

I checked the directory the update-manager is complaining about and noticed that the tmp.i gives only ??? for access right/ownership/size/date.

/var/lib/dpkg looks ok to me:

> root@ubuntu:/var/lib/dpkg# ls -l
total 6197
drwxr-xr-x 1 root root    4096 Apr 19 15:21 alternatives
-rw-r--r-- 1 root root 1487685 Apr 19 15:23 available
-rw-r--r-- 1 root root 1487684 Apr 19 15:21 available-old
-rw-r--r-- 1 root root       8 Mar 27 16:30 cmethopt
-rw-r--r-- 1 root root    1610 Apr 15 11:37 diversions
-rw-r--r-- 1 root root    1656 Apr 15 11:28 diversions-old
drwxr-xr-x 1 root root  118784 Apr 19 15:23 info
-rw-r----- 1 root root       0 Apr 24 10:34 lock
drwxr-xr-x 2 root root       3 Dec 16 02:32 parts
-rw-r--r-- 1 root root     135 Mar 27 16:33 statoverride
-rw-r--r-- 1 root root 1599966 Apr 19 15:29 status
-rw-r--r-- 1 root root 1599966 Apr 19 15:27 status-old
drwxr-xr-x 1 root root    4096 Apr 19 15:26 triggers
drwxr-xr-x 1 root root    4096 Apr 19 15:29 updates
root@ubuntu:/var/lib/dpkg# 

tmp.i --- looks strange to me:

> root@ubuntu:/var/lib/dpkg/updates# ls -l
ls: cannot access tmp.i: Input/output error
total 0
-????????? ? ? ? ?            ? tmp.i
root@ubuntu:/var/lib/dpkg/updates# 

How can that be fixed if fsck does not do it?

---

### Post by ph4nt0m117 on 2012-04-24
> **Cariboo1938 said:**
> 12.04-Beta, USB install, running update-manager gives the following Error message: 


I'm not sure if this is of any interest to developers.

In this case, the hard drive is full.

---

### Post by matt_symes on 2012-04-24
Hi

That does look like a corrupted file. What is the output of (small I and not L after ls)

```
ls -i /var/lib/dpkg/updates/tmp.i
```

Also, to run fsck you want to boot into a live CD/USB. Find the device node for your hard drive root partition.

```
sudo fdisk -l
```

That will show you the device node such as /dev/sdb1

Then type

```
sudo fsck -f /dev/sdXY
```

Where sdXY is the device node found from the command above. This wlll force a check even if the file system clean flag is set.

If in doubt then post the output of the fdisk command back here.

You can also check the amount of free space on the root partition by mounting the partition and running the df command.

```
sudo mkdir ~/root_drive
```

```
sudo mount -t ext4 /dev/sdXY ~/root_drive
```

```
df -h ~/root_drive
```

Change sdXY as before. It assume you used the default ext4 file system That will show you the amount of free space on your root partition. Post the results back here.

Kind regards

---

### Post by Cariboo1938 on 2012-04-25
Here are the terminal outputs.....

What is the output of '*ls -i /var/lib/dpkg/updates/tmp.i*'?

> 
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# ls -i /var/lib/dpkg/updates/tmp.i
16762 /var/lib/dpkg/updates/tmp.i
root@ubuntu:~# 


Also, find the device node for your hard drive root partition with '*sudo fdisk -l*'

> 
Disk /dev/sdb: 8401 MB, 8401190912 bytes
99 heads, 37 sectors/track, 4479 cylinders, total 16408576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ac98

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *         736    16408575     8203920    b  W95 FAT32**
root@ubuntu:~# 


Then type '*sudo fsck -f /dev/sdb1*'. 
This wlll force a check even if the file system clean flag is set.

> 
root@ubuntu:~# sudo fsck -f /dev/sdb1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset : original/backup)
  3:53/6d, 4:59/6b, 5:53/64, 6:4c/6f, 7:49/73, 8:4e/66, 9:55/73, 10:58/00
  , 90:fa/0e, 91:fc/1f, 92:31/be, 93:c9/77, 94:8e/7c, 95:d1/ac, 96:bc/22
  , 97:76/c0, 98:7b/74, 99:52/0b, 100:06/56, 101:57/b4, 102:1e/0e, 103:56/bb
  , 104:8e/07, 105:c1/00, 106:b1/cd, 107:26/10, 108:bf/5e, 109:78/eb
  , 110:7b/f0, 111:f3/32, 112:a5/e4, 113:8e/cd, 114:d9/16, 115:bb/cd
  , 116:78/19, 117:00/eb, 118:0f/fe, 119:b4/54, 120:37/68, 121:0f/69
  , 122:a0/73, 123:56/20, 124:20/69, 125:d2/73, 126:78/20, 127:1b/6e
  , 128:31/6f, 129:c0/74, 130:b1/20, 131:06/61, 132:89/20, 133:3f/62
  , 134:89/6f, 135:47/6f, 136:02/74, 137:f3/61, 138:64/62, 139:a5/6c
  , 140:8a/65, 141:0e/20, 142:18/64, 143:7c/69, 144:88/73, 145:4d/6b
  , 146:f8/2e, 147:50/20, 148:50/20, 150:50/6c, 151:cd/65, 152:13/61
  , 153:eb/73, 154:62/65, 155:8b/20, 156:55/69, 157:aa/6e, 158:8b/73
  , 159:75/65, 160:a8/72, 161:c1/74, 162:ee/20, 163:04/61, 164:01/20
  , 165:f2/62, 166:83/6f, 167:fa/6f, 168:4f/74, 169:76/61, 170:31/62
  , 171:81/6c, 172:fa/65, 173:b2/20, 174:07/66, 175:73/6c, 176:2b/6f
  , 177:f6/70, 178:45/70, 179:b4/79, 180:7f/20, 181:75/61, 182:25/6e
  , 183:38/64, 184:4d/0d, 185:b8/0a, 186:74/70, 187:20/72, 188:66/65
  , 189:3d/73, 190:21/73, 191:47/20, 192:50/61, 193:54/6e, 194:75/79
  , 195:10/20, 196:80/6b, 197:7d/65, 198:b8/79, 199:ed/20, 200:75/74
  , 201:0a/6f, 202:66/20, 203:ff/74, 204:75/72, 205:ec/79, 206:66/20
  , 207:ff/61, 208:75/67, 209:e8/61, 210:eb/69, 211:0f/6e, 212:51/20
  , 213:51/2e, 214:66/2e, 215:ff/2e, 216:75/20, 217:bc/0d, 218:eb/0a
  , 219:07/00, 220:51/00, 221:51/00, 222:66/00, 223:ff/00, 224:36/00
  , 225:1c/00, 226:7c/00, 227:b4/00, 228:08/00, 229:e8/00, 230:e9/00
  , 232:72/00, 233:13/00, 234:20/00, 235:e4/00, 236:75/00, 237:0f/00
  , 238:c1/00, 239:ea/00, 240:08/00, 241:42/00, 242:89/00, 243:16/00
  , 244:1a/00, 245:7c/00, 246:83/00, 247:e1/00, 248:3f/00, 249:89/00
  , 250:0e/00, 251:18/00, 252:7c/00, 253:fb/00, 254:bb/00, 255:aa/00
  , 256:55/00, 257:b4/00, 258:41/00, 259:e8/00, 260:cb/00, 262:72/00
  , 263:10/00, 264:81/00, 265:fb/00, 266:55/00, 267:aa/00, 268:75/00
  , 269:0a/00, 270:f6/00, 271:c1/00, 272:01/00, 273:74/00, 274:05/00
  , 275:c6/00, 276:06/00, 277:46/00, 278:7d/00, 280:66/00, 281:b8/00
  , 282:10/00, 283:ec/00, 284:16/00, 286:66/00, 287:ba/00, 292:bb/00
  , 294:7e/00, 295:e8/00, 296:0e/00, 298:66/00, 299:81/00, 300:3e/00
  , 301:1c/00, 302:7e/00, 303:2d/00, 304:ae/00, 305:61/00, 306:73/00
  , 307:75/00, 308:74/00, 309:e9/00, 310:f8/00, 312:66/00, 313:03/00
  , 314:06/00, 315:60/00, 316:7b/00, 317:66/00, 318:13/00, 319:16/00
  , 320:64/00, 321:7b/00, 322:b9/00, 323:10/00, 325:eb/00, 326:2b/00
  , 327:66/00, 328:52/00, 329:66/00, 330:50/00, 331:06/00, 332:53/00
  , 333:6a/00, 334:01/00, 335:6a/00, 336:10/00, 337:89/00, 338:e6/00
  , 339:66/00, 340:60/00, 341:b4/00, 342:42/00, 343:e8/00, 344:77/00
  , 346:66/00, 347:61/00, 348:8d/00, 349:64/00, 350:10/00, 351:72/00
  , 352:01/00, 353:c3/00, 354:66/00, 355:60/00, 356:31/00, 357:c0/00
  , 358:e8/00, 359:68/00, 361:66/00, 362:61/00, 363:e2/00, 364:da/00
  , 365:c6/00, 366:06/00, 367:46/00, 368:7d/00, 369:2b/00, 370:66/00
  , 371:60/00, 372:66/00, 373:0f/00, 374:b7/00, 375:36/00, 376:18/00
  , 377:7c/00, 378:66/00, 379:0f/00, 380:b7/00, 381:3e/00, 382:1a/00
  , 383:7c/00, 384:66/00, 385:f7/00, 386:f6/00, 387:31/00, 388:c9/00
  , 389:87/00, 390:ca/00, 391:66/00, 392:f7/00, 393:f7/00, 394:66/00
  , 395:3d/00, 396:ff/00, 397:03/00, 400:77/00, 401:17/00, 402:c0/00
  , 403:e4/00, 404:06/00, 405:41/00, 406:08/00, 407:e1/00, 408:88/00
  , 409:c5/00, 410:88/00, 411:d6/00, 412:b8/00, 413:01/00, 414:02/00
  , 415:e8/00, 416:2f/00, 418:66/00, 419:61/00, 420:72/00, 421:01/00
  , 422:c3/00, 423:e2/00, 424:c9/00, 425:31/00, 426:f6/00, 427:8e/00
  , 428:d6/00, 429:bc/00, 430:68/00, 431:7b/00, 432:8e/00, 433:de/00
  , 434:66/00, 435:8f/00, 436:06/00, 437:78/00, 439:be/00, 440:da/00
  , 441:7d/00, 442:ac/00, 443:20/00, 444:c0/00, 445:74/00, 446:09/00
  , 447:b4/00, 448:0e/00, 449:bb/00, 450:07/00, 452:cd/00, 453:10/00
  , 454:eb/00, 455:f2/00, 456:31/00, 457:c0/00, 458:cd/00, 459:16/00
  , 460:cd/00, 461:19/00, 462:f4/00, 463:eb/00, 464:fd/00, 465:8a/00
  , 466:16/00, 467:74/00, 468:7b/00, 469:06/00, 470:cd/00, 471:13/00
  , 472:07/00, 473:c3/00, 474:42/00, 475:6f/00, 476:6f/00, 477:74/00
  , 478:20/00, 479:65/00, 480:72/00, 481:72/00, 482:6f/00, 483:72/00
  , 484:0d/00, 485:0a/00, 504:fe/00, 505:02/00, 506:b2/00, 507:3e/00
  , 508:18/00, 509:37/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 


I didn't know what to do :confused: so I entered option "3" and got this:
> 
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/casper/initrd.lz
  Contains a free cluster (1422417). Assuming EOF.
/casper/initrd.lz
  File size is 14960257 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/casper/vmlinuz
  Contains a free cluster (1421204). Assuming EOF.
/casper/vmlinuz
  File size is 4965840 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Unable to create unique name
root@ubuntu:~# 


I go through the procedure again when I know how to decide:
1) Copy original to backup
2) Copy backup to original

What is the right choice here:confused:

Thank you for the help so far and 
my regards

---

### Post by matt_symes on 2012-04-25
Hi

You have an inode for that file. That is good. Lets take a closer look at the file. Boot into your main Ubuntu installation

Open a terminal and type

```
df
```

You should get output like this. You are interested in the line containing the red **[COLOR=Red]/[/COLOR]**
[COLOR=Black]
It will show where you root partition is mounted. In my case it is [COLOR=SeaGreen]/dev/sda2[/COLOR]

[/COLOR]```

matthew@matthew-Aspire-7540 ~ % df   
Filesystem     1K-blocks     Used Available Use% Mounted on
**[COLOR=SeaGreen]/dev/sda2[/COLOR]        9734404  8161444   1084680  89% [COLOR=Red]/[/COLOR]**
udev             1400228       12   1400216   1% /dev
tmpfs             564892      976    563916   1% /run
none                5120        0      5120   0% /run/lock
none             1412228      156   1412072   1% /run/shm
matthew@matthew-Aspire-7540 ~ % 
```

Type this command below and substitute sda2 for you root partition.

```
sudo debugfs -R "stat <16762>" /dev/sda2
```

Post back the results back here.

> What is the right choice here

As for your fsck attempt on /dev/sdb1, you did the right thing That would have run fsck on your FAT32 filing system. Not what you want to do.

I do not see any linux partitions there from your fdisk -l command. I would have expected to see something like...
```

matthew@matthew-Aspire-7540 ~ % sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d0c8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    97656831    48827392   83  Linux
/dev/sda2   *    97656832   117188063     9765616   83  Linux
/dev/sda3       117188608   136720383     9765888   83  Linux
/dev/sda4       136722430   625137344   244207457+   5  Extended
/dev/sda5       136722432   227014514    45146041+  83  Linux
/dev/sda6       227014578   234372284     3678853+  82  Linux swap / Solaris
<SNIP>
matthew@matthew-Aspire-7540 ~ % 
```

Is this a Wubi install ?

Kind regards

---

### Post by Cariboo1938 on 2012-04-25
Hi,

Confusion complete:confused:

Re.: '***df***'
> 
root@ubuntu:~# df
Filesystem     1K-blocks    Used Available Use% Mounted on
**[COLOR="Magenta"]/cow             4128444 3608824    309908  93% /[/COLOR]**
udev             3811396       4   3811392   1% /dev
tmpfs            1528236     864   1527372   1% /run
/dev/sdb1        8187904 5452972   2734932  67% /cdrom
/dev/loop0        680320  680320         0 100% /rofs
tmpfs            3820584      16   3820568   1% /tmp
none                5120       0      5120   0% /run/lock
none             3820584      76   3820508   1% /run/shm
root@ubuntu:~# 



Re.: '***fdisk -l***' ---> certainly I have this too, but I thought this is not relevant in my case as I try to update the 12.04 which is running on USB drive and I thought the corrupted file in question belongs to this USB FAT filesystem...

> 
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfcb09eec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   744269823   371930112    7  HPFS/NTFS/exFAT
/dev/sda3      1432315904  1464936447    16310272    7  HPFS/NTFS/exFAT
/dev/sda4       744271870  1432315903   344022017    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       818206720  1432315903   307054592   83  Linux
/dev/sda6       744271872   787279871    21504000   83  Linux
/dev/sda7       787281920   818204671    15461376   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8401 MB, 8401190912 bytes
99 heads, 37 sectors/track, 4479 cylinders, total 16408576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ac98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         736    16408575     8203920    b  W95 FAT32
root@ubuntu:~#


---

### Post by matt_symes on 2012-04-25
Hi

This is a Live, persistent USB installation that has the problem ? 
Being run from a USB stick ? 
Booted into a PC when powered on (or warm cycled) and the USB device is the first bootable boot device the BIOS sees ?

Is that so ? This may be why we are crossing wires and would explain FAT32 filing system,  so please confirm this.

Kind regards

---

### Post by Cariboo1938 on 2012-04-25
Hi

This is a Live, persistent USB installation that has the problem ? 
**[COLOR="Blue"]YES![/COLOR]**


Being run from a USB stick ?
**[COLOR="Blue"]YES![/COLOR]**

Booted into a PC when powered on (or warm cycled) and the USB device is the first bootable boot device the BIOS sees?
**[COLOR="Blue"]YES![/COLOR]**

Is that so ? 
**[COLOR="Blue"]YES![/COLOR]**

Hereby I confirm this. :)

Kind regards

---

### Post by matt_symes on 2012-04-26
Hi

> Hereby I confirm this. :smile:LoL. Much confusion there then :D It don't really use persistent USB sticks so....

.. however.

You could try deleting the file (tmp.i) using its inode. 

You can also try debugfs to clear the inode of the file.

Make space on the stick by cleaning apt-caches and removing old kernels.

Kind regards

---

### Post by Cariboo1938 on 2012-04-26
> **matt_symes said:**
> 

You could try deleting the file (tmp.i) using its inode. 

You can also try debugfs to clear the inode of the file.

Make space on the stick by cleaning apt-caches and removing old kernels.

Kind regards
Hi,
Can I use 
a) remove files with inode number
b) cleaning apt-caches 
c) removing old kernels

on a FAT file system as it is on the USB stick?

---

### Post by matt_symes on 2012-04-26
Hi

> **Cariboo1938 said:**
> Hi,
Can I use 
a) remove files with inode number
b) cleaning apt-caches 
c) removing old kernels

on a FAT file system as it is on the USB stick?

I'm really no expert here at all and i am hoping someone else will speak up.

I suggest trying it.

Kind regards

---

### Post by Cariboo1938 on 2012-04-26
Find the inode# for "tmp.i" didn't work:

> a)root@ubuntu:~# ls -i /var/lib/dpkg/updates/tmp.i
ls: cannot access /var/lib/dpkg/updates/tmp.i: Input/output error

b)root@ubuntu:~# cd /var/lib/dpkg/updates
root@ubuntu:/var/lib/dpkg/updates# ls -il
ls: cannot access tmp.i: Input/output error
total 0
? -????????? ? ? ? ?            ? tmp.i

Though, in general inode#s are found on a FAT system
> c)root@ubuntu:/var/lib/dpkg# ls -il
total 6197
 10934 drwxr-xr-x 1 root root    4096 Apr 19 15:21 alternatives
 92343 -rw-r--r-- 1 root root 1487685 Apr 19 15:23 available
106933 -rw-r--r-- 1 root root 1487684 Apr 19 15:21 available-old
135832 -rw-r--r-- 1 root root       8 Mar 27 16:30 cmethopt
238483 -rw-r--r-- 1 root root    1610 Apr 15 11:37 diversions
238478 -rw-r--r-- 1 root root    1656 Apr 15 11:28 diversions-old
 10701 drwxr-xr-x 1 root root  118784 Apr 19 15:23 info
[COLOR="DarkOrange"]237633 -rw-r----- 1 root root       0 Apr 24 10:34 lock[/COLOR]
 38674 drwxr-xr-x 2 root root       3 Dec 16 02:32 parts
135845 -rw-r--r-- 1 root root     135 Mar 27 16:33 statoverride
 92345 -rw-r--r-- 1 root root 1599966 Apr 19 15:29 status
[COLOR="DarkOrange"]237612 -rw-r--r-- 1 root root 1599966 Apr 19 15:27 status-old[/COLOR]
 10698 drwxr-xr-x 1 root root    4096 Apr 19 15:26 triggers
 10696 drwxr-xr-x 1 root root    4096 Apr 19 15:29 updates


,and, for example, I could remove inode# 237633 - file "lock" and inode# 237612 - file "status-old" 
and I could also remove files in directory, let's say 'alteratives' 
but I could not remove directory updates containing the corrupted file tmp.i
> root@ubuntu:/var/lib/dpkg# find . -inum 10696 -exec rmdir --ignore {} \;
find: `./updates/tmp.i': Input/output error
root@ubuntu:/var/lib/dpkg#

I finally decided to give up the idea to fix that and start over again with today released 12.04 LTS

@ matt
Thanks a lot for your patience and help. I learned a lot.
Cariboo
:)

---


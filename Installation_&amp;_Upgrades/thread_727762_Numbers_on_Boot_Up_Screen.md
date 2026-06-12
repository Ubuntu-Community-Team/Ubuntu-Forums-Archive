---
title: "Numbers on Boot Up Screen"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2008-03-18
I have seen a number of posts referring to a list of numbers shown during boot up.

I have recently re-installed 7.10 after problems with booting XP and have exactly the same problem now. Does anyone know what this measn and if this effecting the system in any way?

I have attached a couple of photos showing the list of numbers and then the 'not automatically fixing this' message.

BigTel

---

### Post by PmDematagoda on 2008-03-18
It looks like a partition is damaged/has errors. Post the outputs of:-
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by bigtel on 2008-03-18
I will do this at my first oppurtunity this evening. Thanks.

---

### Post by bigtel on 2008-03-18
Firstly

From the fdisk command - 

Disk /dev/hda: 100.0 GB, 100030242816 bytes
1 heads, 63 sectors/track, 3101136 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x00018d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           2     1062840    33479428+   c  W95 FAT32 (LBA)
/dev/hda3         1062841     2235841    36949531+  83  Linux
/dev/hda4         2235842     3101040    27253737+   f  W95 Ext'd (LBA)
/dev/hda5         2235843     2287604     1630503   82  Linux swap / Solaris
/dev/hda6         2287682     3101040    25620808+   b  W95 FAT32



Secondly

From the cat command -

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=375a2d70-713d-415a-b7c1-37adba1a47b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=0841-1A02  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=346C-1BE2  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=f2f6134e-ef4e-47d1-bd79-ce1e18b33f40 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Can you get any info from these..??

---

### Post by PmDematagoda on 2008-03-18
Try and perform a disk check on hda2:-

1) First unmount the partition:-
```
sudo umount /media/hda2
```

2) Perform the disk check:-
```
sudo fsck -r /dev/hda2
```

Then see if the error persists.

---

### Post by bigtel on 2008-03-19
I have entered the command and I get the following message - it is asking me if I want to restore my boot sector  -  I am unsure what to do now? Should I restore and see what happens (option 2 from below)..?

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  26:ff/f0, 67:02/db, 68:1a/16, 69:41/3b, 70:08/1d, 71:20/4e, 72:20/4f
  , 74:20/4e, 75:20/41, 76:20/4d, 77:20/45, 90:fa/33, 91:33/c9, 92:c9/8e
  , 93:8e/d1, 94:d1/bc, 95:bc/f4, 96:f8/7b, 97:7b/8e, 98:8e/c1, 99:c1/8e
  , 100:bd/d9, 101:78/bd, 103:c5/7c, 104:76/88, 105:00/4e, 106:1e/02
  , 107:56/8a, 108:16/56, 109:55/40, 110:bf/b4, 111:22/08, 112:05/cd
  , 113:89/13, 114:7e/73, 115:00/05, 116:89/b9, 117:4e/ff, 118:02/ff
  , 119:b1/8a, 120:0b/f1, 121:fc/66, 122:f3/0f, 123:a4/b6, 124:8e/c6
  , 125:d9/40, 126:bd/66, 127:00/0f, 128:7c/b6, 129:c6/d1, 130:45/80
  , 131:fe/e2, 132:0f/3f, 133:8b/f7, 134:46/e2, 135:18/86, 136:88/cd
  , 137:45/c0, 138:f9/ed, 139:38/06, 140:4e/41, 141:40/66, 142:7d/0f
  , 143:25/b7, 144:8b/c9, 145:c1/66, 146:99/f7, 147:bb/e1, 148:00/66
  , 149:07/89, 150:e8/46, 151:97/f8, 152:00/83, 153:72/7e, 154:1a/16
  , 155:83/00, 156:eb/75, 157:3a/38, 158:66/83, 159:a1/7e, 160:1c/2a
  , 161:7c/00, 162:66/77, 163:3b/32, 164:07/66, 165:8a/8b, 166:57/46
  , 167:fc/1c, 168:75/66, 169:06/83, 170:80/c0, 171:ca/0c, 172:02/bb
  , 173:88/00, 174:56/80, 175:02/b9, 176:80/01, 177:c3/00, 178:10/e8
  , 179:73/2b, 180:ed/00, 181:bf/e9, 182:02/48, 183:00/03, 184:83/a0
  , 185:7e/fa, 186:16/7d, 187:00/b4, 188:75/7d, 189:45/8b, 190:8b/f0
  , 191:46/ac, 192:1c/84, 193:8b/c0, 194:56/74, 195:1e/17, 196:b9/3c
  , 197:03/ff, 198:00/74, 199:49/09, 200:40/b4, 201:75/0e, 202:01/bb
  , 203:42/07, 204:bb/00, 205:00/cd, 206:7e/10, 207:e8/eb, 208:5f/ee
  , 209:00/a0, 210:73/fb, 211:26/7d, 212:b0/eb, 213:f8/e5, 214:4f/a0
  , 215:74/f9, 216:1d/7d, 217:8b/eb, 218:46/e0, 219:32/98, 220:33/cd
  , 221:d2/16, 222:b9/cd, 223:03/19, 224:00/66, 225:3b/60, 226:c8/66
  , 227:77/3b, 228:1e/46, 229:8b/f8, 230:76/0f, 231:0e/82, 232:3b/4a
  , 233:ce/00, 234:73/66, 235:17/6a, 236:2b/00, 237:f1/66, 238:03/50
  , 239:46/06, 240:1c/53, 241:13/66, 242:56/68, 243:1e/10, 244:eb/00
  , 245:d1/01, 246:73/00, 247:0b/80, 248:eb/7e, 249:27/02, 250:83/00
  , 251:7e/0f, 252:2a/85, 253:00/20, 254:77/00, 255:03/b4, 256:e9/41
  , 257:fd/bb, 258:02/aa, 259:be/55, 260:7e/8a, 261:7d/56, 262:ac/40
  , 263:98/cd, 264:03/13, 265:f0/0f, 266:ac/82, 267:84/1c, 268:c0/00
  , 269:74/81, 270:17/fb, 271:3c/55, 272:ff/aa, 273:74/0f, 274:09/85
  , 275:b4/14, 276:0e/00, 277:bb/f6, 278:07/c1, 279:00/01, 280:cd/0f
  , 281:10/84, 282:eb/0d, 283:ee/00, 284:be/fe, 285:81/46, 286:7d/02
  , 287:eb/b4, 288:e5/42, 289:be/8a, 290:7f/56, 291:7d/40, 292:eb/8b
  , 293:e0/f4, 294:98/cd, 295:cd/13, 296:16/b0, 297:5e/f9, 298:1f/66
  , 299:66/58, 300:8f/66, 301:04/58, 302:cd/66, 303:19/58, 304:41/66
  , 305:56/58, 306:66/eb, 307:6a/2a, 308:00/66, 309:52/33, 310:50/d2
  , 311:06/66, 312:53/0f, 313:6a/b7, 314:01/4e, 315:6a/18, 316:10/66
  , 317:8b/f7, 318:f4/f1, 319:60/fe, 320:80/c2, 321:7e/8a, 322:02/ca
  , 323:0e/66, 324:75/8b, 325:04/d0, 326:b4/66, 327:42/c1, 328:eb/ea
  , 329:1d/10, 330:91/f7, 331:92/76, 332:33/1a, 333:d2/86, 334:f7/d6
  , 335:76/8a, 336:18/56, 337:91/40, 338:f7/8a, 339:76/e8, 340:18/c0
  , 341:42/e4, 342:87/06, 343:ca/0a, 344:f7/cc, 345:76/b8, 346:1a/01
  , 347:8a/02, 348:f2/cd, 349:8a/13, 350:e8/66, 351:c0/61, 352:cc/0f
  , 353:02/82, 354:0a/54, 355:cc/ff, 356:b8/81, 357:01/c3, 358:02/00
  , 359:8a/02, 360:56/66, 362:cd/49, 363:13/0f, 364:61/85, 365:8d/71
  , 366:64/ff, 367:10/c3, 368:5e/4e, 369:72/54, 370:0a/4c, 371:40/44
  , 372:75/52, 373:01/20, 374:42/20, 375:03/20, 376:5e/20, 377:0b/20
  , 378:49/20, 379:75/00, 380:b4/00, 381:c3/00, 382:03/00, 383:18/00
  , 384:01/00, 385:27/00, 386:0d/00, 387:0a/00, 388:49/00, 389:6e/00
  , 390:76/00, 391:61/00, 392:6c/00, 393:69/00, 394:64/00, 395:20/00
  , 396:73/00, 397:79/00, 398:73/00, 399:74/00, 400:65/00, 401:6d/00
  , 402:20/00, 403:64/00, 404:69/00, 405:73/00, 406:6b/00, 407:ff/00
  , 408:0d/00, 409:0a/00, 410:44/00, 411:69/00, 412:73/00, 413:6b/00
  , 414:20/00, 415:49/00, 416:2f/00, 417:4f/00, 418:20/00, 419:65/00
  , 420:72/00, 421:72/00, 422:6f/00, 423:72/00, 424:ff/00, 425:0d/00
  , 426:0a/00, 427:52/00, 428:65/0d, 429:70/0a, 430:6c/4e, 431:61/54
  , 432:63/4c, 433:65/44, 434:20/52, 435:74/20, 436:68/69, 437:65/73
  , 439:64/6d, 442:6b/73, 443:2c/69, 444:20/6e, 445:61/67, 446:6e/ff
  , 447:64/0d, 448:20/0a, 449:74/44, 450:68/69, 451:65/73, 452:6e/6b
  , 454:70/65, 456:65/72, 457:73/6f, 458:73/72, 459:20/ff, 460:61/0d
  , 461:6e/0a, 462:79/50, 463:20/72, 464:6b/65, 465:65/73, 466:79/73
  , 467:0d/20, 468:0a/61, 469:00/6e, 470:00/79, 471:00/20, 472:49/6b
  , 473:4f/65, 474:20/79, 476:20/74, 477:20/6f, 479:20/72, 480:53/65
  , 481:59/73, 482:53/74, 483:4d/61, 484:53/72, 485:44/74, 486:4f/0d
  , 487:53/0a, 488:20/00, 489:20/00, 490:20/00, 491:53/00, 492:59/00
  , 493:53/00, 494:7e/00, 495:01/00, 497:57/00, 498:49/00, 499:4e/00
  , 500:42/00, 501:4f/00, 502:4f/00, 503:54/00, 504:20/00, 505:53/ac
  , 506:59/bf, 507:53/cc
1) Copy original to backup
2) Copy backup to original
3) No action

---

### Post by PmDematagoda on 2008-03-19
Well, I am not entirely sure as to what the best option would be. But in any case make sure that you have a Live CD and a Super GRUB CD at hand so that any problem you face can be easily fixed.

---

### Post by bigtel on 2008-03-19
I have a live CD but no super GRUB CD - I will search the forums to see if I can download one. Thanks for your help - I will update the thread once I have new news..!!

---

### Post by bigtel on 2008-03-19
OK I went for option 2 - Copy backup to original and after some 'buzzing' of my hard drive the terminal prompt appeared. I rebooted and hey presto...It worked..!! I now do not get one error message or numbers or anything.

Thanks for your help.

I have only been using Ubuntu for literally 2 weeks now, but hopefully I will learn to understand it better in the coming months...years..!!

---

### Post by Herman on 2008-03-19
> Does anyone know what this measn and if this effecting the system in any way? It wasn't a problem in Ubuntu, it's a possible problem that Ubuntu was trying to tell you about that Ubuntu was detecting in your Windows XP partition.

When your Windows boot sector isn't the same as it's backup it could be that the boot sector has been corrupted and you should restore the backup, or the back-up has been corrupted, but common sense suggests that would be less likely.

Maybe the corrupted boot sector was the reason you were having a few problems booting Windows XP.

The question is, how did your Windows boot sector get corrupted?
Windows boot sector is vulnerable to viruses, and antivirus programs aren't nearly as clever at detecting all viruses as they pretend to be. There are so many new viruses that they seem to be having a hard time keeping up. Try running on-line scans with several rival brands of anti-virus to your own and see if one of those can detect a virus in your Windows XP.

Ubuntu isn't vulnerable to viruses, so you can safely switch to Ubuntu when you're ready and you can say goodbye to viruses and time consuming antivirus programs and all kinds of other third party protection programs as well.

There are also different version of Windows boot sector available, so if you have used Windows FIXBOOT command, you might have installed a different version of the boot sector. As long as Windows is booting okay it probably doesn't matter.
Have you ever repaired your Windows boot sector with the FIXBOOT command or some similar command at a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") or using some other command from some other kind of a boot disk? If that's the case then you probably have nothing to worry about.

Regards, Herman  :)

---

### Post by bigtel on 2008-03-20
I did have some difficulty after I had installed Ubuntu with the duel boot option. I could not get my XP to boot at all. I kept getting an error message 'partition does not exist' (or something similar) 

I decided not to mess about too much and tried a boot CD with Partition manager to try and locate the partition and fix it. Well it detected an error straight away, fixed it (or so I thought) but I still could not boot XP.

I decided to take the plunge and I set up my Ubuntu a default and I will now remove XP totaly - I am not sure how to do that - perhaps just deleat everything on that particular partion (??)

I have notes of all my setings, passwords etc and I have extracted all my needed files and photo's. So far Ubuntu seems to be working really well.

I would like to dedicate the whole of my hard disc to it now, i.e. remove the partitions but I have no idea how to do it - Could you help??

---

### Post by PmDematagoda on 2008-03-20
You can use Gparted to remove the XP partitions.

Gparted can be installed using:-
```
sudo apt-get install gparted
```
It will be found in System>Administration>Partition Editor after installation.

If you do not want any partitions but the whole drive to belong to Ubuntu, then you may have to use the [Gparted Live CD]("http://gparted-livecd.tuxfamily.org/") to do that.

---

### Post by Herman on 2008-03-20
:) Sure! 

I agree with PmDematagoda and:

It's good that you have notes for all your settings, passwords, and so on.
Is your Windows file system mounted in Ubuntu?
Most of the time Ubuntu will automatically make a mount point in /media and an /etc/fstab entry for Windows so that you will have an icon on your Desktop that you can open and see your Windows files.
If not then you can mount it yourself, let me know if you need help. [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").
The first thing I would do would be to copy all your files from Windows and paste them into Ubuntu.
Many file types will open just as well in either operating system. Most image files, .html files, .pdf files and most music files will be able to be opened just as well in either operating system.
Nowadays some files like spreadsheets (.xlr files) can be opened with Open Office .org and easily saved as .ods file types. Back when I switched from Windows to Ubuntu I had to give up a lot of work or type it again manually. Now things are a lot easier, so try to convert any files you can.
There are certain files you probably can't do anything with like email, unless you resend it to your self somehow. That probably would work for a few of your most important emails, but it would be impractical to try to do that on a large scale. If you need to take email with you, you'd need to copy it to some other kind of document like word documents, and that might be a big job too. If you have important emails though, it might be worth considering, just for some of the important ones, any that may have sentimental value.

The partitioning part of the operation is the easy part. When you are absolutely certain that you have all your files backed up and/or transferred into Ubuntu, you can simply delete your Windows partition. You can use GParted in the Ubuntu Live CD for that. Just boot your Ubuntu Live CD and go 'System'-->'Administration'-->'Partition Editor', and select your Windows partition and delete it.
Or use [GParted -- LiveCD]("http://gparted.sourceforge.net/") as PmDematagoda suggested.
You have a choice. If you don't want to delete your Windows operating system completely after removing all the data out of it you can just resize it to a minimum size and leave it there in case you ever want it again for something. It doesn't take up very much room when it's reduced to a minimum size. If you've been having a lot of trouble with it it probably won't matter if you delete it, you can always install it again clean if you ever need to if you still have the CDs.

Now you will have either no Windows partition or a very small Windows partition and a lot of free space before your Ubuntu partition.
What would you like to do?
I imagine you will want to use all that free space for something, (Ubuntu).
Once again, you have some options to choose from. You could leave the free space for a few weeks and install Ubuntu Hardy Heron there when it gets officially released sometime soon, and then transfer your files from your current Ubuntu into Hardy Heron. That's what I would do.
You could even install Hardy early, but there will be a lot of updates to be downloaded every day and it's not recommended that anyone make it their main operating system yet at this point in time.

Or, you could use GParted Partition Editor to resize your Ubuntu Gutsy partition from the beginning, towards the left, something that was not possible not so long ago. I think even nowadays it will still be a slow process. I'm not sure. 
I find it quicker to copy and paste the whole partition to a new location on the hard disk. It's easier to do that without any files in it,  If you do, the partition numbers will be changed and you'll need to edit /boot/grub/menu.lst to get it to boot properly again, but that's easy.

That's about it I think, let me know what items you need more details on, or if I left anything out, or if I made any mistakes.

Regards, Herman :)

---

### Post by bigtel on 2008-03-23
Thanks for your help on this. I have resized the partitions as you suggested and made myself a new one for my new install of Hardy Heron. I have removed all traces of XP and I have never been happier..!!:)

---

### Post by Herman on 2008-03-23
8) Cool!  You rock :guitar:
Well done and congratulations! 

Regards, Herman

---


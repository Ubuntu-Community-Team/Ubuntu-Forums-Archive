---
title: "Ubuntu installer won't recognise hard drive"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by The Thunder Chimp on 2012-08-30
[SIZE=2][SIZE=3]***Preamble***[/SIZE]
Alright here's the thing. I just got myself a new Dell XPS 8500 computer with Windows 7 pre-installed.
Now, I wanted to make a total factory-state backup before i touched anything and decided for the matter to use Clonezilla. Everything seemed to work just fine with the latter before it died on me with the red error message [I][COLOR=Red]No input device![/COLOR]

[/I][/SIZE][COLOR=Black][SIZE=2]A quick google search pointed out that the problem was most probably due to the lack of a partition table (or the like)*, *a problem that could be fixed by installing a Linux operating system.

I wanted to install  Ubuntu anyway (with the MATE user interface) so I decided to go for it.
[I][B][SIZE=3]
Problem[/SIZE]
[/B][/I]Oddly enough, the Ubuntu installer didn't recognise my computer's only hard drive. It's a 2TB hard drive with a 32GB supplementary Solid State Drive.  It just acts as if it wasn't there, asking me if the installation should proceed on the very USB that ran the installer.
I tried a Linux Mint 13 CD to see if anything was different and it wasn't.

There's this peculiar notification that appears upon opening the Disk Utility on the Live Ubuntu USB. It states the following :

[/SIZE][/COLOR]```
WARNING: The partition is misaligned by 512 bytes. This may result in very poor performance. Repartitioning is suggested.
```I've attached an image of the latter warning, see below.

Thanks for your help!

Don't be afraid to share your thoughts on the Clonezilla issue too!


[COLOR=Black][SIZE=2]
[/SIZE][/COLOR]

---

### Post by darkod on 2012-08-31
I'm not sure, but I think both issues could be related to the Intel SRT or what ever it's called. It seems they started selling machines where the ssd is used as fast cache or what ever, but the setup of the disks is sort of weird. It's some sort of weird raid array which is not a real raid array (you don't have two disks of same size).

Maybe it's not detecting the partition table correctly because of this setup. Of course you have one, otherwise windows won't be able to work at all. There is no way any OS can work on a disk without a partition table.

Note that if you really do have Intel SRT, it will be tricky (if not impossible) to install a dual boot and keep the ssd as fast cache drive. From what I have seen on the forum, the only situation where people were able to install a dual boot, was to "break" the "raid" setup, and that will make the disks work completely as separate disks.

---

### Post by The Thunder Chimp on 2013-01-29
I had decided to keep the fast cache for a while, but I'm now ready to break it in order to dual boot. Any tips or considerations? Any links or how-tos?

Thanks!

---

### Post by darkod on 2013-01-29
Sorry, I don't have any tutorials bookmarked for this specific case. I can tell you my opinion in general, and I'm sure google will turn out something. You might be able to do it without google in fact.

The first thing is getting rid of Intel SRT. If I'm not mistaken, there is an option to disable in windows, and after that in bios. Once you manage to do that, it's done.

After that boot the live mode with the ubuntu cd once, open terminal and delete any meta data on the disks with:
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb

When clean of meta data and SRT disabled, they will be considered as two separate disks sda and sdb.

---

### Post by oldfred on 2013-01-29
Several users experiences. Some installed to hard drives and some installed to SSD and will not use the Intel SRT.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> 
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
From 2011, so now older

---

### Post by The Thunder Chimp on 2013-01-29
Thanks guys everything worked out fine!
I used asymptoticFault's how-to from [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121) (posts 5 and 9)
I was happy to find out that I could keep the ISRT after all. And I installed the MATE desktop.

One last thing while I'm at it, if I had installed Ubuntu on the SSD (obviously incapacitating the ISRT), would I have seen a performance boost as opposed to my current hard drive installation?

Thanks again, it truly helped!

---

### Post by darkod on 2013-01-30
> **The Thunder Chimp said:**
> Thanks guys everything worked out fine!
I used asymptoticFault's how-to from [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121) (posts 5 and 9)
I was happy to find out that I could keep the ISRT after all. And I installed the MATE desktop.

One last thing while I'm at it, if I had installed Ubuntu on the SSD (obviously incapacitating the ISRT), would I have seen a performance boost as opposed to my current hard drive installation?

Thanks again, it truly helped!

Of course. That's true for any OS or program. The SSDs (even the sh*tty ones) have very low access time which makes things pop up much faster. Most of them also have higher transfer rate than mechanical HDDs.

---

### Post by The Thunder Chimp on 2013-01-31
> **darkod said:**
> Of course. That's true for any OS or program. The SSDs (even the sh*tty ones) have very low access time which makes things pop up much faster. Most of them also have higher transfer rate than mechanical HDDs.

I concur! I've reinstalled on the SSD and have 24-second boot times. I just can't believe it!

---


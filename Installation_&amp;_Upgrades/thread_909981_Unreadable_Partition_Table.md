---
title: "Unreadable Partition Table"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Presario on 2008-09-04
Hello guys, I have a problem here...

Linux installation CDs/DVDs can't recognize my partition table but when I used the terminal through a live cd, i used the commands testdisk, fdisk and they can see them. So I guess it's gparted's bug becasue since all of the linux installers uses gparted to partition itself. (correct me if i'm wrong)

So everytime it's at the part where it time to partition my hard disk, it will show no partitions at all. That means I can't install linux anymore without disturbing the rest of my partitons.

Anybody managed to solve this problem?

I even tried to re write my MBR using testdisk, but it made my vista not bootable... I really want to install linux back cause i need to do some work there....:(

I predict it's just my partition table that I have now is not compatible with gparted.

I have to say again, I have installed ubuntu studio before in this laptop.

It all started when I removed the linux partitions to try out ox86. I guess it messed up my MBR.


EDIT: hey this guy here also have exactly the same problem as mine ---> [http://ubuntuforums.org/showthread.php?t=365328](http://ubuntuforums.org/showthread.php?t=365328)

---

### Post by caljohnsmith on 2008-09-04
Yes, it definitely sounds like a problem with your partition table. You can use testdisk to recover it if you are careful. Try the following:
```
sudo testdisk
```
Then "create log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Then do "proceed", "Y" to find Vista partitions, and see if it finds your Vista partition. If it finds your Vista partition, select "enter", and then you can write a new partition table. If it doesn't find Vista, hit enter and select "search!" so it does a deeper search. I think you can take it from there, but let me know if you need more details/info. Let me know how it goes. :)

---

### Post by Presario on 2008-09-05
caljohnsmith, I've tried building my partition table back with testdisk, but it makes my vista unbootable... that's what confuses me, it doesnt even get to the windows loading screen


```
BIOS------------           x-------->Vista Load Screen-------->Vista Login-------->Desktop
  ^            |
  |            |
  --------------

```

this is how it will look like, it's a boot cycle.

Maybe I could record a video of me using testdisk to rebuild my tabe and then u can see the effect.
But I will try it again, maybe I did something wrong and missed a step, making it unbootable.:???:

---

### Post by caljohnsmith on 2008-09-05
After you use the "search!" function in testdisk to do a deep search, can you post the output? That would give us something to go on. Also post the output of:
```
sudo fdisk -lu
```

---

### Post by Presario on 2008-09-06
> **caljohnsmith said:**
> After you use the "search!" function in testdisk to do a deep search, can you post the output? That would give us something to go on. Also post the output of:
```
sudo fdisk -lu
```

okey will do it and show you the results.

---

### Post by Presario on 2008-09-06
Okey this is the results that i got.

BTW, do you know how to mount an external hard drive/ a partition from gparted livecd so that you can transfer some files to and fro? cause it would be easier if I could transfer the screenshots or logfiles that I made in gparted to my external harddrive/ data partition so that I can post it here later clearly.

-----------------------------------------------------------------
[SIZE="5"]**[COLOR="Sienna"]This is the result for "sudo testdisk":[/COLOR]**[/SIZE]

[IMG]http://i8.photobucket.com/albums/a43/Chumbucket1991/Image200.jpg[/IMG]


[COLOR="Sienna"]**[SIZE="5"]This is the deeper search results (quick search):[/SIZE]**[/COLOR]

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 256 / 238 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start         End       Size in sectors
HPFS - NTFS            20887 254 63 31158 253 62       165003552







[Continue]
```
[COLOR="Sienna"][SIZE="3"][B]
after i click "Continue",[/B][/SIZE][/COLOR]

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start         End       Size in sectors
D FAT32 LBA                0  1  1     1273 254 63    20466747 [PQ SERVICE]
D HPFS - NTFS           1274  0  1    10616 254 63   150095295 [VISTA]
D HFS                  10617  0  1    15126 254 63    72453150
D Linux Swap           15848  1  1    16273 254 63     6843627
D Linux Swap           17912  1  1    18337 254 63     6843627
D HFS                  20464  1  1    20887 254 63     6811497
D HPFS - NTFS          20888  0  1    30401 254 63   152842410 [DATA]









Structure: Ok.   Use Up/Down Arrow keys to select partition.
(More instructions below, just that I didnt put it in)
```

Note that D=Deleted it says at the "more information below"




[SIZE="5"][COLOR="Sienna"]**And this is the "Sudo Testdisk -lu" results:      (I or L i cant remember)**[/COLOR][/SIZE]

[IMG]http://i8.photobucket.com/albums/a43/Chumbucket1991/Image202.jpg[/IMG]


Do you need any more information?
My Windows XP installer disk can detect my Vista, PQ Service and Data partitions and also the ubuntu live CD.

---

### Post by Sef on 2008-09-07
Try using the [GParted Live]("http://gparted.sourceforge.net") CD and see if that works.

---

### Post by Presario on 2008-09-07
> **Sef said:**
> Try using the [GParted Live]("http://gparted.sourceforge.net") CD and see if that works.

I have used the gparted live CD... and tried rewriting the MBR when it states everything correct on the screen... then my vista wont boot till I repair it with the CD.

Detailed: Gparted live cd still cant see my partition table when I start the partitioner and i tried to fix it using testdisk and like I said before, Vista wont boot.

---

### Post by caljohnsmith on 2008-09-07
Please post the output of:
```
sudo fdisk -lu
```
(Note that it is fdisk, and not testdisk like you posted previously). :)

---

### Post by Presario on 2008-09-08
> **caljohnsmith said:**
> Please post the output of:
```
sudo fdisk -lu
```
(Note that it is fdisk, and not testdisk like you posted previously). :)


Ouh haha didnt realise that... I'll get the results as soon as possible.


-------------------------------------------------------------------------

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x86b13155

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20466810   170562104    75047647+   7  HPFS/NTFS
/dev/sda3       335565720   488408129    76421205    7  HPFS/NTFS
```

okey this is what i got... everyting seems fine here..

---

### Post by caljohnsmith on 2008-09-08
I think I might know what is happening. From your post #6, you have a 90 MB hda drive that testdisk found. So if you run gparted from the Live CD with:
```
gksudo gparted
```
When gparted comes up, are you sure you have "sda" and not "hda" selected in the box in the upper-right corner of gparted? If you click that box, it will give you a list of your drives. Let me know if that is the problem.

Also, I forgot to mention earlier, but you will save yourself a lot of headache if instead of using gparted to partition your HDD, you instead use Vista's Disk Management. That's because Vista maintains its own partition table of your HDD separate from the main partition table in the master boot record of your HDD. So if you change your partitioning with anything other than Vista's Disk Management, you will probably not be able to boot into Vista after that until you fix Vista's partition table.

---

### Post by Presario on 2008-09-08
> **caljohnsmith said:**
> I think I might know what is happening. From your post #6, you have a 90 MB hda drive that testdisk found. So if you run gparted from the Live CD with:
```
gksudo gparted
```
When gparted comes up, are you sure you have "sda" and not "hda" selected in the box in the upper-right corner of gparted? If you click that box, it will give you a list of your drives. Let me know if that is the problem.

Also, I forgot to mention earlier, but you will save yourself a lot of headache if instead of using gparted to partition your HDD, you instead use Vista's Disk Management. That's because Vista maintains its own partition table of your HDD separate from the main partition table in the master boot record of your HDD. So if you change your partitioning with anything other than Vista's Disk Management, you will probably not be able to boot into Vista after that until you fix Vista's partition table.

Ok I'll double check with my self again about that, but for what I can remember, I know at the top right, there is this drop down list that lets you choose the media and I'm sure that gparted recognize it as sda. and I can remember from the previous installation of my ubuntu, i installed it on sda.


and about vista with it's MBR issue, i can remember clearly that when the first time i install ubuntu into my laptop, I did not mess around with the Disk Management, I shrinked it with acronis and then installed ubuntu with grub as the main boot loader and it managed to boot vista flawlessly without me editing grub stuff or what ever... during grub installation, it recognized my vista partition.

I'll try to get you a screen shot of gparted running.

And FYI, all (approx 8 CDs) of the Linux live cds and installation cd, it cant recognize my partition table, either saying there's no partitions or there is some kind of an error.

---

### Post by Presario on 2008-09-10
Here's the screen shot of the gparted window... so I'm quite sure that I selected the right disk.



[IMG]http://i8.photobucket.com/albums/a43/Chumbucket1991/GpartedRight.png[/IMG]
[IMG]http://i8.photobucket.com/albums/a43/Chumbucket1991/GpartedLeft.png[/IMG]


I guess my problem is just that I need to rebuild my partition table correctly for gparted to see it cause I need to install linux on my laptop. Without gparted able to see my partitions, I cant install them.

---

### Post by caljohnsmith on 2008-09-10
> **Presario said:**
> 
I guess my problem is just that I need to rebuild my partition table correctly for gparted to see it cause I need to install linux on my laptop. Without gparted able to see my partitions, I cant install them.
Can you boot into Vista right now? Or is your HDD not bootable at all? Like I mentioned earlier, it will usually save you headaches if you can use Vista's Disk Management to repartition your HDD anyway, since Vista has its own partition table outside of the MBR partition table. If you can't boot into Vista, do you have the Vista Recovery/install CD/DVD? From there you can run the command:
```
bootrec /fixmbr
```
And it will give you back your Vista MBR, which should allow you to boot Vista if your partition table is not too munged yet.

---

### Post by Presario on 2008-09-11
Yeah I managed to boot to vista for quite sometime already... I had to use the repair cd and it fixed it automatically.... but I still plan on getting linux on my laptop still.... but i dun think i can do that cause gparted still wouldnt recognize my partition table for me to actually choose a partition to install in (eventhough I have created the needed partitions in vista)

IS there a way to actually fix my partition table "properly" so that the install cds could recognize it?

---

### Post by caljohnsmith on 2008-09-11
> **Presario said:**
> Yeah I managed to boot to vista for quite sometime already... I had to use the repair cd and it fixed it automatically.... but I still plan on getting linux on my laptop still.... but i dun think i can do that cause gparted still wouldnt recognize my partition table for me to actually choose a partition to install in (eventhough I have created the needed partitions in vista)

IS there a way to actually fix my partition table "properly" so that the install cds could recognize it?
The only good, free partition table editor that I know of is testdisk. Also, based on your previous fdisk output you posted, you have a lot of unused space on your HDD:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20466810   [COLOR="Red"]170562104[/COLOR]    75047647+   7  HPFS/NTFS
/dev/sda3       [COLOR="Red"]335565720[/COLOR]   488408129    76421205    7  HPFS/NTFS
```
Notice how sda3 starts way beyond where sda2 stops. I would go back into Vista's Disk Management and resize your partitions so you use all that space. Making those changes might be enough to make gparted happy again and able to see your HDD's partitions.

---

### Post by Presario on 2008-09-12
> **caljohnsmith said:**
> The only good, free partition table editor that I know of is testdisk. Also, based on your previous fdisk output you posted, you have a lot of unused space on your HDD:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20466810   [COLOR="Red"]170562104[/COLOR]    75047647+   7  HPFS/NTFS
/dev/sda3       [COLOR="Red"]335565720[/COLOR]   488408129    76421205    7  HPFS/NTFS
```
Notice how sda3 starts way beyond where sda2 stops. I would go back into Vista's Disk Management and resize your partitions so you use all that space. Making those changes might be enough to make gparted happy again and able to see your HDD's partitions.

Yeah I'm aware that I have a big empty space in between sandwiched by my vista and data partition, and that's where I want to put my linux at...

Does that makes a difference? because the laast time, I installed linux, it was in between those partitions.....

IT goes like this: 

PQ Service - Vista - **EMPTY SPACE** - Data

---

### Post by caljohnsmith on 2008-09-12
> **Presario said:**
> Yeah I'm aware that I have a big empty space in between sandwiched by my vista and data partition, and that's where I want to put my linux at...

Does that makes a difference? because the laast time, I installed linux, it was in between those partitions.....

IT goes like this: 

PQ Service - Vista - **EMPTY SPACE** - Data
That's fine if you want to put linux in that empty space, I'm just recommending that you use Vista's Disk Management to set up those partitions rather than Ubuntu's gparted. You'll need to set up that empty space as an "extended" partition (not a "primary" partition), and then within that you can create two logical partitions: one for the main Ubuntu install, and one for swap. That's one way of doing it at least.

---

### Post by Presario on 2008-09-12
> **caljohnsmith said:**
> That's fine if you want to put linux in that empty space, I'm just recommending that you use Vista's Disk Management to set up those partitions rather than Ubuntu's gparted. You'll need to set up that empty space as an "extended" partition (not a "primary" partition), and then within that you can create two logical partitions: one for the main Ubuntu install, and one for swap. That's one way of doing it at least.

I tried experimenting with the vista disk management to find our about how far the extended partition can hold other small partitions and i had some fun for a while... but im not too sure if gparted could still regocnize it after filling it with the extended partitions... 

how do you install linux without using gparted? issit through the terminal or smthin? never tried that.

---

### Post by Presario on 2008-09-17
I filled the empty space already with an extended partition... but gparted still wont see it. even when I install with the live CDs.:mad:

---

### Post by Presario on 2008-10-10
aww man... no body solved this before?

I can't start installing the OSes from a cleaned out hard disc coz i have too much important information to delete..

---


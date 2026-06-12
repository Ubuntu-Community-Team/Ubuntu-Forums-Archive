---
title: "partitions?"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by pwnage101 on 2008-06-11
i've installed ubuntu/kubuntu successfully before making multiple partitions for each installation.  if i remember correctly, one partition was for the OS, one for the "home" directory, and one for swap memory.

what i would do is pop in the liveCD, and partition away using gparted (ext2 if i remember correctly).

i've decided to give linux another go but i dont know if it's the same for ubuntu 8.04.  should i just keep doing what i'd do for any other ubuntu installation?



just to give you an idea of my situation:
-160gb HDD
-vista x64 takes up 75gb
-85gb free space

what i want to do is make another partition for storage too.  if i do that, the vista partition should shrink to under 70gb, leaving at least 90gb for storage and linux. if i factor in the 10gb of flexibility to leave for vista, that means 80gb free space for storage and linux.

what should i format these partitions to? fat32, ext2, etc....

---

### Post by zvacet on 2008-06-11
>  if i remember correctly, one partition was for the OS, one for the "home" directory, and one for swap memory.

It is same with Hardy,so you can partition as you use to.To make Vista to see Ubuntu partition download and install [this driver]("http://fs-driver.org/") on your Vista partition.Ubuntu filesystem format is ext3.

---

### Post by pwnage101 on 2008-06-11
thanks for the clear and simple answer!

however, i'm running into problems with the liveCD
when i pop in the CD and restart, the main menu comes up and i hit the first choice which is the one that lets you try out the OS and/or install it.

after the "Ubuntu" loading screen, a bunch of error messages go down the screen that consist of input/output falures and video buffer failures. every once in a while i see a red "[Fail]" on the right side of the screen.

how can i fix this?  i need to get into the live CD to partition the HDD using Gparted.

currently, my LCD monitor (1680x1050) is directly hooked up to the 8800gtx using a DVI cable. and i'm installing the x64 version of 8.04

---

### Post by zvacet on 2008-06-11
Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and disc integrity for errors?If you find any errors and you still have iso download same iso with torrent and point download to the folder where your existing iso is.Torrent wil just check your iso for corrupted files and replace them wilth good ones.After that chech md5sum again,burn iso on lower possible speed and after that check disc for erors.If everything is fine go for install.

---

### Post by pwnage101 on 2008-06-11
yea found and error in one file. burned the CD at a slower speed and currently in the liveCD successfully

thanks a lot!

---

### Post by pwnage101 on 2008-06-12
one more thing about partitions. in gparted, before i modified the vista partition there was 1gb of unallocated space to the left.  after shrinking the vista partition, it moves the whole partition to the left diminishing this 1gb partition (or empty space or whatever it is).

isn't this the partition that stores backup information for windows?  is it safe to get rid of it with gparted? i'd like a working windows OS too:)

---

### Post by zvacet on 2008-06-12
I never worked with Vista,but if you have unallocated space that mean there is nothing there,and I believe it is not back up.If it is backup you will see how many space that files occupy.I can be wrong,so anybody can correct me.

---


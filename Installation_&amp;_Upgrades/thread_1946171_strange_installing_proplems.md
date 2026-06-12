---
title: "strange installing proplems"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by abdorefky on 2012-03-24
[SIZE=3]hi every one :[/SIZE]
[SIZE=3]its my first time with ubuntu ,and so far i can't install it [/SIZE]
[SIZE=3]i have windows 7 and windows 8 and i want to install ubuntu 11.10 on its own partition[/SIZE]
[SIZE=3]1: the setup cannot detect my other operating systems[/SIZE]
[SIZE=3]2: the setup cannot detect my partitions[/SIZE]
[SIZE=3]i will let the photos explain[/SIZE]
[SIZE=3]*this is the first thing after choosing language[/SIZE]
[SIZE=3]*as u can see nothing on desktop[/SIZE]
[IMG]http://img41.imageshack.us/img41/7950/screenshotat20120324130.png[/IMG]
 
[SIZE=3]after 30 min searching on forums those 2 icons just appeared when i was saving a photo [/SIZE]
[SIZE=3]any way this is the second photo[/SIZE]
[SIZE=3]I have another 2 operating systems >>> lol[/SIZE]
[IMG]http://img814.imageshack.us/img814/6484/screenshotat20120324131.png[/IMG]
[SIZE=3]and the third photo[/SIZE] 
[IMG]http://img716.imageshack.us/img716/6484/screenshotat20120324131.png[/IMG]
 
[SIZE=3]is there something should i do in that file system ?[/SIZE]
 
[IMG]http://img710.imageshack.us/img710/7418/screenshotat20120324133.png[/IMG]
 
[SIZE=3]now after i saw that file system .. i am totally confused [/SIZE]
[SIZE=3]best thing that : i am trying to install , and using the internet at the same time [/SIZE]
[SIZE=3]i hope some one answer me [/SIZE]
[SIZE=3]any way i am still trying [/SIZE]
[SIZE=3]sry if my english sux [/SIZE]
[SIZE=3]ty[/SIZE]

---

### Post by abdorefky on 2012-03-24
[SIZE=3]wow .. the install see every partition as 160 GB :([/SIZE]
[IMG]http://img31.imageshack.us/img31/5876/screenshotat20120324141.png[/IMG]

---

### Post by abdorefky on 2012-03-24
i go try make the driver unallocated space :mad:

---

### Post by miegiel on 2012-03-24
I would recommend to make the empty partitions for ubuntu root (aka /) and swap (same size as your RAM or larger) in advance of installing ubuntu. This often works better than doing it during the installation process. You can resize, reagange and make them in windows. Or you can start ubuntu from the CD (the "try ubuntu option) and do it with the *gparted* program. (Personally I prefer using the last method because it's safer to change partitions on your disk when you're not also running an OS on that disk.)

btw Those pics are really small :D

---

### Post by abdorefky on 2012-03-24
[SIZE=2]thank you  for responding miegiel
i am sorry because the photos was small but i have tried to make partition for the ubuntu but the install see's the harddisk as free space
i will try the  *gparted* program now [/SIZE]
[SIZE=4]any way can i create partition with that way ? >>[/SIZE] [SIZE=4]and what will happed to other partitions>> [/SIZE]
[IMG]http://img805.imageshack.us/img805/4060/screenshotat20120324165.png[/IMG]

---

### Post by cybpabeofm on 2012-03-24
Try using GPARTED to see if it sees your drive the same way. Do you have your hard drives raided? Can you give us ALL of you system hardware (CPU, GPU, RAM, ect)

---

### Post by abdorefky on 2012-03-24
allright Cybpabeofm I am downloaing that gparted,
I don't have raid hard drivers ,
my pc hardware is so poor :) 
945 mother board
duel core prossesor 3.00 cach 2 mb 
1 gb ram 667 
nivdia  6200 le 
---------

---

### Post by jmore9 on 2012-03-24
I used Gparted live cd.  You boot to the cd and can see evrything without much trouble.  You can also make and delete partitions - NTFS -EXT4 - EXT3 - FAT32 etc.  Give it a try and if you do pay close attention to which drive and partition you wish to work with.  It also has docs for it.

---

### Post by abdorefky on 2012-03-24
all right thank you [SIZE=2]jmore9[/SIZE]
but I still don't know which form should I convert my partition to , so the Ubuntu can see it. 
i still have windows 7 and windows 8 and scared to destroy there boot 
i go eat now 
brb 1 hour

---

### Post by darkod on 2012-03-24
If the partitions and the OSs are not detected correctly I wouldn't recommend to continue.

You need to find the reason first. For example, the disk might have raid meta data remains if it was used in raid before. Windows ignores that but ubuntu doesn't.

Also, the disk might be dynamic in windows, in which case DO NOT install ubuntu. In windows open Disk Management and check whether the disk is basic or dynamic. If it's dynamic that is MS format and ubuntu will not understand the partitions correctly so it is not good to install it.

---

### Post by abdorefky on 2012-03-25
[SIZE=3]thx darok[/SIZE]
[SIZE=3]but I think the proplem is not dynamic now < am I right ?[/SIZE]
[SIZE=3]also I dont know why windows 8 partition titled with green !!!![/SIZE]
[SIZE=3]the other thing u said is the metadata .. is it fixable ? [/SIZE]
 [SIZE=4]I have installed the gparted , it see's the hard disk as free space too !![/SIZE]
 
 
 
[IMG]http://img825.imageshack.us/img825/9574/allbasic.jpg[/IMG]
[SIZE=4][/SIZE]

---

### Post by darkod on 2012-03-25
The meta data is easily fixable but it doesn't look like that is your problem. You can try it anyway since it¡s obvious you are not running raid. Boot into ubuntu live mode and in terminal do:
sudo dmraid -E -r /dev/sda

If that asks you if you want to remove raid meta data, just confirm.

Also, lets take a look at the partitions from ubuntu point of view. While you are in live mode in terminal, post the result of:
sudo parted /dev/sda unit s print

That should show the partitions list as ubuntu sees them.

EDIT: The green border line means the extended partition that contains all the logical partitions. But I can notice the 8.54GB partition says is Primary but it is inside the extended partition which shouldn't be possible. I don't know whether because of the issue of not understanding the disk partitions correctly it tried to create a primary partition inside the extended. Only logical partitions can be inside it.

Lets see what the parted command says. With which tool did you create the 8.54GB partition, with Gparted from ubuntu live mode?

---

### Post by abdorefky on 2012-03-25
[SIZE=3]I have used EASEUS partition master home edition [/SIZE]
[SIZE=3]I also noticed the disk management see's windows 8 partition as logical and the program see's it as primary[/SIZE] 
[IMG]http://img31.imageshack.us/img31/2808/myhard.jpg[/IMG]

[SIZE=4]about the code u gave me I don't know where to type it :S[/SIZE]
[SIZE=4]but I have noticed a block appears on right corner appears when I start typing [/SIZE]I
[SIZE=4] have tried to type on it but nothing appeared [/SIZE]

---

### Post by abdorefky on 2012-03-25
ahh sry its on terminal I will go try now

---

### Post by abdorefky on 2012-03-25
[SIZE=3]I have tried : sudo parted /dev/sda unit s print[/SIZE]
[SIZE=3]and it gave me this [/SIZE]
[SIZE=3]Error : can't have overlapping partition [/SIZE]
[SIZE=3]edit : I go sleep because I have exam 11.30 am so u see soon [/SIZE]

---

### Post by abdorefky on 2012-03-26
[SIZE=4]here is the screen shot 
i have also tried  sudo fdisk -lu (i think it give some information of the hard )
is there other commanded should i use ?[/SIZE][IMG]http://img543.imageshack.us/img543/4317/screenshotat20120326131.png[/IMG]

---

### Post by darkod on 2012-03-26
I am not sure if EASUS did this, but somehow sda2 is inside the extended partition sda3 which is impossible.

The first thing to try would be to use EASUS again and delete the 8.54GB partition. Because you created it with EASUS maybe if you delete it it will return things to normal.

That would still leave a potential problem with sda8 because by deleting sda7 sda8 will remain outside the extended partition when it should be inside. But lets see. Delete the 8.54GB partition first with EASUS and we'll see if it helps.

If it doesn't, you still have the option to use fixparts and try to repair things.

In future try to avoid tools for partitions like EASUS, you have everything you need in Gparted on the ubuntu cd and windows Disk Management if working with windows partitions. These other tools can get confused it seems.

---

### Post by abdorefky on 2012-03-26
[SIZE=3]thank you very much darkod [/SIZE]
[SIZE=3]I go study the pic and what u told me :)[/SIZE]
[SIZE=3]in the main times I have suffered to get this photo from disk utility because the run mode freeze every 5 min :S[/SIZE]
 
[SIZE=3]any way after I saw that pic ........ [/SIZE]
[SIZE=3]I have found that I have 2 bad sectors [/SIZE]
[SIZE=3]and also I do have 226 GB hard disk + 18446744[/SIZE]
[SIZE=3]this Ubuntu is really cool ,[/SIZE]
[SIZE=3]but I wasn't know that I  have to study the whole hard disk before installing it :D[/SIZE]
[SIZE=3]now I have found that my hard on the edge[/SIZE] 
[SIZE=4]now I am sure that Ubuntu is much better than windows[/SIZE] 
[IMG]http://ubuntuforums.org/[[IMG]http://img38.imageshack.us/img38/5635/screenshotat20120326164.th.png[/IMG]](http://imageshack.us/photo/my-images/38/screenshotat20120326164.png/)[/IMG]

---

### Post by abdorefky on 2012-03-27
i will copy the data and format my disk and i will install the
windows 7 , windows8 , ubuntu 
is there a guide for booting problems ?
which operating should i begin with windows or ubuntu ?

---


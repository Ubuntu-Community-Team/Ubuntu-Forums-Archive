---
title: "installing 8.04 and use RAID 1 arrays"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by nvid1a on 2008-08-02
Hi there,

Im about to change a server from my office from windows 2000 advanced server to ubuntu 8.04 64-bit.

the server i have has the following configuration:

7 HDDs drives - 5 SATA2 and 2 IDE

1 SATA2 of 120gb has the operating system
2 SATA2 of 500gb are in BIOS nVidia RAID as RAID 1
2 SATA2 of 400gb are only separated disks for common storage

so that makes the 5 SATA2

the 2 IDE of 160gb remainin are on BIOS nVidia RAID as RAID 1 too.

The thing is, i read a lot about using RAID arrays in ubuntu with the nforce4 AMD chipset that im working on and it seems that this raid bios is useless in ubuntu, to see further i started the server booting ubuntu and it shows me all the disks separate and obviusly the RAID ones are duplicated as expected.

So i was starting too see that the best solution is to disarm the RAID from the bios and install ubuntu to proceed on Linux Software RAID, is this correct ? or i must keep the RAID set in BIOS ?.

The operating system will be on other HDD, so this 2 RAID 1 arrays i need are only for storage, also they are on ntfs right now so i was wondering that to make linux software raid work i need to format one disk of the array to ext then pass the information from the ntfs one to the new ext, format the the last ntfs from the array and then arm the linux software raid this way, repeating the same procedure with the other RAID 1 array. Is this a good way to do it ? or am i all wrong ?, im a little scared about cause i dont want to lose any data.

Can anyone help me with this ? or maybe i just keep the windows 2000 advanced server ?

Thanks.

---

### Post by redraiderbum on 2008-08-02
I just wrote this today if it will help:

[http://ubuntuforums.org/showthread.php?t=877967](http://ubuntuforums.org/showthread.php?t=877967)

I want to make sure I get the question right.  You want to preserve the data from the array while at the same time transferring to linux yes?  It seems like a difficult question because it depends on how your free space is configured.  If you want to disarm the arrays in bios you can then mount the ntfs volume and pass the info to a newly formatted ext partition.  I have done this before and it does work.

---

### Post by nvid1a on 2008-08-02
> **redraiderbum said:**
> I just wrote this today if it will help:

[http://ubuntuforums.org/showthread.php?t=877967](http://ubuntuforums.org/showthread.php?t=877967)

I want to make sure I get the question right.  You want to preserve the data from the array while at the same time transferring to linux yes?

thx that would help me a lot to make the array work.

going to your question yes, i want to preserve the data from the array while transferring to linux.

i dont know what to do first, you kept the sil raid controller with the arrys done on bios or just let the disks as normal sata to next join them as software raid ?.

thx!

---

### Post by redraiderbum on 2008-08-02
Is it possible for you to push all of the data you have on the two 160's off onto the raid1 500's before doing the ubuntu install?  

I guess I should ask, how much free space do you have and where is it?

---

### Post by nvid1a on 2008-08-02
> **redraiderbum said:**
> Is it possible for you to push all of the data you have on the two 160's off onto the raid1 500's before doing the ubuntu install?  

I guess I should ask, how much free space do you have and where is it?

its a good idea i have enough space in the other raid 1, but i have a practical problem with it, maybe logical.

some paths of the information in the 160gb raid 1 array, i mean this:

d:\work\project1\excel\... etc etc, some of them are too long.

sadly windows 2000 let you create them but when you try to copy or access them it fails saying that the path is too long and it can not read.

maybe i can pass the 95% of the information in it but i can not lose any byte of that data, is pretty critical.

---

### Post by redraiderbum on 2008-08-02
The best thing to do would be just to shorten the path and remember you did it then rearrange later.

So if you can unload all of the info the 500 raid1.  I would do that first and not disarm that raid yet.  Also, I would boot to an ubuntu live cd to make sure you can mount the data on at least one of the 500 raid1.  

Assuming you can do both of those and you don't need to preserve the data on the OS disk (if you do need to preserve it you could offload that somewhere also).  Then you could go ahead and install ubuntu on the 120 GB HDD.  Once the install has completed you can format the two 160's as individual drives for now (that is, not as a raid array so you have enough space).

That will give you approximately 420 GB of free space between the OS disk and two 160's.  If that is enough space, you can unload all of the data from the 500's on there.  Which will allow you disarm and raid from the bios without needing to pass info from one 500 to another (honestly that seems a little sketchy).

Then you can follow the guide to configure the first software raid1 with the two 500's.  Once that raid1 is finished you can transfer all of the data back to that array.  That will allow you to make the second raid1 with the 160's (if that is what you want to do).

---

### Post by nvid1a on 2008-08-02
> **redraiderbum said:**
> The best thing to do would be just to shorten the path and remember you did it then rearrange later.

So if you can unload all of the info the 500 raid1.  I would do that first and not disarm that raid yet.  Also, I would boot to an ubuntu live cd to make sure you can mount the data on at least one of the 500 raid1.  

Assuming you can do both of those and you don't need to preserve the data on the OS disk (if you do need to preserve it you could offload that somewhere also).  Then you could go ahead and install ubuntu on the 120 GB HDD.  Once the install has completed you can format the two 160's as individual drives for now (that is, not as a raid array so you have enough space).

That will give you approximately 420 GB of free space between the OS disk and two 160's.  If that is enough space, you can unload all of the data from the 500's on there.  Which will allow you disarm and raid from the bios without needing to pass info from one 500 to another (honestly that seems a little sketchy).

Then you can follow the guide to configure the first software raid1 with the two 500's.  Once that raid1 is finished you can transfer all of the data back to that array.  That will allow you to make the second raid1 with the 160's (if that is what you want to do).

ok, seems all good with this.

just to make sure, to make linux software raid work i must have the disk in raid mode in nVidia BIOS too ?

---

### Post by redraiderbum on 2008-08-02
No the software raid will be done through ubuntu not through the bios raid controller so when you get to doing a raid1 with the 500's you will probably want to turn it to native mode rather than raid(although I'm not sure it matters which way it is set).  When using mdadm you will be creating the array at the OS level from separate partitions.

I just wouldn't touch the 500's until you have everything saved on the other drives.  At the very least, if the process gets fudged up somewhere you could reinstall windows and just mount the 500's with no loss of data.

---

### Post by nvid1a on 2008-08-02
> **redraiderbum said:**
> No the software raid will be done through ubuntu not through the bios raid controller so when you get to doing a raid1 with the 500's you will probably want to turn it to native mode rather than raid(although I'm not sure it matters which way it is set).  When using mdadm you will be creating the array at the OS level from separate partitions.

I just wouldn't touch the 500's until you have everything saved on the other drives.  At the very least, if the process gets fudged up somewhere you could reinstall windows and just mount the 500's with no loss of data.

ok, you are right in the last point, i understand the first too.

in the 120 hdd where the OS is, windows 2000 is in one partition of 60gb ill put ubuntu in the other half and install grub to get dual boot in case something goes wrong.

you really helped me out, very much thanks.

---

### Post by redraiderbum on 2008-08-02
Sounds good.  Hope it goes well!

---


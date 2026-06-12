---
title: "having trouble installing from burned cd"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by smarite_on_computer on 2006-04-27
hey i have done a little search in this forums but i am unable to find any thing simular to my problem

i've download the iso file from [http://ftp.citylink.co.nz/ubuntu-releases/5.10/ubuntu-5.10-install-i386.iso](http://ftp.citylink.co.nz/ubuntu-releases/5.10/ubuntu-5.10-install-i386.iso)
i've extrated it to a folder then wrote it to a bootable cd.

i run the cd when i restart the computer but it comes up with completely different to what i was told it would show.

did i do something wrong or was i not ment to extract iso file???

can any body help?

Thanks

---

### Post by jazzmuzik on 2006-04-27
You shouldn't have extracted the iso. You want to keep it as an iso and burn it to a disk. And you want to tell your burning software that it is an iso file, i.e., burn it in iso (or image) mode, not data mode.

---

### Post by smarite_on_computer on 2006-04-27
thanks i did not know that. :)
ill try it and see what happens

im just a newbie to linux, i was sujested it because windows kept on playing up on me 

thanks

---

### Post by confused57 on 2006-04-27
You need to burn the iso file as an image.  If you have Nero, there should be an option to copy or burn as an image(image is the keyword).  In Roxio, you may be able to just right click the iso file and Roxio will automatically burn it as an image.  Also, burn the iso at a lower speed(4x-8x max); you'll have a better chance that the burn will not be corrupted.  If you really want to be sure about the iso you downloaded, you need to do a md5checksum verification.  If you have any more questions, there's always someone willing to assist.
Here's the link for the checksum I use:

[http://www.md5summer.org/download.html](http://www.md5summer.org/download.html)

---

### Post by jazzmuzik on 2006-04-27
As confused57 was saying, the md5 verification of the iso (basically a checksum to see if the iso file is perfect bit for bit) is a step you can skip, but if you can you should do it. That's the only way to know if the iso file you downloaded is good. Downloading a file that large can have errors, and certain ways of downloading, like via http, are more prone to introducing errors than other methods.

I'm not sure how to do an md5 check in Windows. There's a utility somewhere for it. Basically you compare a long number (32 characters I believe) computed from the iso to the number the iso should be. Hope that makes sense. It takes a several minutes to do the test.

---

### Post by smarite_on_computer on 2006-04-27
great, works now how do i get to install witout eraseing hdd?

---

### Post by confused57 on 2006-04-28
I'm not sure what you mean by not erasing HDD, if you already have an operating system on your computer and want to dual-boot, here's an excellent guide:

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by smarite_on_computer on 2006-04-28
i have two hard drives.
the first has win xp
the seccond has my download files and other importaint stuff
i want to install ubuntu on the hard drive without deleting the documents

hardrive one is to small to stick anything on it :rolleyes:

---

### Post by confused57 on 2006-04-28
I'm new at Linux also, so I'm not qualified to give you any instructions on actually how to do what you have in mind.
There are Linux partitioning tools, such as gparted, qtparted, Disk Drake that can be run from a LiveCD to repartition with.  As with any partitioning tool, and during installation there is always a chance of data loss.  You may be able to shrink the partition your data is on and free up space to install Ubuntu on and you'll be dual-booting.
What you want is fairly involved for anyone relatively new to Linux.  Someone experienced with what you have in mind  will hopefully guide you through it or give you some useful links.

If you haven't already, try running a Ubuntu LiveCD on your system to see if there may be any hardware compatibility problems before attempting to install.

---

### Post by jazzmuzik on 2006-04-28
Look for instructions on how to repartition your drive without destroying the existing data. Going into detail is beyond what I can do on these forums. But basically you want to make the Windows partitions smaller so you can create room for Linux.

---

### Post by smarite_on_computer on 2006-04-28
ok, i've installed it now and looks great!!! :p
ok, now how do i use it???
some tutorials would be nice because, i was using it works a bit like windows, but the file system is different, how do i access hard drice c: and d: ?
i tried it, but came with error, 'access is denied'. can any boby help

thanks

---

### Post by confused57 on 2006-04-28
Good job getting it installed,  here's some links which may help:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)
[http://www.lowfatlinux.com/?aw2b](http://www.lowfatlinux.com/?aw2b)

Your hard drives will be listed as hda and hdb, and accessing them will
involve "mounting", see the 1st link, where you also might want to check the
partitioning of your harddrives.  The 2nd link will give you some idea of the filesystem used in Linux.

---


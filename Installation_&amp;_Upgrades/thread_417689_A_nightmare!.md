---
title: "A nightmare!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by eldhund on 2007-04-21
Hello!

The most horrible thing happened! I tried to install the latest Xubuntu release o my PC. Xubuntu asked if I liked to migrate my XP documents and I said yes. Then the Widows partition was deleted and now I only have a Linux partition. I canceled the installation but still my windows partition is gone and I only have one big linux partition. I had so much important documents on that Windows partition. Can somone help me to save my docs and recover my win partition?

best regards

---

### Post by Swab on 2007-04-21
This is not good.  I don't think you are going to get your data back.   

Anyone got any suggestions?

---

### Post by thegreenman on 2007-04-21
First try using this [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) 

The application called photorecovery which is bundled with this can actually find doc or pdf  or text files too.  I used this two days ago to recover 3 years worth of valuable photos and home movies which I accidentally formatted in linux over windows xp. 

It worked for me and it's free.

---

### Post by FLPCGuy on 2007-04-22
> **eldhund said:**
> Hello!

The most horrible thing happened! I tried to install the latest Xubuntu release o my PC. Xubuntu asked if I liked to migrate my XP documents and I said yes. Then the Widows partition was deleted and now I only have a Linux partition. I canceled the installation but still my windows partition is gone and I only have one big linux partition. I had so much important documents on that Windows partition. Can somone help me to save my docs and recover my win partition?

best regards
After 20 years of computing I was 'just fooling around' one day and wiped and reformatted my Windows NTFS partition because I got two drives mixed up.  I hadn't added any files to the new partition. Partition Recovery got all my files back and repairing Windows restored all my installed software (much of it old downloads that can't be replaced).   Some long filenames didn't make it.  PR isn't free, but you can download a preview version that will show you exactly what can be recovered before you buy.  This menu driven app is very simple to use.  It costs about $30 for the license key.    Just Google for Partition Recovery.

I never did find a free or open source alternative.   Email support is included when you buy...nice folks.  I think you will also need to boot from a floppy, though I imagine you could also run it from a bootable CD.  There are imitations out there but I believe this is the original.  If you installed a new OS, any cluster that happened to overwrite a portion of your old files with new ones cannot be recovered except by drive experts [$1,500 up].

For future reference, an external USB HD costs under $100,  DVD-burners less than $50.  Nothing beats the timely backup of unique personal files and entire partitions for that matter (see Partimage.org) to a separate drive or media.  We all get caught eventually. Sorry for your loss.

---

### Post by solarix on 2007-04-22
> **FLPCGuy said:**
> After 20 years of computing I was 'just fooling around' one day and wiped and reformatted my Windows NTFS partition because I got two drives mixed up.  I hadn't added any files to the new partition. Partition Recovery got all my files back and repairing Windows restored all my installed software (much of it old downloads that can't be replaced).   Some long filenames didn't make it.  PR isn't free, but you can download a preview version that will show you exactly what can be recovered before you buy.  This menu driven app is very simple to use.  It costs about $30 for the license key.    Just Google for Partition Recovery.

I never did find a free or open source alternative.   Email support is included when you buy...nice folks.  I think you will also need to boot from a floppy, though I imagine you could also run it from a bootable CD.  There are imitations out there but I believe this is the original.  If you installed a new OS, any cluster that happened to overwrite a portion of your old files with new ones cannot be recovered except by drive experts [$1,500 up].

For future reference, an external USB HD costs under $100,  DVD-burners less than $50.  Nothing beats the timely backup of unique personal files and entire partitions for that matter (see Partimage.org) to a separate drive or media.  We all get caught eventually. Sorry for your loss.


I agree with you but it seems you never took a look on testdisk.

I used it for several Filesystems

UFS  Ntfs ext3 and it worked great, it´s a great tool to restore a destroyed Partition Table.

---

### Post by Candace on 2007-05-02
Hi,

Okay, I did the same thing - overwrote my Windows partition when I installed Linux. I'm a newbie, too. :-\  I have downloaded and extracted the files for TestDisk but I am not sure what to do now. I don't know how to run them. Any pointers? I actually don't really need to recover all my documents because I backed everything up except for 2 docs which are semi-important. I can retype them though. 

Mostly, I think I just want to have a Windows to boot up if I need to, but I don't understand logically what to do. Do I just need to do a fresh install of Ubuntu and leave room (how much?) for windows as a NTFS primary partition at the beginning? And then boot Windows from CD and install that without making any partitions? I have never booted Windows from CD so I am not sure what steps it will take me through. Step by step instructions would be appreciated.

Thanks, Candace

---


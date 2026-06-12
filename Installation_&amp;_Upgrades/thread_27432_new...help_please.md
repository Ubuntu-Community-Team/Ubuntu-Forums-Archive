---
title: "new...help please"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by wolfesidhe on 2005-04-16
[COLOR=Indigo]Hello.        I am new to linux for the most part. I've only ever used a live cd of different versions. I have 2 hard drives (a 40 and an 80 gig), and have windows 98 se on the 80gig.  I'd like to install ubuntu on the 40 gig, but I would like to get some advice (instructions?) on how to do it.   There are some of the windows files on the 40 gig drive (which I think windows put there by default).  I just got a copy of partition magic 8 and don't really know how to use it yet.  I've done a google search and couldn't really find anything that was in layman's terms. Could someone please post a walkthrough for this for me?

Many thanks in advance  :) 
WolfeSidhe[/COLOR]

---

### Post by kori.mendocino on 2005-04-16
it would be best if you completely erase the 40gig drive, or at least the partition you wish to install ubuntu to, because fresh is always best.

you might want to use partition magic to format the drive the right way before the installation process, but you can do it with the ubuntu installer, too (though its a lot prettier and simpler with partition magic).

now, if you chose to use some kind of partitioning tool before-hand, erase the whole 40gb drive or the partition on it you are going to use. from the now free space, you basically need to create four partitions - the first is your **root directory**, /, where all your system stuff is placed, the second one - the **/usr directory**, where all your software is, a **swap partition** and **/home**.

you don't need more than 3-4gb on neither **/** nor **/usr**, and no more than twice your RAM size for the swap partition. if you distribute 3gb on /, 3gb on /usr and, say, 800mb on swap, you can use all the remaining space for /home, as it is the place where you will place all your stuff - all your downloads, configuration files, documents, pics, movies, etc

dont forget, that you need to create the partitions with a linux-friendly filesystem, like ext2, ext3, reiserfs, etc. since you're new, better use ext3.

now, after you do all this, double check if there isnt some bad option so you won't erase all your windows stuff, and push the button.

later on, in the installation process, when the time comes to edit the partition tables, choose 'manually edit the partition tables' and edit the options for each partition, like what filesystem it is (set 'ext3' on the ext3 partitions and fat32 or ntfs for your windows partitions), where is it mounted (/, /usr, /home, swap and stuff). for the swap partition, you have to choose 'swap' filesystem, i reckon.

and that's all, basically. have fun:)

---

### Post by ijsje on 2005-04-16
[QUOTE=wolfesidhe]I have 2 hard drives (a 40 and an 80 gig), and have windows 98 se on the 80gig.  I'd like to install ubuntu on the 40 gig, but I would like to get some advice (instructions?) on how to do it.
[/QUOTE]
I presume you want a dual boot setup, so you can choose between windows 98 and ubuntu at startup. The ubuntu installer will do this by default.

> There are some of the windows files on the 40 gig drive (which I think windows put there by default).

Is the 40gb or the 80gb hard drive your C-drive? The 40gb will contain some files like the boot.ini if it's the C-drive, otherwise there's nothing to worry about.

> 
I just got a copy of partition magic 8 and don't really know how to use it yet.  I've done a google search and couldn't really find anything that was in layman's terms. Could someone please post a walkthrough for this for me?

You can keep the 80gb hard-drive with windows like it is now, and install ubuntu at the 40gb drive. Only the files at the 40gb drive will be erased, but you have no files stored at the 40gb drive except for some files windows put there by default. The ubuntu installer can partition the the 40gb drive, so there is no need for partition magic.

If you install ubuntu make sure you don't select the option to erase your 80gb hard drive. I recommend making a backup of your important files so you won't loose those files if you format the windows drive by mistake.

You can partition the 40 gb drive like kori.mendocino described. You should create the root partition and swap partition in any case, the /usr and /home are optional, if you don't create them they will use the root partition. The thing about having a seperate home and usr partition is that the (important) root partition will always have free space left if the home directory gets out of space. So it's safer. And as kori.mendocino mentioned, it's best to choose ext3.

---

### Post by wolfesidhe on 2005-04-16
[QUOTE=kori.mendocino]
now, if you chose to use some kind of partitioning tool before-hand, erase the whole 40gb drive or the partition on it you are going to use. from the now free space, you basically need to create four partitions - the first is your **root directory**, /, where all your system stuff is placed, the second one - the **/usr directory**, where all your software is, a **swap partition** and **/home**.
[/QUOTE]
 
  Forgive me for being a newbie :) I just want to make sure I do it the right way to begin with to avoid having to reformat and reinstall everything all over again lol.   For those partitions I need to create, would they be logical or primary? 

[QUOTE=kori.mendocino]you don't need more than 3-4gb on neither **/** nor **/usr**, and no more than twice your RAM size for the swap partition. if you distribute 3gb on /, 3gb on /usr and, say, 800mb on swap, you can use all the remaining space for /home, as it is the place where you will place all your stuff - all your downloads, configuration files, documents, pics, movies, etc[/QUOTE]
 
I have 640 mb of ram, so I would double that amount for the swap? and the root and usr should be about 3-4 gb? 

Thanks for your response and your patience with a newbie :)

WolfeSidhe

---

### Post by wolfesidhe on 2005-04-16
[QUOTE=ijsje]I presume you want a dual boot setup, so you can choose between windows 98 and ubuntu at startup. The ubuntu installer will do this by default.[/QUOTE]
Yes, that's exactly what I was wanting to do. Should I still use the boot magic program that came with partition magic? Or will another bootloader be installed in the process of installing ubuntu?


[QUOTE=ijsje]Is the 40gb or the 80gb hard drive your C-drive? The 40gb will contain some files like the boot.ini if it's the C-drive, otherwise there's nothing to worry about.[/QUOTE]      the 80 is the C drive.   I just did a double check, and there are copies of things that should be in the c-drive on the d-drive (the recycle bin is one, and some programs files were apparently installed there.  I thought at first it was just some windows default files, should I use partition magic after all since those files are there? there is already a recycle bin on the c-drive, so I can't understand why it is on the d drive.   

Thank you 
WolfeSidhe

---

### Post by ijsje on 2005-04-16
> Yes, that's exactly what I was wanting to do. Should I still use the boot magic program that came with partition magic? Or will another bootloader be installed in the process of installing ubuntu?
Ubuntu will install a boatloader named GRUB, it can handle both linux and windows. It's a simple menu at startup, and you can choose between normal ubuntu, ubuntu recovery mode, and the windows drive.

> the 80 is the C drive. I just did a double check, and there are copies of things that should be in the c-drive on the d-drive (the recycle bin is one, and some programs files were apparently installed there. I thought at first it was just some windows default files, should I use partition magic after all since those files are there? there is already a recycle bin on the c-drive, so I can't understand why it is on the d drive.
In windows every partition has it's own recycle bin (at the recycle bin properties you can set a different quota for each partition). The recycle bin you normally use checks the recycle bins at all partitions at once, so for the user it looks like there is only one recycle bin.
I don't think there's anything important at the D-drive, maybe some scandisk files and a couple of unimportant windows default files. If you can find something you don't want to loose, you can copy it to your C-drive.
You could even temporarely unplug your 40gb drive, and see if windows still boots, that way you can really make sure there's nothing crucial at that drive.

---

### Post by wolfesidhe on 2005-04-17
[QUOTE=ijsje]Ubuntu will install a boatloader named GRUB, it can handle both linux and windows. It's a simple menu at startup, and you can choose between normal ubuntu, ubuntu recovery mode, and the windows drive.


In windows every partition has it's own recycle bin (at the recycle bin properties you can set a different quota for each partition). The recycle bin you normally use checks the recycle bins at all partitions at once, so for the user it looks like there is only one recycle bin.
I don't think there's anything important at the D-drive, maybe some scandisk files and a couple of unimportant windows default files. If you can find something you don't want to loose, you can copy it to your C-drive.
You could even temporarely unplug your 40gb drive, and see if windows still boots, that way you can really make sure there's nothing crucial at that drive.[/QUOTE]
 Making 4 partitions was mentioned, but I wanted to make sure before I went ahead with this, should these 4 partitions be primary or logical partitions? 

Thanks
WolfeSidhe

---

### Post by paretooptimum on 2005-04-17
"primary or logical"

AFAIK, and I have done it both ways on a number of computers, it really doesn't matter. Make some one and some the other.

Make em all primary. I'm sure someone wiser than me will point out a problem, but I've never seen it in the real world. Use primary on smaller disks and logical on larger. 

OK, to be safe, make the first one primary and the other three (under the partitioning system above, which I don't use) logical. 

I generally just use / swap and /home. A seperate /home is a good idea though, so you can reinstall without wiping the stuff you care about. My /home is another drive though. If you love ubuntu and dump windows, you can turn your 80g into /home.

Why don't you just let the ubuntu partitioner have all of the 40gb drive and do what it wants. Don;t worry about partitions or primary/secondary. Just go with it.

---


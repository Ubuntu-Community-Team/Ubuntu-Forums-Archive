---
title: "fresh installation in trouble ! :-("
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2009-12-20
hello all !
i am in trouble and all this is a lil mysteriuos to me.
my pefectyl runnin Ubuntu 9.04had got corrupted earlier while an online upgrade to 9.10. after that i could not boot into the ubuntu OS at all. so i went ahead and reinstalled it after formatting the / partition.
after that i could access the new OS and check out its nice feautures (the new software centre is quite nice) and also updated the OS.
now, when i opened the OS after a proper shutdown i am getting a message which says that "cannot mount the filesystem". it also tries to run "fsck" which it wasn't able to do so. so i did it and it seems to say something about "1.2 % non-contiguous disk space".

let me also mention here that i checked out the various softwares available in the new OS installation. one of these was a drive checker. i was quite alarmed to see that it said that there are some bad sectors on my internal HDD !  :-(

now i know this is not a good thing. but it also seemed to indicate that there is nothing serious and so i wasn't too worried about the bad sectors.

then this problem happened and i can't boot into Ubuntu 9.10 with or without recovery mode.

please help !!

PS- would it be a better idea to backup data on my other OS (XP pro SP2)on DVD's or an external HDD ? could the ubuntu problem / bad sectors cause data loss in XP ??

thanks!

---

### Post by darkod on 2009-12-20
Boot with the 9.10 cd, Try Ubuntu option, and run the fsck on the / partition. It should be like:
sudo fsck /dev/sda1 (depending which is your / parttion replace /dev/sda1)

It should be able to repair any errors. The bad sectors reported might just be a wrong report due to the broken upgrade. See first what fsck can do and can it repair any problems that it finds.
After that if you still suspect you have a problem, you can also run TestDisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Before doing any of this, you can copy the data from your XP on external hdd, just in case. When booted with the 9.10 cd it will allow you to copy data. It's never a bad thing to have a backup but it doesn't mean something will go wrong.

---

### Post by phillw on 2009-12-20
Re: many bad areas reported on hard drive. There have been some issues reported with one of the packages - can't remember its name.

The advice is to get a test disk from your hard-disk manufacturer (They're free to download). That will confirm the status of your hard drive - Operating system independent.

Phill.

---

### Post by AM_SOS on 2009-12-22
hello darkod , phillw and others!

well what happened here to my boot in issues with ubuntu 9.10 is weird. 

before i could do the fsck check with the installation cd, i was able to boot in into the ubuntu partition in the normal manner !!

i had just checked casually and before i realized it, there was some message about checking the disk at the bottom of the boot up screen. soon as it reached 100 percent , i got the normal password and user name page and could log in easily . 

i have since updated the OS again , hoping that this will somehow prevent any further problems with the booting process. 

now the system is working normally but i am really worried about its general reliability !

please suggest if i should do some tests to confirm future problems ..

any help would be greatly appreciated !

---

### Post by phillw on 2009-12-23
> **AM_SOS said:**
> hello darkod , phillw and others!

well what happened here to my boot in issues with ubuntu 9.10 is weird. 

before i could do the fsck check with the installation cd, i was able to boot in into the ubuntu partition in the normal manner !!

i had just checked casually and before i realized it, there was some message about checking the disk at the bottom of the boot up screen. soon as it reached 100 percent , i got the normal password and user name page and could log in easily . 

i have since updated the OS again , hoping that this will somehow prevent any further problems with the booting process. 

now the system is working normally but i am really worried about its general reliability !

please suggest if i should do some tests to confirm future problems ..

any help would be greatly appreciated !

As the system realised it was 'poorly', it automatically ran the fsck for you (It's a good OS & doesn't just lie there with the BSOD - It goes fixes itself !!)

As it has run the fsck and you can log on as normal - it's sorted it.

There is nothing to stop you running fsck from the LiveCD as darkod suggests above. If you trust fsck (and I do) and you have no idea what it is asking to repair (and I never have !!) - You can run it in **y** mode, that will make it think that you are saying to Yes each time it asks if you want it to repair / heal something. So, when booting off the LiveCD, using the above example it would be
```
sudo fdisk -y /dev/sda1
```  Obviously, you may need to change the /dev.... part.
To quickly see which your Ubuntu area is on, whilst you are logged on as normal ```
 sudo fdisk -l
```  (That is a lowercase L, not the number one)

You're looking for the line that ends in 83  Linux
> /dev/sda3            4466        6653    17575110   83  Linux
On my System it is /dev/sda3

**NEVER** run fsck on a mounted system - ALWAYS run it from the LiveCD
(Now, you can unmount certain areas to fsck them, but it is as easy to just use the LiveCD until you're more familiar with partitions etc.)

So, from the LiveCD, drop to a command prompt (Terminal) I would type in
```
sudo fdisk -y /dev/sda3
```  For MY system.

Running fdisk with the -y parameter could be harmful, but unless you know what is poorly on the disk you'd not know which to answer No to. Just so as you're aware. It's never failed me, but that is not to say it will never.

A nice, not too over complicated over-view of fsck is here --> [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

So, don't worry when about once a month your system does an fsck all on its own. This is normal and just another way for the system to keep an eye on your important data !!

Regards,

Phill.

---

### Post by phillw on 2009-12-25
Regarding your query about using a 9.04 LiveCD on 9.10, I'd not reccomend it, simply because the default file system has changed from ext3 to ext4. Whilst I'm by no means certain this could be an issue, between ext4 and the change over to Grub2 - It'd be wise to burn yourself a 9.10 LiveCD.

Regards,

Phill.

---


---
title: "Dual booting XP, Ubuntu and Fedora"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Edwinrg00 on 2007-03-28
This is my first post on this forum, I am a newbie.

I have an 80gig drive split between Windows XP and Fedora Core 6, I also have a slaved second 20 gig drive with Ubuntu. I was successful in dual-booting WP and Fedora; however, when I installed Ubuntu and rebooted I got the option between XP and Ubuntu but no Fedora.
I'm guessing Ubuntu wrote over the GRUB for Fedora. Is there any way to recover from this and be able to choose between the three OS's?

---

### Post by thewahls7 on 2007-03-28
Welcome.


Well, I find it odd that it would pick up an operating system on the slave before the master. I don't know how ubuntu would overwrite something on a completely different hard drive. My knowledge of linux is very limited, and I have none of ubuntu. 

I would just say try to reinstall Fedora.

Hopefully some more knowledgeable folks will come along to help you with this further. :popcorn:

---

### Post by pradeepadapa on 2007-03-28
u hav to edit the menu.lst file of grub so that it detects all the 3 OSes.

---

### Post by bernied on 2007-03-28
There's no need to reinstall Fedora.

If Fedora uses grub, and you know where the Fedora menu.lst file is, then an entry like this in the Ubuntu /boot/grub/menu.lst will do the job:

```
title Fedora
configfile **(hd0,1)/boot/grub/menu.lst**
```
It's the location that is the tricky part - you can try '(hd0,1)/boot/grub/menu.lst' as in the above, but it was only a guess of mine, so it may be wrong.
If you could post the results of 
```
sudo fdisk -l
```which is a list of your disks and partitions, then that would help.

---

### Post by bernied on 2007-03-28
[Herman](http://users.bigpond.net.au/hermanzone/) is very good with all things to do with grub and dual booting. You will find some enlightenment on his site.

---

### Post by dannyboy79 on 2007-03-28
all that is going to do is simply boot Fedora's grub list. he doesn't want that. SInce grub can directly boot any verison of linux, we just need to add an entry for this fedora os. please post the output from /boot/grub/menu.lst and also inform me where fedora's kernel is located and we'll get youu straightened away!

Of course there is an advantage to the way that was previously suggested. this way, when you boot into fedora and the kernel gets updated, grub-update should update the menu.lst located within fedora's /boot/grub/ folder and this will be good! otherwise if you update your ubuntu kernel, it'll update your ubuntu menu.lst (which is the one that gets loading from the mbr) and possibly (depending where you put the fedora boot line) could overwrite the fedora line. I know Herman is way smarter about this and I am sure he would suggest using a config file. good luck


**EVERYTHING BELOW is from Herman's webpage** (all credit goes to him!!!!!! He is the man when it comes to dual-booting.)\
When kernels get updated that are not Ubuntu's kernel, those other linux kernel's entries won't get automagically get updated in the menu.lst, here are some solutions to that problem.

*_1. Configfile Boot Entry_*
This is the one I like best. I recommend you try it too. The 'configfile' command will tell Grub to find the other Linux's menu.lst or grub configfile and use that to boot with. Since that is maintained by the OS it belongs to, it should always be up to date.
Another neat advantage is, all other operating systems listed in the other grub menu can be subsequently booted. You can use as many different grub menus as you like.
Following is an example.
code:
title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst 
Where: Edgy Eft is a Linux operating system on partition number 6.
Where: /boot/grub/menu.lst is the exact file path and filename of the configfile for Grub to load. You may need to check what directory path other distros use for keeping their grub menu.lst in, it could be /GRUB , for example, (no /boot folder, and /GRUB with capital letters). Also, the filename might not always be 'menu/lst, it could be something else, like 'grub.config' or the like. You will need to find out somehow, and alter the details following your configfile command accordingly.

To speed up booting, you can turn down it's timer and hide it's grub menu if you like. Or, the opposite, take advantage of the opportunity to display another nice grub splashimage instead. 




*_2. Chainloader boot entry_*
A popular method is to install the other OS'es Grub or Lilo to the operating system's first sector and then make an entry that will chainload it. Grub's 'chainloader' command is used. This is similar to the way we chainload Windows. That will mean it will use it's own Grub or Lilo menu. Since it's own menu is kept up to date by the operating system it belongs to, it should always be up to date. 
To speed up booting, you can turn down it's timer and hide it's grub menu if you like. Or, the opposite, take advantage of the opportunity to display another nice grub splashimage instead. 
code:
title        Ubuntu Edgy Eft
root        (hd0,5)
savedefault
chainloader    +1 
Where: Edgy Eft is a Linux operating system on partition number 6, and it has Grub installed in the first sector of the partition.



*_3. Symlink boot entry_*
A third method that works very well would be to make an boot entry that will boot the other Linux by it's symlinks, and not refer to it's kernel or ramdisk specifically. Almost all Linux operating systems have symlinks to the kernel and initrd.img files in the root of their filesystems. A few might not. Obviously you will only be able to use this method if there are such symlinks provided, or if you can make them yourself.
The advantage of symlink booting is that it is very reliable. Even if there is a problem with the grub menu in the other operating system and you cannot boot that OS any other way, symlink booting will probably work.
Here's an example of a symlink boot entry,
code:
title        Ubuntu Edgy Eft
root         (hd0,5)
kernel       /vmlinuz root=/dev/hda6 ro quiet splash
initrd       /initrd.img
savedefault
boot 
Where: Edgy Eft is a Linux operating system on partition number 6.

Can you see that I have altered the 'kernel' line to refer simply to to /vmlinuz, which is a symlink, rather than a specific kernel like '/boot/vmlinuz-2.6.15-23-386'?
Also, the initrd line has been simplified to '/initrd.img' rather than a specific file like '/boot/initrd.img-2.6.15-23-386'.
The symlinks always point to the most up to date kernel and initrd.img files, so there is no need to worry about updating your grub menu after a kernel update in your other system when you are using symlink booting.

---

### Post by bernied on 2007-03-28
Both Fedora and Ubuntu like to update their grub menu.lst files. My way allows them to do that without upsetting each other, which so many dual-booters complain of.

It also means that it's not necessary to find out what the Fedora kernel needs to boot, you just need to know the location of one file.

But I'm sure that Edwinrg is able to decide what is best.

---

### Post by Edwinrg00 on 2007-03-28
Guys I appreciate  all the responses!

The following is the output for /boot/grub/menu.lst ;

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Edwinrg00 on 2007-03-28
How exactly and where do I make the entry for:

title Fedora
configfile (hd0,1)/boot/grub/menu.lst

---

### Post by confused57 on 2007-03-28
You might first want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

For the configfile & chainloader methods, grub would need to be installed to Fedora's root partition:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You could always mount your Fedora root partition & get your exact entry to boot your kernel, but I prefer the chainload method, for reasons mentioned previously.

Added:  You Fedora installation live cd may have an option to just reinstall lilo(if that is what Fedora's using)...you could install lilo to Fedora's root partition and use the chainloading method to boot from your Ubuntu grub.  You might want to search on a Fedora forum or website for some info about how to go about this.

---

### Post by Edwinrg00 on 2007-03-28
Here it is....

edwinrg00@UBUNTU:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        5112      104422+  83  Linux
/dev/hda3            5113        9729    37086052+  8e  Linux LVM

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/sda: 4102 MB, 4102029312 bytes
1 heads, 32 sectors/track, 250368 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2      250368     4005872    e  W95 FAT16 (LBA)
edwinrg00@UBUNTU:~$

---

### Post by Edwinrg00 on 2007-03-28
I guess my Fedora partition is  on /dev/hda2 5100 5112 104422+ 83 Linux; the second partition on the 80 gig drive.

---

### Post by confused57 on 2007-03-28
To boot Fedora using chainloading, you'd need to boot up the Ubuntu live cd & install Fedora's grub to it's root partition:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Using the above link, you'd open a terminal, enter:
```
sudo grub
find /boot/grub/stage1
```
this should return:
root (hd0,1)  <-----this should be your Fedora root partition
root (hd1,0)  <-----this is your Ubuntu partition

to install Fedora's grub to it's root partition, you'd enter this:
```
root (hd0,1)
setup (hd0,1)
quit
```

Then you'd add an entry to your Ubuntu menu.lst to boot Fedora:
```
title    Fedora
rootnoverify (hd0,1)
chainloader +1
```

I think you already know how, but to edit  menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add the above entry at the very end of the menu.lst file.

You might want to wait on someone else to confirm the above, but it's the way I would go about booting Fedora from Ubuntu's grub menu, if it were my system.

---

### Post by Edwinrg00 on 2007-03-28
This is what I got...

   [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> find /boot/grub/stage1 
 (hd1,0)

grub>

---

### Post by confused57 on 2007-03-28
> **Edwinrg00 said:**
> This is what I got...

   [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> find /boot/grub/stage1 
 (hd1,0)

grub>
I'm guessing  fedora must use lilo, then the above instructions wouldn't work, since "find /boot/grub/stage1" didn't show any results for your fedora root partition.

You might be able to mount your fedora root partition from Ubuntu and get your entry to boot fedora & add it to your menu.lst?
See this link for mounting fedora from Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

It would be something like this:
```
sudo mkdir /media/fedora
sudo mount -t ext3 /dev/hda2 /media/fedora
cd /media/fedora/boot
```

then maybe you can find the necessary directories for your kernel entries:
```
ls -a
```
you can also mount your fedora partition, using the live cd.

I'm not familiar with lilo, so what I've mentioned is just a "shot in the dark", but might get you started...until someone else who is familiar with lilo or Fedora can reply.
It seems from searching in the Fedora forum that it does use grub, so unless your Fedora is using lilo, I don't know why your Fedora stage1 wasn't found.

Added:  Here's a link on using lilo:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
after mounting your /media/fedora, you could probably just open nautilus & navigate to your /media/fedora directory & explore for your kernel boot entries.

---

### Post by Edwinrg00 on 2007-03-29
I did a re-install of Fedora, when it boots and gets to the GRUB it sees XP and Fedora but no Ubuntu. Fedora is using grub, not lilo.
How would I add the ubuntu to the grub list? I hope this aproach is much simpler.

Thanks.

---

### Post by dannyboy79 on 2007-03-29
follow the same instructions that he already posted. thread #13.

or go here 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
and follow the instructions under **Operating System Entries for Multiple Booting More Linux Systems**
and pick 1 of the methods and just do it. the easiest is going to be chainloading liek is already suggested or the config file option.

---

### Post by confused57 on 2007-03-29
> **Edwinrg00 said:**
> I did a re-install of Fedora, when it boots and gets to the GRUB it sees XP and Fedora but no Ubuntu. Fedora is using grub, not lilo.
How would I add the ubuntu to the grub list? I hope this aproach is much simpler.

Thanks.
As dannyboy79 mentioned, you can probably follow the directions I gave you earlier, but you might want use the Ubuntu live cd to install Ubuntu's grub to it's root partition:
```
root (hd1,0)
setup (hd1,0)
quit
```

then add an entry to Fedora's grub:

title   Dapper or Edgy or Ubuntu  <---Whatever you want to call it
rootnoverify (hd1,0)
chainloader +1

---

### Post by bernied on 2007-03-30
Hello again. This thread is an excellent example of the strengths and weaknesses of community support for an operating system. Lots of intelligent, capable people willing and able to help, but each with their own ideas on the best way to solve the problem. And of course we are on different time zones and have other demands on our time. Any one of us could have fixed this in our own way quite quickly, but all combined we just make a lot of extra work for Edwinrg. I'm sorry, this was never that difficult to fix.

I guess the moral is, you just need to know what you are doing if you are going to try to boot more than one operating system.

Anyway, presuming that you can still boot to Fedora, and you haven't messed too much with your Ubuntu install with that lovely install disk, (in my opinion) here is what will fix your problem.

Edit the **Fedora **menu.lst file, and add the following entry (the safest place to add this is probably right at the end of the file, though that might not be so convenient - I'm sorry but I don't know how Fedora manages grub, so I might not get this bit right):
```
title Ubuntu - hooray!
configfile (hd1,0)/boot/grub/menu.lst
```
That should do it.

As I said, I know nothing of Fedora, but [a quick google](http://www.google.co.uk/search?hl=en&q=editing+files+in+fedora&btnG=Google+Search&meta=) tells me that to edit the file (in case you don't know how to) you need to do something like:
```
su
vi /boot/grub/menu.lst
```
Please tell us if this fixed it for you, maybe then we can help with tweaking it so it's neater and faster.

---

### Post by bernied on 2007-03-30
> **confused57 said:**
> For the configfile & chainloader methods, grub would need to be installed to Fedora's root partition
For the record, this is true for chainloader, but not for configfile. So if you are using configfile to start another linux install and grub is already working (you get a menu), you do not need to alter any boot records by using the grub setup command.

configfile uses the instance of grub already running to load a menu only, whereas chainloader boots a new bootloader (or whatever it is told to), which might be grub, ntldr (the windows bootloader), etc. The [grub manual](http://www.gnu.org/software/grub/manual/grub.html) is quite well written, if a little daunting.

---

### Post by bernied on 2007-03-30
I've just realised that you may already have followed the confused advice above, in which case you should be up and running with chainloader. It if works, don't fix it!

There are many ways to multiboot - this thread has shown three of them.

Here's another aspect of community support, egotistical posters - like me, but we're all guilty sometimes - don't always properly read previous posts before attacking the keyboard with a rant like 'Nooooo, you should do it thiiiiiiiss waaaaaaay!!!!11!!!'

---

### Post by confused57 on 2007-03-30
> **bernied said:**
> I've just realised that you may already have followed the confused advice above, in which case you should be up and running with chainloader. It if works, don't fix it!

There are many ways to multiboot - this thread has shown three of them.

Here's another aspect of community support, egotistical posters - like me, but we're all guilty sometimes - don't always properly read previous posts before attacking the keyboard with a rant like 'Nooooo, you should do it thiiiiiiiss waaaaaaay!!!!11!!!'

Thanks for the info, I don't think I'll ever be too old to learn something new...I've always used chainloading to boot other Linux distros, mostly because someone else recommended it when I was setting up my system & it's worked  pretty well for me.  I hadn't pursued reading the "documentation" and made an assumption about configfile booting...and I do know what the end result of making assumptions can be.

---


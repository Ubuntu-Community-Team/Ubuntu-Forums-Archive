---
title: "Trouble with installing Ubuntu on my netbook"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by AmiableAdder on 2010-10-11
So I've been trying to install any of the following onto my netbook: 10.04 lts, 10.04 netbook, 10.10 rc, and 10.10 (like as soon as it came out), and I can't get any of them to work.

I have to use a usb to install it because I have no cd drive. 

I used the universal usb installer for all of them but none worked. There's no option for 10.10 in the installer (which is understandable considering it just came out), so i selected the "try some other linux iso" option and that didnt work. I also tried the 10.04 option for 10.10 and that didnt work (i didnt think it would). When i start up my comp it wont boot into ubuntu.

10.10 rc did the same thing.

I got 10.04 to boot from the usb but when I try to install it it sort of freezes at a certain point (not during the install, but the page before the partition manager.

10.04 netbook kept coming up with a crash report whenever i tried to run anything.

I also tried using grub4dos and couldnt get it to work.

If anyone knows what's wrong or how to fix it that would be awesome because I've stumped.

---

### Post by Mark Phelps on 2010-10-11
Don't know how your hard drive is formatted, but if the installer doesn't get to the partitioner, there's the possibility the netbook already has the maximum of 4 primary partitions allocated.

To see this, boot from an Ubuntu USB (in LiveCD) mode, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).

That will list out your partitions.  Post the result back here.

If you already have 4 primary partitions, you will have a LOT of work ahead of you to install Ubuntu.

---

### Post by AmiableAdder on 2010-10-11
Thanks for the reply.

Ill try to make this how it looks in the terminal. I currently have no access to internet (other than my droid so thats what im using currently :P), my 10.10 iso wont boot, and i deleted my 10.04 iso once i got the 10.10 one because i have slight ocd for having extra stuff on my computer. didnt know i might still need it at the time i was just excited for 10.10). So im using a terminal in crunchbang live so hopefully its similar, if not hopefully my internet starts working so I can get 10.04 again.


Disk.  /dev/sda: 160.0 GB,  160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xad7ec673


   Device        Boot              Start                     End               Blocks        Id     System
/dev/sda1                                 63         14683409           7341673       12    Compaq diagnostics
/dev/sda2        *        14683410      312576704      148946647        7      Hpfs/ntfs



This second part is my usb drive formatting:

Disk   /dev/sdb: 4007MB, 4007657472 bytes
22 sectors/ track, 4137 cylinders, total 7827456 sectors
units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

 
       Device    Boot               Start                  End           Blocks       Id           System
/dev/sdb1         *                      22           153895         769087        b           W95 FAT32
/dev/sdb2                     1538196         7827203       3144504      83          Linux

---

### Post by AmiableAdder on 2010-10-11
That ended up not coming out too well :/

Basically i think it means i have 2 partitions on my harddrive.

---

### Post by BingHeZhouKe on 2010-10-11
i usually use a software called "ultra iso"to make a usb installer,you may have a try ,and it runs in windows.

---

### Post by AmiableAdder on 2010-10-11
Tried ulra iso.

When I booted i get an error saying "could not find kernel image: linux"

---

### Post by mikewhatever on 2010-10-11
The universal usb installer now supports 10.10. Hope it work for you.

---

### Post by AmiableAdder on 2010-10-11
Just tried it. 

10.10 desktop did nothing when i booted, just a black screen with the white underscore. I waited about 3 minutes just in case it was loading or something but nothing happened.

Netbook edition had an error while I was running the usb installer, so i have a feeling it didnt download properly so I'm going to re-download it and try again.

---

### Post by aksoutherland on 2010-10-11
You might also try using UnetBootin to prep your USB key.

I have used it many times in the past.

---

### Post by AmiableAdder on 2010-10-11
I've tried that but I'm not sure if i did it right.

Is it better to select distribution or diskimage? Because I already have the 10.10 iso so if i didn't need to re download it that would be great.

*Edit*

Couldn't get either way working. Just boots to the black screen with the white underscore.


*Edit*

Got wubi 10.10 to work. I'm just gonna replace windows in wubi.

---


---
title: "Option to boot from windows?"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by wrynn on 2005-10-22
i deleted my old winxp partition (and all the NTLOADR information contained there) to make room for badger... hoping that somehow badger would be able to make a new boot loader and detect my other xp installation and add it to the list.


unfortunately that did not happen and my system just boots straight into linux with no option to go into my xp installation.. any ideas on how i can fix this?

---

### Post by adwait on 2005-10-22
If you deleted the WinXP partition, doesn't it mean that there is no windows installed on your system as of now?

---

### Post by wrynn on 2005-10-22
there were 2 xp installations.. only 1 of them was deleted to make room for badger

---

### Post by tikal26 on 2005-10-22
you cango to any partition software or fdisk and see that your windows partiton is still there also amke sure that a bootable flag is set on the xp partition.

---

### Post by wrynn on 2005-10-23
I want to be able to have the option to boot into /dev/sda1, does that mean i have to mark it booatable along with /dev/hda1? how do i do that?

```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         974     7823623+  83  Linux
/dev/hda2             975       16708   126383355    f  W95 Ext'd (LBA)
/dev/hda3           16709       19929    25872682+   7  HPFS/NTFS
/dev/hda5            1021        8669    61440561    7  HPFS/NTFS
/dev/hda6            8670       12493    30716248+   7  HPFS/NTFS
/dev/hda7           12494       16708    33856956    7  HPFS/NTFS
/dev/hda8             975        1020      369432   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246    7  HPFS/NTFS
/dev/sda2            1148        4499    26924940    f  W95 Ext'd (LBA)
/dev/sda5            1148        4499    26924908+   7  HPFS/NTFS
```

---

### Post by paddyg on 2005-10-23
if you installed win xp on sda1 when there was already another win xp on hda1, the new windows added a boot line to the boot.ini on hda1 (and, i suppose, as a signature into the bargain), because the win loader was on hda1. I don't think there's any boot.ini on sda1.

If you decide to back up and install windows again to sort things out, please remember you'll have to install linux once again after windows, because grub will be overwritten.

Also, i was hard put to make grub on IDE to detect a win loader on SATA (i've got 1 40GB IDE and 1 120GB SATA)--- i failed.

BTW what's on the other hda and sda partitions?

PS: sorry i wasn't of any help

---

### Post by wrynn on 2005-10-23
[QUOTE=paddyg]

BTW what's on the other hda and sda partitions?
[/QUOTE]

i duno why sda2 even exists .... wtf is W95 Ext'd (LBA)? 

but sda5 is just program files...

in disk manager it says the sda is "inaccessible" and clicking "enable" does absolutely nothing

---

### Post by penguinchrissy on 2005-10-23
I think that it has something do to with the NTFS file system because I get the samething on my ntfs harddrives

---

### Post by santorini on 2005-10-23
perhaps you can try this:

at the grub bootup screen

i) press "c" for command line
ii) type the following commands
rootnoverify (sd0,0) 
# btw, you may want to try pressing TAB after you've typed "rootnoverify (" to get a list of
# options, "sd" might be here, then TAB again, perhaps "0" is here to make "sd0", then 
# TAB again to get ,0 to make (sd0,0).
chainloader +1
boot

if the results are positive, these lines can be added to grub.conf for a new boot option.

---

### Post by wrynn on 2005-10-23
i tried just typing rootnoverify (sd0,0) and i got error23: "error while parsing the number"

---

### Post by paddyg on 2005-10-23
[QUOTE=wrynn]i duno why sda2 even exists .... wtf is W95 Ext'd (LBA)? 

but sda5 is just program files...

in disk manager it says the sda is "inaccessible" and clicking "enable" does absolutely nothing[/QUOTE]

Do you have a laptop?

One more thing: Windows xp should come first.
For example:

hda1: Windows xp (primary)
hda2: extended
hda5: linux (ext3)
hda6 swap

---

### Post by wrynn on 2005-10-23
i typed 
>rootnoverify (


and then pressed TAB and it said:

***possible disks: fd0, fd1...., hd0, hd1***

for some reason sd0 isnt a possible disk.  what does this mean?

---

### Post by paddyg on 2005-10-23
[QUOTE=wrynn]i typed 
>rootnoverify (


and then pressed TAB and it said:

***possible disks: fd0, fd1...., hd0, hd1***

for some reason sd0 isnt a possible disk.  what does this mean?[/QUOTE]

you are lucky as far as GRUB is concerned.

GRUB (and i disagree with post #9, Santorini's, here) doesn't make any difference between sata or ide, just fd and hd
(for example, just take a look at [http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax))

So, hd0 is linux hda, while hd1 your sda.

---

### Post by wrynn on 2005-10-23
my device.map says:

(hd0)   /dev/hda
(hd1)   /dev/sda

---

### Post by wrynn on 2005-10-23
lol ya paddy i just figured that out from google

---

### Post by bluck on 2005-10-23
[QUOTE=wrynn]i duno why sda2 even exists .... wtf is W95 Ext'd (LBA)? 

but sda5 is just program files...

in disk manager it says the sda is "inaccessible" and clicking "enable" does absolutely nothing[/QUOTE]


means its an extended partition (opposed to primary).   LBA is Logical Block Addressing.

none of this really helps your problem, but there. :)

---

### Post by paddyg on 2005-10-23
wrynn, i really wish good luck with grub, but i think things to work really fine with win xp and linux should be planned as in my post # 11.

Hope you'll get over it in the end somehow.

---

### Post by wrynn on 2005-10-23
i typed
rootnoverify(hd1, 0)
chainloader +1
boot

and the system hung

---

### Post by SilentCacophony on 2005-10-23
[QUOTE=wrynn]i typed
rootnoverify(hd1, 0)
chainloader +1
boot

and the system hung[/QUOTE]

Hi. You may want to check out this link: [http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html)

I think the makeactive option should be set as well. I would try an entry like so, in /boot/grub/menu.lst:

```
title Windows 
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

```
I don't think the boot command is necessary for chainloaded partitions.

---

### Post by wrynn on 2005-10-23
i tried it and it says "NTLDR is missing"

before i wiped the 2nd xp instalation, i copied the ntldr file etc and put it into the sda partition containing the other instalation of xp

so it SHOULD be there... maybe we are pointing at the wrong parittion

---

### Post by wrynn on 2005-10-23
well i guess i am better off just finding my windows xp cd and booting with it and telling it to perform a fdisk /fixmbr?

of course that could totally screw up my system but it has worked before..

and then next time i should do a clean install of windows on my SATA drive, and then install ubuntu onto a partition on that same SATA drive? but on the next partition down? is that the best way?

---

### Post by wrynn on 2005-10-23
i had a brilliant idea and just unplugged my IDE drive (the one that contains GRUB and Ubuntu), and let my system boot from the SATA drive only

and it displayed the same "NTLDR missing" error...

so i guess your command worked perfectly, its just that the SATA partition has nothing to work with...

so i guess i should just run fdisk /mbr with the IDE drive unplugged and then see what happens

---

### Post by SilentCacophony on 2005-10-23
I don't know much about NTLDR, but one of my bookmarked computer help sites has some info on it:

[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

> and then next time i should do a clean install of windows on my SATA drive, and then install ubuntu onto a partition on that same SATA drive? but on the next partition down? is that the best way?


That's basically what I do. I have two other primary partitions with ubuntu on each, myself:

```
Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32 **<- Windows 98 SE**
/dev/hda2             313         722     3293325   83  Linux **<- Ubuntu #2**
/dev/hda3             723        1338     4948020   83  Linux **<- Ubuntu #1**
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux **<- Storage**
/dev/hda6            1852        2364     4120641   83  Linux **<- Storage**
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA) **<- Shared Storage**
```

---

### Post by santorini on 2005-10-24
did you try tabbing to get a list of available options? if there were "sd" then probably grub can load it for you

EDIT: oh i missed a lot of posts, i didn't read paddy's comment before posting this. yeh, paddy's recommendation should work fine.

---

### Post by paddyg on 2005-10-24
[QUOTE=wrynn]i had a brilliant idea and just unplugged my IDE drive (the one that contains GRUB and Ubuntu), and let my system boot from the SATA drive only

and it displayed the same "NTLDR missing" error...

so i guess your command worked perfectly, its just that the SATA partition has nothing to work with...

so i guess i should just run fdisk /mbr with the IDE drive unplugged and then see what happens[/QUOTE]

Yes, and then remember to modify the bootloader config file on hda when you plug the ide drive back in. The system should boot from the ide (between ide and sata, usually ide is the one preferred)

PS: Santorini, grub doesn't recognise any sd, just fd and hd (all hard drives are hd, whether sata or not). Grub naming is different than linux

---

### Post by wrynn on 2005-10-24
i slipstreamed my SATA drivers into a custom XP install ISO using nlite ([http://www.nliteos.com/](http://www.nliteos.com/)) and proceeded to boot it.  I entered the recovery console & copied missing XP boot files from my freshly burned custom disc (using [SilentCacophony]("http://www.ubuntuforums.org/member.php?u=40187")'s [ great link]("http://www.computerhope.com/issues/ch000465.htm")) as a guide :)  

Now I can boot Windows fine with my Ubuntu drive unplugged.  


I'm going to see what happens when both drives are plugged in simultaneously...

---

### Post by wrynn on 2005-10-24
when both drives are in, grub is booting to windows automatically (as it should) but before loading windows it says "boot.ini is missing, booting from c:\windows"

and then it loads windows just fine

---

### Post by santorini on 2005-10-25
is it all fixed? =) 

so you did have a menu with windows xp and grub chose it as default?

btw, my post #28 was quite a mistake, since i didn't see the posts before mine. weird. (perhaps I "saw" there were only 2 pages instead of 3? weirdweird)

---

### Post by wrynn on 2005-10-26
well its booting straight into windows unless i press escape and choose ubuntu.. i'd prefer ot have the menu come up everytime by default

---

### Post by SilentCacophony on 2005-10-26
> well its booting straight into windows unless i press escape and choose ubuntu.. i'd prefer ot have the menu come up everytime by default

Good to hear it's straightened out. As for having to hit escape to get the menu, that's not the default behavior that I get. If you look in your */boot/grub/menu.lst* file, there should be a line that says *hiddenmenu* that causes that behavior. If you comment it out with a #, then it should always present the list. Like so:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

---


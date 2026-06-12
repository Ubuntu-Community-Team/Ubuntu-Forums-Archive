---
title: "help!!! computer gone wild!!!!"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by ShakEEn on 2006-08-20
i had xp pro then i installed ubuntu... everything was workin fine untill this morning... it showed me error 17 and i had no clue what that was for.. so i ran my XP recovery disc and installed xp pro (i dont knw y) but nothin changed.. i was still gettin the same error.. then i decided to reinstall ubuntu to fix the error and that kinda fixed it coz it didn't give me error 17..  and when i restarted my comp., it showed me the followin: ubuntu (works fine), and for other OS, it showed, xp pro (factory default), and xp pro (none of the data was erased)... and after that it showed UBUNTU (this one doesn't work anymore, shows list and stuff)!!!... i have no clue what to do..  so can you guys help me uninstall everything except for my original xp pro... yepp...
down is the image that shows up on windows disk management.. crazy!!!>


[[IMG]http://img99.imageshack.us/img99/8278/crazycopydf9.jpg[/IMG]](http://imageshack.us)

---

### Post by ShakEEn on 2006-08-20
can anyone help me?? please.. or should i just spend 100 or more dollars and get it fixed... i dont have time or money for that coz i m leavin off for college this thursday:(

---

### Post by LKRaider on 2006-08-20
Apparently you did a few partitions too many there :P

I don't know how is your particular setup, but I would first backup all my data to DVD-RW's (or CD's, if that is what you have), then boot from the Ubuntu CD and have it install over the whole harddrive (thus erasing everything on it).

If you want just XP, I am sure it can do that too... I think (I haven't installed it in a long time)

If you want to keep the exact system you have there, it is possible too... but it is very difficult to instruct you over the web with so little information about the system - and more stuff can go wrong too. (especially since you seem to have made a mess of it :P )

---

### Post by ShakEEn on 2006-08-20
ya it's a big mess...

i ran my xp recovery disc but nothin happened.. it just added another xp os , makin it even worse... i will prolly try to do what u suggested...  

will i have any problems with the partitions if i install ubuntu over my harddrive???.. when i got the computer, which was last week, it had two partition already... will things change???

thanks for the suggestion..


i shouldn't have installed linux... see what boredom and breakup does to u....

---

### Post by LKRaider on 2006-08-20
If you install Ubuntu selecting to _take over_ the disk, **EVERYTHING** will be **ERASED**. So if you want to keep things, you should backup them.

From looking at your screenshot, and trying to understand what you said there, this is what I think is going on:

You have installed:
1) WinXP(1) - Working one
2) WinXP(2) - Newly installed one
3) Ubuntu(1) - Not working one
4) Ubuntu(2) - Working one

So you have two of each installed. Unfortunatelly, with just that screenshot I can't really help figuring which partition is which system.

If you can inform me EXACTLY which partition belongs to which system, I could try helping you remove the ones you don't want.

So, respond/correct the following please:

[HTML][FAT32 - I: -  3.9Gb]	belongs to	[ WinXP(2) ? ]
[FAT32 - C: - 53.7Gb]	belongs to	[ WinXP(1) ? ]
[FAT32 - D: - 9.32Gb]	belongs to	[ WinXP(1) ? ]
[   Linux - 11.0Gb  ]	belongs to	[ Ubuntu(1)? ]
[   Linux -  0.5Gb  ]	belongs to	[ Ubuntu(1)? ]
[   Linux - 22.0Gb  ]	belongs to	[ Ubuntu(2)? ]
[   Linux -  0.9Gb  ]	belongs to	[ Ubuntu(2)? ]
[ NTFS - G: - 2.9Gb ]	belongs to	     [ ? ]
[ NTFS - H: - 2.9Gb ]	belongs to	     [ ? ]
[ NTFS - F: - 4.4Gb ]	belongs to	     [ ? ][/HTML]

If you can answer that, and tell me which partitions you want to keep, maybe I can help more.

---

### Post by ShakEEn on 2006-08-20
[FAT32 - I: -  3.9Gb] belongs to [ WinXP(2)? ]TRUE
[FAT32 - C: - 53.7Gb] belongs to [ WinXP(1)? ]TRUE
[FAT32 - D: - 9.32Gb] belongs to [ WinXP(1)? ]NONE
[Linux - 11.0Gb] belongs to [ Ubuntu(1)? ] Maybe 2
[Linux -  0.5Gb] belongs to [ Ubuntu(1)? ] 2 swap files??
[Linux - 22.0Gb] belongs to [ Ubuntu(2)? ]THIS SHOULD BE 1... i think
[Linux -  0.9Gb] belongs to [ Ubuntu(2)? ]1 swap files??
[NTFS - G: - 2.9Gb] belongs to [ ? ]NONE
[NTFS - H: - 2.9Gb] belongs to [ ? ]NONE
[NTFS - F: - 4.4Gb] belongs to [ ? ]I HAVE MSOCACHE FILES THER, WHICH I CAN DELETE...

when i first installed linux, it took a big chunk off my harddrive so i think linux - 22.0GB is indeed Ubuntu 1...

i appreciate ur efforts..:rolleyes:

---

### Post by LKRaider on 2006-08-20
Okay, one more question: do you have PartitionMagic there?
If not, you'll have to edit the partitions from linux with Q/Gparted. Are you familiar with that? (The Ubuntu Live CD includes Qparted)


First step before editing: Copy all data from the NTFS partitions and FAT32 partitions into your C: (53Gb) partition. Have your Ubuntu Live CD at hand too.

Step 2) Now backup your important data! Really, better safe than sorry :P

3) Open PartitionMagic or Q/Gparted and do this:

3 - a) Remove the 3 NTFS partitions
3 - b) Remove the 2 FAT32 partitions (I: and D: )
3 - c) Remove the 22Gb and the 518Mb one linux partitions (non working Ubuntu and the small swap partition)
3 - d) Apply the changes and reboot. Check if you can get into your WinXP and Ubuntu systems. If not, you probably have to reconfigure Grub.

4) You probably can still boot Ubuntu at this point (can you?) but not WinXP : is that the case? If so, boot to Ubuntu and open a terminal and type this:
```
gksudo gedit /boot/grub/menu.lst
```
In the file, look for the option to boot Windows, something like this:
```
title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1
```
The important part is _root (hd0,0)_. Edit so it is that way.
Try and reboot into WinXP.

5) Did all this work out ok? If so, you can now run PartitionMagic or Q/Gparted to expand the size of the partitions so to use the whole HD.
5 - a) Make C: occupy all the space that was for I and D before.
5 - b) Move the Swap partition to the end of the disk and resize the Linux one to occupy the rest of the space.
You could resize diferently if you want.


PLEASE, do these steps CAREFULLY, and if you have problems, DO NOT PROCEED further and report back here if you require more help.

If all goes awry, remember you got backups of your data. (you did backup it, right? ;) )

---

### Post by ShakEEn on 2006-08-20
thank u sir... but i got it fixed this morning... this guy from [www.qunu.com](www.qunu.com) told me to delete everything :D except for my workin system... 
but ya... thank u for ur time.. i really appreciate that:mrgreen: ...
cheers!!!.. haha... thank u again...

---

### Post by LKRaider on 2006-08-20
Cool, glad it's working there :)


EDIT: hah, I see your feedback is on the frontpage of the service now :P

---


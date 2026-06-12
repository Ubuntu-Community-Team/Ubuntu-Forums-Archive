---
title: "Xp doesn't work because of bad sectors --&gt;  install ubuntu"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by adhamj90 on 2011-03-31
hello, 
it is my first post here and i looked in the forum and the Internet for similar problems but couldn't find any, and i hope I'm posting in the right category.
my problem is that I used to have windows xp. but recently i started having a message at startup telling me that my disk might be failing and i should run the test (which would crash and reboot th laptop). then after a while windows wont even start.
so I tried to use ubuntu netbook live from a usb and it is working fine ! i can even access ALL my data on the hard disk, although it is telling me that the hard disk is failing and that it has 1024 bad sectors. 
I have only one hard disk and one partition (120 GB). 
my question is, can i just install ubuntu and somehow block the bad sectors ? ( I DON'T WANT WINDOWS ANY MORE :cool:)  and is there any way i could keep my old data on the hard disk without backing it up (it is not really important btw). :confused:

thanks a lot in advance.
Adham

---

### Post by coffeecat on 2011-03-31
Hi and welcome to the forum. 

Since both Windows and Ubuntu is telling you that your hard drive is failing, I would be inclined to go with the majority vote and assume your hard drive is failing - sorry. It would be unwise to install anything to it. All you would achieve is hours of frustration and an unreliable system, probably quickly followed by an unbootable system.

The reason that Ubuntu works fine from the USB is that it is working from the USB. It is not using the failing hard drive. You can see your files, and perhaps copy them, but not for long I fear.

My advice: backup any data on the drive that you need to another USB drive using the live Ubuntu session. Then have the drive replaced. It may not be difficult to do that yourself. What make and model of machine is it? Laptop, netbook, or desktop?

About blocking bad sectors: the hard drive firmware is doing that for you already. If you are getting a fail imminent message then sectors are going bad quicker than the firmware can deal with it.

---

### Post by Karlchen on 2011-03-31
Hello, Adham.

If a harddisk is dying, it is dying, no matter which operating system has been installed on the dying harddisk.
If the harddisk is no longer good enough for Windows XP, it is not good enough for Ubuntu, either. This is true for purely technical reasons.

So my piece of advice will be:

[LIST]
[*]backup all the data on the dying disk which are worth being backed up
[*]replace the dying disk by a new disk
[*]re-install Windows XP SP3 or Ubuntu on the new disk, just as you please
[*]live happily ever after ...
[*]... till one fine day in a far away future  the new disk will start dying,  too ...
[/LIST]


Kind regards,
Karl

---

### Post by mastablasta on 2011-03-31
> **coffeecat said:**
>  
The reason that Ubuntu works fine from the USB is that it is working from the USB. 

 
It even only loads from USB and it loads the whole system in RAM. So any changes are lost on reboot (because RAM is then emptied).
 
Also listen to the very good advices given to you (above me). Or you could face data loss.

---

### Post by Grenage on 2011-03-31
Save your future sanity; backup any data you want and discard the drive.

---

### Post by adhamj90 on 2011-03-31
thanks all for the really fast replys !
the thing is this is my old laptop.. and i dont really need the data in it and don't want to get a new hard disk for it..
i just thought if i could install ubuntu on it, it wont be using the RAM and lose all the changes everytime i use it ( i only use it to connect it to my TV). 
but i think it wont work because it gives me the "DISK FAILURE IS IMMINENT" warning message.
i guess ill just use it until it wont be working anymore. :-/

---

### Post by adhamj90 on 2011-03-31
> **coffeecat said:**
> 
My advice: backup any data on the drive that you need to another USB drive using the live Ubuntu session. Then have the drive replaced. It may not be difficult to do that yourself. What make and model of machine is it? Laptop, netbook, or desktop?


I have a compaq presario c700 laptop, how difficult would it to be to do it myself ? and will it cost a lot ? 
thanks

---

### Post by mörgæs on 2011-03-31
I take it that the machine is mostly for experimenting now - which is a great way of learning Ubuntu.

You could 

- wipe the disk completely using Killdisk
- run Gparted from the live CD and define a major partition (80 GB) and two-three smaller ones. 
- forget about the big partition and install Ubuntu using the small ones

If you are lucky, then only a part of the hard drive is failing, and another part is working well. If the small partitions are fine, you will have a working system (but don't use it for important data, though!)

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by coffeecat on 2011-03-31
> **adhamj90 said:**
> I have a compaq presario c700 laptop, how difficult would it to be to do it myself ? and will it cost a lot ? 
thanks

Depends. I did a quick google for your model and didn't come up with anything directly relevant. Have a look on the back. Is there a panel you can remove with four (or thereabouts) screws? If you remove it, can you see a 2.5" hard drive? If so, it's easy. If not, then it might mean a major disassembly of the laptop which could be difficult. Also, you need to be sure whether this laptop takes one of the older IDE/PATA drives or a newer SATA drive. Guessing the age of the thing, it could be either. You need to be sure; the two interfaces are not compatible.

---


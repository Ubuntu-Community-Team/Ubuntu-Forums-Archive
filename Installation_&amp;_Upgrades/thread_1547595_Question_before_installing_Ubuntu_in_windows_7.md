---
title: "Question before installing Ubuntu in windows 7"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by tjustleft on 2010-08-06
Just got a nice gift from my granddad. An Asus Essentio CM1630 with AMD Athlon ii X2 220 windows 7 home premium. I haven't messed with windows in over a year. The last was xp home. With xp and win98 I had local disk C and system save D. At first I thought something was wrong with this new system. The 640gb drive was partition with win7 C 238gb and data D 339gb. I'm like why is the recovery partittion getting over half my drive? Bestbuy Ask an agent person wondered the same thing. Geek squad didn't know but says it's how people like it. On my own I think I've figured that D is no longer a recovery partition but just what it says, Data, for our personal files or whatever. Please enlighten me if that is wrong :)

Now to the actual question. In your opinions would it be better to shrink win7 C and install Ubuntu there or shrink D and install it there? Just because I'm used to it and like it it will be Hardy 32 bit. I know it may only use 3 of the 4gb of ram but my old machine only has 384mb :). 

Also if I install hardy on C can I tell it to put Home and all my personal files on D since it has most of the room?

Thanks everyone. I hope I didn't rattle that out too badly :)

---

### Post by TNT1 on 2010-08-07
Why not just a fresh install and set up Hardy as you want it?

---

### Post by wiredman on 2010-08-07
My question would be:
Which is going to be your primary OS, Linux or Win 7.

If Linux , I would recommend repartitioning your C Drive. Shrinking Win 7 and then Installing Ubuntu.

If Win 7, then you can just shrink D and install your ubuntu at the end.

---

### Post by tjustleft on 2010-08-07
Ubuntu will probably be my primary os. I will most likely use C and use D for personal files. Just can't get used to the the partition difference in win7 vs xp and win98. I am so far behind :)

Awesome! I just loaded the hardy cd and tried it out. Not sure if gimp 2.6 is shaky in windows 7 but it is not so fast for me on this new computer. However gimp on the hardy live cd was amazing! Running it from the live cd I expected it to be slower than gimp 2.6 installed in windows. Nope. That just blows my mind that it could be faster running it that way! Can't wait to see how it runs when I install hardy :) What would be a good size for the swap partition? Sorry but after a year I still feel like a noob. Since I haven't installed ubuntu in so long I'll have to read up and remember how I did it :)

---

### Post by daweina on 2010-08-07
hi  
try to defragment your system and check for an error
if its does well , right  or try to use wbui :popcorn:

---

### Post by Mze on 2010-08-07
Shrink the D drive and use the available space for Ubuntu.

here's an [article]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") to guide you along

---

### Post by Mark Phelps on 2010-08-07
If you're planning on continuing to use Win7 but switch over to using Ubuntu most of the time, having done that already, I recommend the following:

1) before you do ANYTHING else, boot into Win7, launch the Backup feature, create and burn a Win7 Repair CD.  This will prove invaluable later should something get hosed up during the dual-booting work.

2) Using Win 7 Disk Management, shrink the "C" drive down to 40GB or so -- if it will let you.  If not, shrink it as far as it will let you.  And, yes, Win7 WILL let you shrink its own OS partition.

3) After shrinkage, reboot back into Win7 a couple of time to let it make any needed filesystem adjustments.

4) Using the Win7 Disk Management utility again, move the ""D drive to the left (adjacent to the now-shrunk "C" drive) and shrink it down (if you want) -- to leave room to the right for Ubuntu.

When all of this is done, boot using the Ubuntu CD and select the "use largest free space" option to have Ubuntu format and partition the free space to install itself.

Once Ubuntu is installed, boot into it, open a terminal, and run "sudo update-grub".  This will regenerate the GRUB menu and should add an entry for Win7.

---

### Post by tjustleft on 2010-08-08
Thanks everyone :)

This is all new to me so please excuse me for being slow in wrapping my mind around it. 

Mark it looks like it will only let me shrink C by about half. That sill leaves quite a bit of room so not so bad. You say to have Ubuntu use the largest free space. Even if D is shrunk in half it either half will have the largest free space. If I remember correctly I can tell ubuntu exactly where to install. When c is shrunk will I be assigning a label to the new free space? Also you say move d to the left of c. Checking things out before doing all this and I see no option for move. 

I guess a handicap of my previous ubuntu running so well is that there weren't a lot of problems to cause me to learn this new stuff :)

---

### Post by tjustleft on 2010-08-09
Sorry people this is still confusing me. I still can't find Move in disk management. Will I notice a difference if I install Ubuntu without moving the partition after shrinking? 

I could just load the disk and install but want to get it as close to perfect the first try. I can't afford a compute and want to be extra careful with this gifted one :)

Thanks again :)

---


---
title: "Help deleting Ubuntu from running alongside windows 7"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by skywalkerjedi95 on 2009-11-28
Please help me!  I was trying to install Ubuntu 9.04 and I hit the install icon inside the demo you can boot into.  I told it to install alongside Windows 7 thinking it would install as a program in windows like when i run the installer in windows.  Little did i know that it doesnt seem to work that way.  So the first thing that alerted me was when i tried to run updates and it said there wasnt enough room.  Now i have a 500Gb HD so i knew something was wrong.  When i booted into windows it doesnt show up as a program.  How do i get my ubuntu install off?!  At least so i can install it the correct way, from inside windows.

---

### Post by earthpigg on 2009-11-28
hi,

where you went wrong was after the 'install side by side with windows' part, you saw a visual image of how your hard drive would be partitioned... it starts with ubuntu taking up the bare minimum of space so as not to be rude to windows. the user is then generally supposed to move the slider so ubuntu has more than the absolute bare minimum. generally, at least 15gb.

at this point, to accomplish what you wish, you will need to do two things:

1) delete the ubuntu partition and the ubuntu swap partition. boot from the live cd again and select system -> admin -> partition editor

2) restore the windows bootloader. this is what a windows forum has to say about that (i have never done it, so cannot vouch for it): [http://www.neowin.net/forum/lofiversion/index.php/t720866.html](http://www.neowin.net/forum/lofiversion/index.php/t720866.html)



once this is done, to install ubuntu via wubi, put the cd in ***while windows is running*** and let the windows ubuntu installer do its thing. then, you will be able to use windows add/remove programs to remove it like you wanted.

you may want to google around and verify that wubi works with windows 7 -- win7 did not exist when ubuntu 9.04 came out, so i have no idea if it will play friendly with it.

---

### Post by darkod on 2009-11-28
> **skywalkerjedi95 said:**
> At least so i can install it the correct way, from inside windows.

I understand you installed by mistake thinking something else would happen, but having them side-by-side, or both of them on its own partitions and filesystems is actually the correct way.

Installing inside windows (wubi way) is more of a "virtual" ubuntu so you can work with it and look around how you like it. I don't consider it long term solution. Actually, there are many threads last few days that after doing some updates the wubi installation stops working.

Ubuntu is NOT designed to work inside windows, and I don't think any linux is. Think what you want to achieve because actually having a dual boot is the "correct way".

---

### Post by iamwhatiseem on 2009-11-28
Installing it side by side is the correct way.

Having said that - this is one of the pitfalls of the general population installing an OS.
As with the OP, they may not really understand that Ubuntu, and all other flavors, is not a program.
It is unfortunate that junior high and high school do not teach kids even something as simple as what an OS is.
Instead they spend the time teaching Powerpoint and Word #-o

---

### Post by skywalkerjedi95 on 2009-11-28
Thanks everyone!  Will I be able to delete it?  See what happened is you guys dont understand.  I want Ubuntu I use it for a main operating system on other computers but I want to have the option to uninstall it from add remove programs in windows 7 ok?  I tried to install 9.10 using wubi but it gave me a 64 bit install which was good but i couldnt download any programs from the software center and my wireless didnt work and so i went to 9.04.

---

### Post by darkod on 2009-11-28
If the uninstall option is all you need from wubi, the real install is even better. You just delete the ubuntu partition(s) and restore windows MBR. Job done.
Not to mention ubuntu would run much slower in wubi I guess, it's not full install after all.
As I said, if you are after long-term usable Ubuntu, you are getting yourself in trouble with wubi. It's enough to accept updates in Ubuntu-wubi and very often some of them will break it. Then what?
Don't forget, for the ubuntu developers is not easy to make it work perfect inside windows. Do you think they are getting cooperation from MS? You can't really blame them if wubi brakes more often than not. If you are after dependable Ubuntu, the dual boot is your best friend. :) IMHO

---

### Post by darkod on 2009-11-28
> **iamwhatiseem said:**
> Installing it side by side is the correct way.

Having said that - this is one of the pitfalls of the general population installing an OS.
As with the OP, they may not really understand that Ubuntu, and all other flavors, is not a program.
It is unfortunate that junior high and high school do not teach kids even something as simple as what an OS is.
Instead they spend the time teaching Powerpoint and Word #-o

And the Ubuntu team has done more damage than popularity with wubi I think. Probably trying to make it easy for long term windows users, all they achieved seems to be Ubuntu to look less reliable. And with wubi more people will think that it's just a "program" for inside windows.
Of course you need to learn something about Ubuntu (Linux) before installing it. Don't you for windows?

---


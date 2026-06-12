---
title: "NTFS non destructive partitioning"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by Cerberus42 on 2005-11-24
alright, ill give you a glimpse int the circumstances

I am using a family computer with a 160 GB hard drive formatted to NTFS running windows XP media cneter edition

I want to resize the NTFS system without destruction by 20 GB (it currently occupies the whole drive) and put ubuntu on the free space.  This is a family computer and i absolutely cannot screw this up.  I need a free way to resize the file system and install linux on it (i just want my own little corner to work in, no need for file sharing or anything.)

as well i would like to use the standard windows boot menu, just so that i dont get any angry comments from the other users about grub.

Any and all help is appreciated

---

### Post by yesplease on 2005-11-24
You can resize with the ubuntu install CD.  Defragment first and check how much free space you have.

You can put grub on another medium like floppy or usb stick.

Trying ubuntu wont break your system, it is also easy to remove. It is good practice though to back up your flies, you never know what may happen.

This is good for starters: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

---

### Post by Cerberus42 on 2005-11-24
i heard that the ubuntu install can be destructive

as well is there any way to allow the windows boot menu to accomadate ubuntu?, i would rather not have to use a floppy to boot it, it would be great security but it isn't what i am looking for

---

### Post by yesplease on 2005-11-24
I edited my first post a bit.

It is not destructive. In a normal install the windows mbr is overwritten by grub.

You can reverse this with the windows CD in rescue mode, for instance if you want to get rid of ubuntu.

I do not know of a window prog that could boot ubuntu. However, Grub is not a big deal, it shows a menu with ubuntu and windows. Anyone can use it.

Nobody can acces your ubuntu however, they need the password first.

---

### Post by Cerberus42 on 2005-11-24
but iwant to keep ubuntu, just have a dual boot system, using the windows boot menu because it is the primary OS and it would be more friendly to other users of the computer.  IN iwndows i know you can change boot.ini to allow booting multiple operating systems, is there a way to get windows to recognize ubuntu and allow it to be booted from its own boot menu?

---

### Post by yesplease on 2005-11-24
I often edit my posts, this can be confusing, sorry about that. 

I dont think windows could handle that. Grub is userfriendly, it will show a few lines with ubuntu, windows, and whatever OS you have. The user chooses between them with the arrows.

---

### Post by az on 2005-11-24
[QUOTE=Cerberus42]but iwant to keep ubuntu, just have a dual boot system, using the windows boot menu because it is the primary OS and it would be more friendly to other users of the computer.  IN iwndows i know you can change boot.ini to allow booting multiple operating systems, is there a way to get windows to recognize ubuntu and allow it to be booted from its own boot menu?[/QUOTE]
Really, the safest and easiest way is to use grub.  You can make the grub menu hidden and boot windows one or two seconds later.  If you want to boot windows, just hit escape during those two seconds to reveal the grub menu and pick ubuntu.

That way, if you make windows the default OS in grub, it will boot windows without the other users seeing a difference.

---

### Post by Cerberus42 on 2005-11-24
that sounds like a good plan, i will try it out once i get the cd's (i ordered them because downloading operating systems takes a long time on my connection, i did it for win98 and it takes nearly a day lol

---

### Post by yesplease on 2005-11-24
I would like to add that you can stop the install (up to a point) when you dont understand how to resize for instance. 

However, is is prudent to read a bit, so you will know what you are doing. For instance the starterguide (it tells you how to restore windows mbr if you want to, and things like that).

---

### Post by gravediggers on 2005-11-24
Maybe try gparted - it is a little friendlier and imho more intelligent. Not sure if its included on the ubunti live CD ,but shouldn't be too hard to track down (I think I saw it on my Knoppix live CD).

---

### Post by Cerberus42 on 2005-11-24
i read a guide about it already, but in 4-6 weeks (sounds so generic lol) i will print out an ntfs resizing guide, after defragging and install it

is it possible to disable a password though?, if someone accidentally loaded it they might be a little distubed if they found a hidden part of the computer that was password protected, they would think it was my porn vault or something like that (well my stepdad would anyway)

and what it is gparted?

---

### Post by yesplease on 2005-11-24
Gparted is on the live CD and makes live even easier, you can resize with it and make new partitions.

You actually downloaded windows 98 :)

When the CDs arrive and you still have questions, come back here, good luck.

I dont know if you can disable the password, it is bad security anyway. You are able to make a read-only user that can see most things, but not overwrite or execute them.

Edit: ok, it seems we are crossposting, and I will leave this to Azz :)

---

### Post by az on 2005-11-24
[QUOTE=Cerberus42]i read a guide about it already, but in 4-6 weeks (sounds so generic lol) i will print out an ntfs resizing guide, after defragging and install it

is it possible to disable a password though?, if someone accidentally loaded it they might be a little distubed if they found a hidden part of the computer that was password protected, they would think it was my porn vault or something like that (well my stepdad would anyway)

and what it is gparted?[/QUOTE]


There are a ton of guides.  Anyway, the installer does it all for you.  You just have to pick the default option it offers you (resize partition to create new space) and tell it the size you want.

Yes, you can dissable the login.  Actually, you can tell GDM to automatically log in a user (you) upon boot.  You will never see the login screen unless you log out.  Also, you can tell it wo automatically log you in after a certain delay.

---

### Post by Cerberus42 on 2005-11-24
yes i did download windows 98 SE rofl

it wouldn't install off the cd though, so i copied it to the hd and installed from there, it gives me the same problems as the recovery disk verison would have, but now it has better hardware support

i also downloaded windows ME, which was a horrible waste of time lol
(no win8 is not on this comp, it is on my old 333 mhz one that i felt like reviving, it hadn't been opened since we got it in 98 (the case))


and i will probably need a bit of help when the time comes thanks for the info

---

### Post by yesplease on 2005-11-24
I did even worse, I bought Windows Me. After all these years I still feel that MS ows me an operating system :)

---

### Post by aysiu on 2005-11-24
I've seen the Windows boot menu before, and it doesn't look that different from Grub's boot menu: black screen, white text.

If you want to Window-fy the Grub menu, you can change the boot splash image as well.

That said, it is *possible* to copy the Ubuntu boot partition to a floppy and somehow make that part of the Windows boot.ini, but it's annoying, especially for newbies who don't know what they're doing.

It's *far* easier to just install Grub to the MBR, as Grub will automatically add Windows to the boot menu.

You can change Windows to be the default boot option and make the timeout 1 second or 2 seconds if you want.

This is the best resize and dual boot guide I've seen:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[quote=cerberus42]I want to resize the NTFS system without destruction by 20 GB (it currently occupies the whole drive) and put ubuntu on the free space. This is a family computer and i absolutely cannot screw this up.[/quote] This really worries me. Yes, the Ubuntu partitioning tool is nondestructive, but you're an idiot (clinically speaking--I don't mean this as a direct insult) if you are planning to resize a partition and install a new operating system without backing up all your data first.

Back it up.

Back it up. I'm not kidding.

I don't care if you have to burn 150 CDs, use 350 floppy disks, or borrow a friend's external hard drive. Back it all up before you do anything.

Installing a new OS without backing up your data is like driving a motorcycle on the highway with no helmet.

---


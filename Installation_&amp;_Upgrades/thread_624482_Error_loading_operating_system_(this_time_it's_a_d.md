---
title: "Error loading operating system (this time it's a different story)"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by shoorik1987 on 2007-11-27
OK i know there are a bunch of similar stories about this out there. Trust me i have been reading bunch of posts on this forum and googling all over the web for several hours on my girlfriends laptop and nothing has helped. Tried downloading all types of recovery stuff for windows, ubuntu, downloaded that grub thing tried that to... Who knows maybe I'm doing something wrong. 

What I have figured out from all the posts is that it in some way has something to do with dual booting.

So here is the story:

First of all i would like to clarify that i am a total noob at this... so don't hate :)

It starts with me installing ubuntu over WinXP a couple of day ago. I didn't partion the hard drive, so I installed Ubuntu 7.10 over the whole hard drive. 
Some time after that i regreted my choice and decided to go with dual boot or whatever it's called... so I looked around a bit in the forums (not enough apperantly, otherwise everything would have been ok now) and downloaded this software, i think it was Gparted. I partioned my 200gb harddrive 150gb for ubuntu and 50gb empty space so i could install windows. That went nicely but, after i got XP installed I couldn't fire up ubuntu. (I tought it would let me choose  which one to boot) 
So i boot up Gparted trough the cd that i created there i right clicked on the windows hard drive and unchecked the boot box and checked it on the ubuntu harddrive. 
When I restarted my computer I got the "Error loading operating system" message. 

Can anyone plz help me?

I can't boot any CDs because I get the error before i even get a chance to get to that phase...

(I can access that blue setup screen in the begening tho by pressing delete in the beginning)

I can also access some other screen by pressing TAB button... It popps out a screen with some options and this messege:
"Create Raid array with the hard disks attached to VIA RAID controller"

I got absolutely no clue what that means, but I can't choose any options there except for escapte button which takes me out of there.

So can anyone plz help me with this?
BTW sorry for all the spelling errors and such.

---

### Post by confused57 on 2007-11-27
Your Windows partition needs the boot flag active.  You can reinstall grub to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

See if your Windows will boot, by resetting the bootflag...then reinstall grub to the mbr.
You'll have to manually add a Windows entry to grub...open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a small "L"
The output from fdisk -l will help someone give you the correct Windows entry in grub's menu.lst.

Added:  I just noticed you can't boot any cd's...you might try going into your bios setup and disabling Raid, if it's enabled(ignore this, don't think it would help).
Here's an excellent guide for setting your bios to boot your cd drive first:
[http://www.users.bigpond.net.au/hermanzone/p1.htm](http://www.users.bigpond.net.au/hermanzone/p1.htm)

---

### Post by shoorik1987 on 2007-11-27
> **confused57 said:**
> Your Windows partition needs the boot flag active.  You can reinstall grub to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

See if your Windows will boot, by resetting the bootflag...then reinstall grub to the mbr.
You'll have to manually add a Windows entry to grub...open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a small "L"
The output from fdisk -l will help someone give you the correct Windows entry in grub's menu.lst.

Added:  I just noticed you can't boot any cd's...you might try going into your bios setup and disabling Raid, if it's enabled(ignore this, don't think it would help).
Here's an excellent guide for setting your bios to boot your cd drive first:
[http://www.users.bigpond.net.au/hermanzone/p1.htm](http://www.users.bigpond.net.au/hermanzone/p1.htm)

Thanks that helped. Went in bios setup and it was set to boot hard drive before cd..so i set it to boot cd instead and it worked... it was also set to quick boot and skipped the "Press ESC to boot" screen, so i changed that by putting Quick Boot from "Enabled" to "Disabled"

Thanks alot

---


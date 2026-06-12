---
title: "How To get Internet?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Dogfighter on 2006-12-22
yea, its obvious im a complete linux noob ](*,)  forgive me.
im going to install ubuntu, did read a tutorial and theres written that u need to download few things.
soooo.... im not connected through a router what means i need the system up and running to have an internet connection (PPPoE).
how do i do that? couldnt find something in tut, also did a search here without results that would have helped me.
thanks in advance, and if i posted in the wrong category move it :)

---

### Post by nalmeth on 2006-12-22
Hmm, if I have you right, you're wondering if the install will finish without an Internet connection?

I'm pretty sure it will. I don't actually know what components are installed over the internet, but I think its just updates. 
I've installed Ubuntu on a PC with no internet before, but that was a couple releases back. 

In any case, I think you're good to go, no harm in trying anyway. Hopefully your other partition is backed up just in case anything goes wrong with it.
Unless of course you're asking something different.

EDIT: Wait a tick.. The system will be up and running if you're installing from the liveCD, so this shouldn't be a problem. Have you used the liveCD and the internet doesn't work?

---

### Post by Dogfighter on 2006-12-22
erm, i dont know if its the livecd :-? 
ive got this 1: ubuntu-6.06.1
pretty much i just need to know how to set up a internet connection, in windows it would be easy, settings - network - add new network.
sorry if i didnt make this clear in the first post :-| 
so this is what i need to know, how to do so.

---

### Post by nalmeth on 2006-12-22
That is probably the liveCD.

Just put the disc in the tray, and reboot. The CD will load Ubuntu into your RAM and you can play around with the OS without installing it, and without it touching your harddrive. 

When its loaded you can see if the connection is working or not. The equivalent place you're looking for is System -> Administration -> Networking.

I understand PPPoE has something to do with DSL modem or something?

Google turned up this page first result, it may help you out:
[http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux](http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux)

---

### Post by Dogfighter on 2006-12-22
yea its a dsl thing.
i do want to install it as its better as livecd :P and i dont just wanna play around with it, i wanna make it my 1st OS (in the future ^^)
when i can install it without an connection, set up my connection and install the missing stuff then, everything is fine. sounds like im able to do so. thanks for ur help :)

---

### Post by nalmeth on 2006-12-22
> yea its a dsl thing.
i do want to install it as its better as livecd :P and i dont just wanna play around with it, i wanna make it my 1st OS (in the future ^^)
 help :)
Right on! 
I don't think I made it clear, but the liveCD will boot up the temporary system, and then you will install it from there. Click INSTALL on the desktop.
Anyway, I think you'll figure things out. 
>  when i can install it without an connection, set up my connection and install the missing stuff then, everything is fine. sounds like im able to do so. thanks for ur
No problem. Enjoy yourself :)

---

### Post by Dogfighter on 2006-12-23
im back with more questions :P (sry! :D)
first of all, im still able to boot up windows after ive installed ubuntu right? 
secondly the "build in partitioning" wont work, but ill just do with partition magic, no biggie.
so i canceled the installation, and tried to set up an internet connection.
well... ive found it but i couldnt get it to work.
i did fill in my username and pw but ok was greyed out and not clickable (i dont have any other information?!).
what to do?

---

### Post by nalmeth on 2006-12-23
Ubuntu will install GRUB, a boot-manager, and it will add Windows to the list, so yes, you will have both. 
That is odd about the partitioning. I would advise you to defrag your windows partition before shrinking it, I have heard it can cause problems.
I don't have any experience with DSL modems, but try the link I gave you before, it seemed to have a procedure to it:
[http://www.wikihow.com/Configure-Hom...n-Ubuntu-Linux]("http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux")

Ask as many questions as you like! 
Cheers
EDIT: One more thing, if Partition magic can make EXT3 partitions, you can make one there. Otherwise, its totally fine just to leave enough unallocated space on the drive, and you can instruct Ubuntu just to use that empty space

---

### Post by Dogfighter on 2006-12-23
btw, in what system partition system? i can choose so many extensions lol i only know FAT32 (crap) and NTFS :rolleyes:
EXT3 will be the one?
ill try to defrag and try to redo the install then :)
*EDIT* just did read the link u gave, but that aint helpfull :X
i dont have a router, only a modem what i cant access. :?
well maybe some1 knows what to do, ill ask a friend as well, as hes using linux.
*EDIT2* :D
can i access the other drives too then? i know i cant use .exe and stuff, but browsing / moving files is possible?

---

### Post by Dogfighter on 2006-12-23
weeee!
ive managed to mess up and had to format my main partition and reinstall windows. pmsl.
as u know win is a piece of..... so of course it messed up once again.
here is what i did: formatted C: said install it there. and it did: format D: and installed on F: LOL
so.... will i get problems because win isnt on C: ? would suck :(

---

### Post by Dogfighter on 2006-12-23
everything is alright, install was no problem this time :P (my first post using linux! ^^)
anyway, thanks for ur time and help :)

---


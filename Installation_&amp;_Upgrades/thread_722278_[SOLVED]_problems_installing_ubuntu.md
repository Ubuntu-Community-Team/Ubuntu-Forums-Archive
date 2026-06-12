---
title: "[SOLVED] problems installing ubuntu"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by albyyx on 2008-03-12
I have been looking in the threads but i haven't find anything likely to this, so i hope i haven't missed the right one.

I'm trying to install ubuntu 7.10 x64 in my laptop, Intel core 2 duo 1.66mhz (i assumed this is for the x64 distro and not x86, but maybe i've assumed wrong). 

I have a windows partition, around 70gb over 120  (all in NTFS) which is the total of the disk, and i don't want to delete it (not yet, at least) so i'm trying to install it in 40gb more or less. 

So i download my dvd (because the device won't read cd's by any means, i am still trying to workout if it's hardware or software problem, but doesnt matter, the thing, i need the dvd.

I download it from the official mirrors, and i burn it, 2x without errors.
Then i boot it and check it's integrity, it says all is fine so i just boot it again and go to ubuntu and click install, so i'm going thru all the installation screens til i get into "partition"

I have currently tried with guided (use the biggest continuous space or something like that) and manual. The thing is that it starts thinking thinking and freezes. Been waiting up to half an hour with no activity in the hard disk and  the dvd rom at all, i cannot do anything or even move the mouse, it's  just frozen.

I have thought it may be because the 120 gb are in NTFS with no partitions, i haven't prepared the HD from windows before formatting, but i'm not really sure if this would matter under the partitioning tool.
I thought it also may be because of the x64, maybe i need the x86 since core 2 duo is 2x32?

to be honest im a bit lost with this, and i'd like to blow the whole windows from my PC as soon as i make sure i can make work the wireless adapter without problems (that will probably be another post, in the future)

Can someone please help meeee???
Thank you very much :D

---

### Post by Bruce M. on 2008-03-12
> **albyyx said:**
> I'm trying to install ubuntu 7.10 x64 in my laptop, Intel core 2 duo 1.66mhz (i assumed this is for the x64 distro and not x86, but maybe i've assumed wrong).

Search the net for your laptop.  Somewhere in the spec's it will tell you if it is x64 or not.

Just because it a duo core doesn't make it x64

This *may* be your problem.

Make a backup of everything you want off the windows partition that you want to keep.

Obviously if it isn't an x64 you'll need another CD.

Start with that.
Bruce

---

### Post by albyyx on 2008-03-12
Hi Bruce, 
Thanks for your quick reply. I've been browsing the web, ended up in acer webpage 
"Newest-generation Intel® Centrino® Duo mobile technology -- featuring the Intel® Core&#8482;2 Duo processor with Intel® Extended Memory 64 Technology (EM64T) -- delivers exceptional multitasking performance and reliable wireless connectivity wherever you go"
(from [http://global.acer.com/products/notebook/tm4230.htm](http://global.acer.com/products/notebook/tm4230.htm))

There's not much in the windows drive that i NEED to keep, just some pictures already backuped and couple of books from wiley and ubuntu, all the rest may be redownloaded if needed... problem is that i have the broadcom wifi adapter and afaik it may give problems... but that will be another point to worry if i manage to suceed in the installation

Any other clue?
Because i'm totally lost :(

Thank you

---

### Post by Bruce M. on 2008-03-12
> **albyyx said:**
> Hi Bruce, 
Thanks for your quick reply. I've been browsing the web, ended up in acer webpage 
"Newest-generation Intel® Centrino® Duo mobile technology -- featuring the Intel® Core&#8482;2 Duo processor with Intel® Extended Memory 64 Technology (EM64T) -- delivers exceptional multitasking performance and reliable wireless connectivity wherever you go"
(from [http://global.acer.com/products/notebook/tm4230.htm](http://global.acer.com/products/notebook/tm4230.htm))

There's not much in the windows drive that i NEED to keep, just some pictures already backuped and couple of books from wiley and ubuntu, all the rest may be redownloaded if needed... problem is that i have the broadcom wifi adapter and afaik it may give problems... but that will be another point to worry if i manage to suceed in the installation

Any other clue?
Because i'm totally lost :(

Thank you

Hi,
[LIST=1]
[*]Looks like your [NVIDIVA GeForce]("http://www.nvidia.com/object/linux_display_ia32_1.0-8756.html") card will be OK
[*] And a [HOW TO: Configure wireless cards with Broadcom chipsets]("http://ubuntuforums.org/showthread.php?t=25683")
[/LIST]

So now on to the installing Ubuntu with Windows Vista problem.

Looks like [Acer]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer") has pretty good support, although I don't see your specific model there.

That being said, I have seen were people have been having problems with Vista (mostly on a Dell) as it has a "Recovery" partition that is in fact the "boot partition", C:\ and Vista on D:\. Then during the boot process it changes the letters so it looks like Vista is on C:\

Check your HD and see if you have a Vista Recovery program or partition.
I'm going to search the forums to see if I can find some more information for you.

Bruce

---

### Post by albyyx on 2008-03-12
Hi Bruce
I don't use vista in the lappy, i bought it without OS so i could choose the one i like better, i'm sorry for missing this detail but i'm not used to post in forums
The one i'm running is winxp profesional 32 bits.
The grafic card is not the nvidia one, but the intel i cannot tell you the model because i cannot open that page from here, form work (awesome)

Thanks a lot again for all your help and sorry for the mess

---

### Post by Bruce M. on 2008-03-12
> **albyyx said:**
> Hi Bruce
I don't use vista in the lappy, i bought it without OS so i could choose the one i like better, i'm sorry for missing this detail but i'm not used to post in forums
The one i'm running is winxp profesional 32 bits.
The grafic card is not the nvidia one, but the intel i cannot tell you the model because i cannot open that page from here, form work (awesome)

Thanks a lot again for all your help and sorry for the mess

So you want to put Ubuntu on the laptop running Win XP - 32bit?

---

### Post by albyyx on 2008-03-12
Yes i would like to have both running i've done that before and it was nice because on desperate moments i always could run to xp... 
but now that i think... 
windows xp 32 and ubuntu 64 bits may not be compatible??
Don't kill me if they are not, i'm just terrible for computers... and i'm sorry if i made you waste your time :S
:frown:

---

### Post by Bruce M. on 2008-03-12
> **albyyx said:**
> Yes i would like to have both running i've done that before and it was nice because on desperate moments i always could run to xp... 
but now that i think... 
windows xp 32 and ubuntu 64 bits may not be compatible??
Don't kill me if they are not, i'm just terrible for computers... and i'm sorry if i made you waste your time :S
:frown:

It's OK, I'm learning too.  But you definately need the 32bit version for the WinXP machine.  :)

---

### Post by albyyx on 2008-03-12
i think I'm gonna blow the whole windows thing up.
I have long a wire to connect while i make the wireless work, if it doesn't so...
Because i will have to backup anyway :D

Do you have any clue how to mark this post as fixed? it's no longer an issue 

Thanks a lot :)

---

### Post by Bruce M. on 2008-03-12
> **albyyx said:**
> i think I'm gonna blow the whole windows thing up.
I have long a wire to connect while i make the wireless work, if it doesn't so...
Because i will have to backup anyway :D

Would love to be sitting beside you to watch that.  :)

> **albyyx said:**
> Do you have any clue how to mark this post as fixed? it's no longer an issue 

Thanks a lot :)

Yup, at the top of the page: Thread Tools > Mark as Solved.

BUT, after you do that come back here (even thought it's marked Solved) and add a post ... give us the results.  :)

Bruce

---

### Post by egalvan on 2008-03-13
> **Bruce M. said:**
> 

Just because it a duo core doesn't make it x64

Start with that.
Bruce

CORE DUO   equals SINGLE CORE definitely...   maybe 32 or 64 bits, don't recall at moment 

CORE 2 DUO  equals  DUAL CORE definitely -- 64BITS  definitely.

:popcorn:

---

### Post by egalvan on 2008-03-13
> **albyyx said:**
> 
windows xp 32 and ubuntu 64 bits may not be compatible??

:frown:

Don't have to be compatible, they aren't married, or even living together.  :lolflag:

Seriously, dual-booting separates the environments. They don't see each other, talk to each other, depend on each other  (let's forget about GRUB, it's not included in this debate)

:popcorn:

---

### Post by Bruce M. on 2008-03-13
> **egalvan said:**
> CORE DUO   equals SINGLE CORE definitely...   maybe 32 or 64 bits, don't recall at moment 

CORE 2 DUO  equals  DUAL CORE definitely -- 64BITS  definitely.

:popcorn:

Made me go and look it up: [Intel Core]("http://en.wikipedia.org/wiki/Intel_Core")

Core Duo = 32 bit
Core 2 Duo = 64 bit

Learned something new today.  :)

---

### Post by albyyx on 2008-03-13
I MADE IT!
yet i haven't blown up windows yet (but wireless is working without problems)
So i'm planning to blow the whole thing up tonight
*grin*
*evil smile*

---

### Post by Bruce M. on 2008-03-13
> **albyyx said:**
> I MADE IT!
yet i haven't blown up windows yet (but wireless is working without problems)
So i'm planning to blow the whole thing up tonight
*grin*
*evil smile*

Will be watching for fireworks in the sky tonight.  :)

---


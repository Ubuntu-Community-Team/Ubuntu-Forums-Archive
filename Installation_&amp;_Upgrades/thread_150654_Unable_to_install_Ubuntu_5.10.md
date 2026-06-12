---
title: "Unable to install Ubuntu 5.10"
date: 2006-03-26
forum: Installation &amp; Upgrades
---

### Post by bug80 on 2006-03-26
I downloaded & burned the CD ISO for Ubuntu 5.10. The MD5 sum was ok, but still the installation stops with an error during "Loading installation modules". Furthermore it says something about being unable to read the CD-ROM. Repeating that step and loading the modules manually doesn't help.

I tried three different discs, burned at low speeds (down to 8x). Since the installation always stops at exactly the same point (right at the beginning of "Loading installation modules") I don't think it's a burning speed problem.

My system is a Dell Dimension 9150.

Has anyone seen this before?

---

### Post by Sef on 2006-03-27
> burned at low speeds (down to 8x)

Try burning at 1x-4x.  Faster speeds can sometimes mess up the burn.

---

### Post by stefaninbern on 2006-03-27
x

---

### Post by bigmo on 2006-04-03
Well I'm having the same problem I downloaded both the install and live versions and burned them on CD (OK it was burned at x24). I also used the CD received from Shipit and they all fail at the same point.
How can 3 different CDs fail at the same point?
Surely that can't have anything to do with the burning speed of the CDs.

Has anyone found the actual problem?

---

### Post by repeat on 2006-04-03
I have a kind of same problem. I just downloaded, and tried to install Ubuntu Dapper Drake Flight 4. My installation stops at this point every time:
---
[!!] Install the base system

Debootstrap warning

Warning: File:///cdrom/pool/main/x/xfsprogs/xfsprogs_2.7.7-1_i386.deb
was corrupt

If I click 'continue' this message appears:

Warning: Couldn't download package xfsprogs
---

Anyone who knows what this means, or how to fix it?

I also downloaded Ubuntu 5.10 for some days ago, and the installation stoped at almost the same point. Tried to install it into two different computers (laptops)

---

### Post by bigmo on 2006-04-03
OK just a little update...
After 4 downloads, after wasting 17 CDs ](*,)  and trying to burn :mad:  them with 5 diffrent apps, I gave up. 
Well I kinda gave up... 
I tried downloading the development version live cd and that works like a charm.
obviously I will not install it on HD but just a little not to give you guys hope.

---

### Post by allstars47 on 2006-04-03
[QUOTE=bigmo]OK just a little update...
After 4 downloads, after wasting 17 CDs ](*,)  and trying to burn :mad:  them with 5 diffrent apps, I gave up. 
Well I kinda gave up... 
I tried downloading the development version live cd and that works like a charm.
obviously I will not install it on HD but just a little not to give you guys hope.[/QUOTE]

i have the same problem ,too
i've tried Breezy cd,dvd and ....6.04 (flight 5)cd and dvd ,
all in AMD64 version.
but only 6.04 cd would work.  
but when i boot into ubuntu
some adminisration tools wont work!?
like networking,disk manage...etc
the only way to make it work is to type the command in terminal
like $>sudo disks-admin      ............................
so now i am trying to reinstall it,and with Breezy,not Drapper again
i plan to update my ubuntu after June would be a nice choice...

---

### Post by bug80 on 2006-04-07
It seems more people have the same problem. I didn't try burning at speeds lower than 8x. Maybe I will in the future, but I really think it has nothing to do with it, since all CDs fail at exactly the same point, no matter which burning speed I used (just like Bigmo).

I did try to select another language (English instead of Dutch) to see if only some language related files were corrupted, but that didn't help.

I installed Mandriva 2006 (from a DVD burned at 4x) without problems and I'm using that now, so there is no need for me to install Ubuntu anymore

**However** if some Ubuntu developer wants to know what's going on (maybe it's a bug) and has some suggestions I will be glad to try them out with my Ubuntu CD.

---

### Post by va1ha11a on 2006-04-12
I am having the same problem...I think it may be the cd image. It happened on my laptop and server install. But I used an image froma different mirror and all seemed ok so far. [edit] no i forgot the new image i got was kubuntu

---

### Post by kchukchukchu on 2006-04-14
Hello, everyone, 

I have also tried to install Breezy for more than 20 times, using up 3 CDs and checking sums and I was burning at 8x.  but my installation (for the same CD) either failed at loading CD (before partitioning) or installing base system (exactly the same error as a message above).  

Just wondering if anyone has figured out a way to do this, I suppose I should just try to download from the version for a different country?

thanks, just to let you know that i also have the same problem,
Kay

---

### Post by RussellW on 2007-01-12
> **repeat said:**
> I have a kind of same problem. I just downloaded, and tried to install Ubuntu Dapper Drake Flight 4. My installation stops at this point every time:
---
[!!] Install the base system

Debootstrap warning

Warning: File:///cdrom/pool/main/x/xfsprogs/xfsprogs_2.7.7-1_i386.deb
was corrupt

If I click 'continue' this message appears:

Warning: Couldn't download package xfsprogs
---

Anyone who knows what this means, or how to fix it?

I also downloaded Ubuntu 5.10 for some days ago, and the installation stoped at almost the same point. Tried to install it into two different computers (laptops)
In the odd case that anyone else runs across this thread looking for a solution to this very problem I hope this will help.

I have a Gateway Solo laptop 9300 series that I wanted to put Ubuntu on. I burnt a CD and tried to run it. No good. I searched for answers. Tried the alternative. I tried burning it slower. I tried different media. I tried Kubuntu, Xubuntu, Edubuntu, Knoppix, and Slackware. I tried this version and that version. The only things I could get to run on it were XP, PCBSD and FreeBSD. I used Darik' s Boot and Nuke and tried some more. One Ubuntu CD worked on a tower I have but not on the laptop.

I pondered on this quite a bit as you can see, frustrated over it, Googled my anus off. Finally the only thing left that it could be, in my mind, turned out to be the problem......

the CD player in the laptop!!!!!!!!! I don't know why. It's a 24x, should do the job just fine. NOT! I had another one that I could use that was newer and faster and it is also a CD/RW. I popped it in and in record time, VOILA!! Kubuntu is now loaded and ready to go. 

I hope that maybe this will help someone else before they spend(waste) as much time and patience as I did. If not, it's good to get it off my chest!

Happy Ubuntuing to all!!!

---


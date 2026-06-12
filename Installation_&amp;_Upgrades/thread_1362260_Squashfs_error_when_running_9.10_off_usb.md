---
title: "Squashfs error when running 9.10 off usb"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by bimalc on 2009-12-22
So I have been trying all day to load netbook remix by way of a kingston 4gb usb flash drive which I used both unetbootin and the instruction on linux pendrive to make (planning to dual boot with windows 7 on my S12 with ion) and all I've gotten is a bunch of 'sqashfs' errors ([https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)).
 
I have tried:
 
changing the IDE mode to compatibility instead of SATA (made windows unbootable, didn't help at all with loading ubuntu)
 
checking the MD5 sum(passed)
 
using the ACPI=off  option
 
using IDE=nodma option
 
using both of the above options simultaneously.
 
The furthest along I can get is the checklist where you see the ubuntu logo and it iterates all the things it is checking/loading and saying 'ok' to.  There are more 'tasks' listed than 'ok's (if that makes sense; either this is by plan, or there are somethings failing and this might be a place to look for clues as to what's going wrong) but eventually the screen will flash over with a burst of color (I'd swear it was a desktop with a blue background, but at this point I might just be hallucinating) and then it goes black except for a watch (or at least what looks like a watch to me) sitting in the middle of a screen.  The system is totally unresponsive at that point until I tried tapping the power button and then I got dumped back at a terminal like environment (but without an actual prompt I could type at) and I'm presented with a string of 'squashfs' errors.
 
Using various combinations of runtime options and bios configurations, I've variously managed to end up at the same point before ubuntu even went through the checklist of things it was trying to load and one time even ended up at a terminal prompt Ubuntu$ubuntu, but I've never successfully made it into the gui ...
 
I like to think I'm a reasonably sophisiticated end user, but I can't find any comprehensive solution to the whole squashfs error scenario ...
 
I'm going to try and bum a surplus USB off of someone in the next couple of days (I'm stuck in western NY at the inlaws without access to a car) in case it is the flashdrive, but other suggestions would be appreciated.

---

### Post by SuperEngineer on 2009-12-28
take a look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478547)

if your situation is the same as I had [assuming USB v CD install is the same] I resolved it by 'accident'!!

You will find, however, that BIOS disk settings (SATA v RAID emulation) do have to be set correctly.  I have a multi-boot set up and when experimenting with BIOS I find that I lost the abilty to boot to WinXP (although it was showing in GRUB)... resetting immediately got got it back.

Persevere... I did and now multi-boot betwwen 9.o4, 9.10, Mint and WinXP perfectly ok.

---

### Post by rohit2412 on 2010-01-11
@SuperEngineer

I couldnt understand ur solution, my problem is similar but i cant even boot off a live usb. Could you please elaborate?

---

### Post by C.S.Cameron on 2010-01-11
I would re-format the drive in FAT32 and try unetbootin again with the remix iso.

---

### Post by rohit2412 on 2010-01-12
@Cameron I have the same error and have done that(reformat) 3 times with 32 and 64 bit desktop editions.. Not working yet. I just booted 9.04 in single try and memory tests pass. This doesnt look like faulty hardware to me.

---

### Post by rohit2412 on 2010-01-12
I just installed my system using debootstrap...and the new installation works fine..except for that crackling sound...but it has solutions...

So i dont know what was faulty...But it was only for live usb and the installation works now...

---


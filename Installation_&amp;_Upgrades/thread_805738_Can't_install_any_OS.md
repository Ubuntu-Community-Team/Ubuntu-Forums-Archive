---
title: "Can't install any OS"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by jappish on 2008-05-24
Hey!

Just got my new PC yesterday and I'm having problems I've never expierenced before, here's my setup

- Memory: Corsair 2x1GB DDR2 8500 dominator
- MB: Gigabyte GA-EP35-DS3 iP35
- CPU: Intel Core 2 Quad Q9450 2.66Ghz 12MB cache
- Optical Drive: Sony NEC Optiarc AD-7203S SATA
- HDD: maxtor SATA 1, I also have a Seagate SATA 2 500GB but I don't wanna install an OS on that drive
- PSU: Xilence 500W
- GPU: Asus Geforce 8500GT 256


I tried installing Ubuntu 8.04 x64 and this happens:

I get to the menu where I can choose language and then I hit install.

It starts loading and I get to the screen with the new Ubuntu background and then the cd stops spinning and nothing else happens.. I can move the mouse but there nothing to interact with...and that's where I'm stuck. So I tried the text installer CD instead:

With the text installer it seems that the the installation process completes successfully and when Ubuntu loads and almost gets to the log in screen it stops, just before the login screen is shown.. now I only have a black screen with mouse and loading icon that isn't moving anymore (the mouse still moves)

So, in all my anger I took the Vista x64 disc and tried that instead.. Vista gets to the first blue screen of the installation loader and I only get to use the mouse, Once, when I waited for an hour I got to choose language in vista too, but then it gave me an error code 0x80070570 (cannot read D\sources\install.wim)
The disc is in perfect condition

thnx

---

### Post by Kevbert on 2008-05-24
First thing to do is check your memory.  From the Ubuntu disk run the memory test (a menu option).  When you first turn on the PC it does a very crude memory test (during POST) and of course nothing has warmed up. The Ubuntu one is a bit more extensive and should find if there is any memory problems.

---

### Post by jappish on 2008-05-24
Thank you for the fast reply!

I actually found a way to fix it.

When I almost gave up hope and wrote my first post here at Ubuntu forums I went back to the computer and tried installing win XP 32-bit, and it worked nice.

Then I tried ubuntu 7.04, also 32-bit and liveCD worked without any problems.

Then I remembered that I've seen a setting in BIOS where I could change a setting from 32-bit to 64-bit, in the explaination box it sead to set this setting to 64-bit if you are installing a 64-bit OS, and I did, but no 64-bit OS would install when it was set to this, so I changed it to 32 and then ubuntu 64-bit installed nicley...

I'm no expert but it seems as if there is a bug in BIOS :s anyways, the ubuntu 8.04 64-bit has just finished installing and now I have stuff to do :D 

Hope this helps anyone with the same problem


EDIT:

Still can't install Vista 64 so I guess the solution above only applies on ubuntu, now running mem test, doesn't look good, about 20 errors after 7% completion :(

---

### Post by Kevbert on 2008-05-24
It suggests that you may have bad memory or that the memory is not seated (fitted in its sockets) correctly.  As this is a new PC I'd advise you to take it back to where you bought it. If you decide to refit your memory yourself watch out as the memory is static and you could easily damage it or something else.

---

### Post by wpshooter on 2008-05-24
I would suggest that you check on your BIOS version and update it if there is a newer version available.  Remember, because a computer is "NEW" does not necessarily mean that it has the latest BIOS version installed.

Good luck.

---

### Post by jappish on 2008-05-24
I just ran memtest with just one module inserted and after full test had past I had 149 errors @ failing address 0003feee788 Good: 00000000 Bad: 00000001 Err-bits: 00000001

The other module showed 154 errors on the same adresses

Then I put both modules together and ran the test, after 30 minutes (completed full tests about 2½ times) it showed 275 errors on the same addresses

I don't know if this is so serious

I have been very carefull when handlig the RAM, I used a ESD bracelet

The thing is, Ubuntu works fine now.. how come vista won't install and how come ubuntu did, if the RAM is damaged.. I'll check my BIOS version and see if I can upgrade it

thnx guys

---

### Post by Kevbert on 2008-05-24
I'd still get the memory replaced as your PC is so new.  If you don't change the memory sticks you're liable to get random crashes and lockups, and could easily loose your precious data.  I recently upgraded my RAM to 4Gb and the memory tests all passed after I resolved a seating problem.  Out of interest if you swop the memory sticks around, do you get the same errors (you shouldn't).  A bios upgrade won't solve this and may cause a warranty problem.

---

### Post by jappish on 2008-05-24
I'll try swapping the memory sticks around and I'll get back to you later, I have taken pictures of the memtest results, I'll see if I can attach them later.

Replacing the modules seems like the only thing to do, I have no more ideas on what to try, but it still seems kinda odd that both xp and ubuntu 32-bit worked directly :s

thnx again

---

### Post by pixel :-) on 2008-05-24
if it's the same address,it maybe that it's the socket that is damaged, try the same ram module on all sockets.Be aware that you going to corrupt your system if you use bad memories.I'll recommend to reinstall when you settled the memory problem, you 'll have random problems, and it will be a mess to guess whats corrupted.

---

### Post by jappish on 2008-05-24
Ok, I really thoght that it was normal to get a few errors, 600 in one hour seemed like a bit too many.. hmm.. well, I have to return them on monday then...

But I'm still wondering... could the errors be caused by the MOBO? I mean if the MB is damaged somehow?

I think I check and see with some friends if they might have som RAM that fits on my mobo before I send back my ram

---

### Post by Kevbert on 2008-05-24
> **jappish said:**
> Ok, I really thoght that it was normal to get a few errors, 600 in one hour seemed like a bit too many.. hmm.. well, I have to return them on monday then...

But I'm still wondering... could the errors be caused by the MOBO? I mean if the MB is damaged somehow?

I think I check and see with some friends if they might have som RAM that fits on my mobo before I send back my ram

If the motherboard is damaged the errors are likely to be the same when you swap the memory around (probably a damaged track or dry joint).  If you do try your friend's memory check it's the right speed and type before you try it out.

---

### Post by jappish on 2008-05-25
Hi again!

I actually updated the BIOS yesterday and today I ran memtest for an hour without a single error, now the thing is, before I ran the test I moved both RAM modules to the other DDR channel, so I don't really know if the errors came from the memory modules, the other DDR channel or if the errors occured because the old BIOS didn't handle the modules properly.

I also discovered that the installation problems with Ubuntu might be related to the fact that I used cloneCD to burn the .iso files with, I tried the the cd in another pc and I expierenced similar problems...

I have a lot of stuff to do the coming days but I'll report back when I try some more configurations.

thnx

---

### Post by Kevbert on 2008-05-25
Good to hear that your memory is now working.  I wouldn't have thought that the bios would have anything to do with it.  The 32/64 bit option which you had in the bios previously was probably related to the amount of memory that you could use (ie address length), so it wasn't the cause of the errors.

---


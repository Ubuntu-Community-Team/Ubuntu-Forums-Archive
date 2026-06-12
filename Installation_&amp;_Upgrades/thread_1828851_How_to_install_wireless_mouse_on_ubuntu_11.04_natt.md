---
title: "How to install wireless mouse on ubuntu 11.04 natty"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by vcodek on 2011-08-19
Could someone tell me the way how could I install my
Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]
wireless mouse on my ubi?

lsusb says:
Bus 001 Device 007: ID 062a:0102 Creative Labs Wireless Keyboard/Mouse Combo [MK1152WC]

Thanks a lot!
Regards: Arpi

---

### Post by Mark Phelps on 2011-08-21
You don't install wireless mice/keyboards -- you just plug them in.

If you're asking about install software that came with them -- you're out of luck.  That's Windows software and won't work in Ubuntu (or any other Linux distro).

That means that while you should get basic mouse and keyboard functionality in Ubuntu be default, you won't get fancy stuff (like special keys on the keyboard, special buttons on the mouse).

---

### Post by vcodek on 2011-08-26
Ok!
Thanks.

when I mentioned "install" I just meant 
make the basic functions (cursour moves, cliks) work. And not make special functions avaliable.

Thanks again!

---

### Post by Mark Phelps on 2011-08-27
> **vcodek said:**
> Ok!
Thanks.

when I mentioned "install" I just meant 
make the basic functions (cursour moves, cliks) work. And not make special functions avaliable.

Thanks again!

Those should work by default.  If they're not working, that means Ubuntu doesn't really recognize the device and has not installed the proper drivers.  Which means, basically, that you have to try some different hardware.

---

### Post by MAFoElffen on 2011-08-27
> **Mark Phelps said:**
> Those should work by default.  If they're not working, that means Ubuntu doesn't really recognize the device and has not installed the proper drivers.  Which means, basically, that you have to try some different hardware.
I've have my own questions on this Mark...

I know on one side you are correct.  The default setting of Ubuntu is set to PNP and to use HAL to pole for a mouse and keyboard (constantly).  The user can remove and plug in that equipment and it "should" be recognized.  That "should" is inconsistent and frustrating!!!

On wireless and optical (ir), I'm still not completely sure on that... I have some Logitec and Microsoft wireless combos.... and some the mice will work, another the keyboard...  But they were all older (recycled) used equipment, so I could never verify if I had one "set" that really worked, without going out and buying one -- without verifying beforehand that it was going to work with Ubuntu..  

Curious to the other side of this-- I do enough installs of Desktop and Server... and testing of dev versions... to notice that those same keyboards (and mice combos) "are" listed in the keyboard install lists in the Desktop LiveCD's and Server Install  CD's.   

So the curiosities that brings up "is" :
 - If they are listed <> they must be supported somehow.
 - If they are supported in a list "separately <> there most be something different with the drivers or there most be some other functionality  that those drivers add.
 - Another concern along those lines is, that if they are listed separately, then maybe they don't get autorecognized and "need" to be specified..

So, following that logic-- the next questions would be:
 - How do you specify one of those keyboard/mice combos outside of a fresh install?  Those drivers and configs need to be maintained somewhere on the system...  
 - If an "install" can install those drivers, then those drivers are available... 
 - If an "install" can install those drivers, then there must be a way to install them "someow" after an install- even if manually.
 - Where is this support keyboard list maintained in the wiki? (Supported Hardware)  I cannot find this same list in a search, but I guess I could look through the embiquity scripts (the install scripts) to find it on the LiveCD... 
- If there was a supported list, people could look up - oh, this show work...

Yes-- "I've" thought about these questions... and still am.

---

### Post by MAFoElffen on 2011-08-27
This thread got me going again on this...

At least for the keyboard part of this:
In Gnome > System > Preferences > Keyboard > Keybiard Type > press on the keybaord type listed on the button... It will bring up a list // which keyboards(*) regular, wireless and such are listed.  

* - Some of the keyboards listed are parts of combo sets...

Mice:  Types not found as be able to be changed (yet)

---

### Post by vcodek on 2011-08-28
Hy fellows!

The problem was caused by the batteries, I changed to rechargeable type.
Despite these batteries can work quiet well if
I use it as tv remote controller energy source or
flashlight energy source.

I assumed that this could be enough for a wireless mouse too,
but it is not enough!

Ps: May only rechargeable batteries are capable for my
mouse. I don't know, I have not found any user guide!  


Thanks your replies!
Regards: Arpi

---


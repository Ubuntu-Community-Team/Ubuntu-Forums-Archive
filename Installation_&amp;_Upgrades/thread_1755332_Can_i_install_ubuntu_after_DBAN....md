---
title: "Can i install ubuntu after DBAN..."
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by ThatCoolGuy220 on 2011-05-11
Im wiping my Hdd cause the swap isnt clean and it stucks at **Preparing To Install Ubuntu**, screen

Im doing it by  Dod short method

But im wondering if my PC could get Bricked, F...ed or Screwed after this .](*,)

Or will everithyng be Fine?

Also my usb is being DBANED idk why? but i hope i can still use it after this.


Note:

51%

---

### Post by ThatCoolGuy220 on 2011-05-11
huh?

---

### Post by ThatCoolGuy220 on 2011-05-11
76%:popcorn:

---

### Post by wilee-nilee on 2011-05-11
> **ThatCoolGuy220 said:**
> Im wiping my Hdd cause the swap isnt clean and it stucks at **Preparing To Install Ubuntu**, screen

Im doing it by  Dod short method

But im wondering if my PC could get Bricked, F...ed or Screwed after this .](*,)

Or will everithyng be Fine?

Also my usb is being DBANED idk why? but i hope i can still use it after this.


Note:

51%

All dban does is wipe the drive with and removes the partition table, including the mbr=1st 512MB, you shouldn't have a problem. 

Not sure if that is the fix for your problems though, but you never know.

---

### Post by ThatCoolGuy220 on 2011-05-11
thx bro

usb is working like if it was brand new.

But.....................

I had to Format it after that my other PC asked for it 

Now my doubt is how do i format my HDD

or will the LIVE CD/USB do it?

---

### Post by wilee-nilee on 2011-05-11
I would just boot the live cd/or thumb  open gparted click on device-create-partition-tables and run the default. You can just close gparted hit install and choose the whole disc from the choice of install gui.

You can also in gparted make custom partitions then choose custom in the same gui you would choose whole disc if that was what you wanted instead(I presume you understand the either or in this explanation).  

Here is a link for having a separate home partition, apparently good for saving stuff, never do this so I can only link you.
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

Not the best of links, but lots of people on the forums do this so if you decide to roll this way; start a thread with a header mentioning your goal, separate home...etc, and I suspect you will get the info you need for this. 

Main thing here really though is the first instruction just make the partition table in gparted, and you can install to the whole disc without building partitions with the install to whole disc choice.

I'm going to crash shortly if you respond, I may not be awake hopefully, lol.

---

### Post by ThatCoolGuy220 on 2011-05-11
lol im feeling like hitting the desktop soon.

And about Separate home, it looks very interesting i will look dor that in the morning or aftrnoon it depends on at wich i wake up.............

Have a good nite

---

### Post by ThatCoolGuy220 on 2011-05-12
the /home should be done with live CD?

Cause Gparted on live Cd doenst work..

Also can i use the Puppy live Cd to do it 

And wouldnt remastersys. do the job?

---


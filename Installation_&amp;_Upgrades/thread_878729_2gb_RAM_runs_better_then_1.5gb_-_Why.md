---
title: "2gb RAM runs better then 1.5gb - Why?"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Crath on 2008-08-03
Hello all, and thanks for helping.

I have 2gb RAM installed in my desktop and love it, but it has been giving me some problems.  At random times, ubuntu just freezes up and never comes back.

Now back a week ago before i switched this computer from xp to ubuntu, it was doing the same thing in xp, just freezing up at random times and it had never done that before.


Whenever I take out one of the 1gb sticks and put in a 512 stick (1.5gb total) everything is flawless and I can't get it to freeze


I am pretty sure my sticks are both good, because everything recognizes the ram (both ubuntu and xp recognized it)

Yes, my motherboard supports 2gb and I did recently upgrade the bios.

What could be causing these freezing issues?  Any info is greatly appreciated! thanks

---

### Post by Pumalite on 2008-08-03
To be sure memory is good you have to run a memtest lasting 8 to 12 HRS
[http://en.wikipedia.org/wiki/Memtest86%2B](http://en.wikipedia.org/wiki/Memtest86%2B)

---

### Post by Crath on 2008-08-03
Ok, I will run this, but in the mean time, do you think there is any settings i need to change in ubuntu to make it utalize the ram efficently?

---

### Post by coffeecat on 2008-08-03
> **Crath said:**
> Whenever I take out one of the 1gb sticks and put in a 512 stick (1.5gb total) everything is flawless and I can't get it to freeze

Does that happen with one particular 1 Gb stick, or does it happen if you replace either of the two 1 Gb sticks with the 512? If it's only with the one stick, then it must be a faulty stick.

But if this happens with both 1Gb sticks, then I have another possible explanation. Does the motherboard support dual-channel mode, and have you put the sticks in the appropriate slots so that they would run in dual-channel mode? The bad news is that some motherboards are a bit flaky with this and the system freezes up even when you put in perfectly good memory.

I had a motherboard (now consigned to the junk :( ) on which I was multibooting Windows and several Linux distros all of which would freeze up randomly when I put the memory modules in as a dual-channel pair. I tried no less than **three** different pairs, one each from Crucial, Kingston and PNY - all good makes - and the system would freeze with all three. It worked perfectly with just one memory stick. I would get more freezes with the PNY than with the Crucial and more with the Crucial than with the Kingston, but that may just have been down to chance. I refuse to believe that I was unlucky enough to happen upon three faulty sets from three different manufacturers. It must have been the motherboard.

---

### Post by Crath on 2008-08-03
yes i here are the configs i tried sofar, and seemed to have issues. 1gb(a) will indicate the 1st of 2 sticks, and (b) the other

Bad Configurations
1gb(a) 1gb(b)

Good Configurations
1gb(a) 512mb
1gb(b) 512mb
1gb(a)
1gb(b)
512mb

Now, about this dual channel stuff, what is going to be the difference between the 2 sticks that will determin which goes in which slot? I read my motherboard manual and it didn't say anything about certains lots for certain chips.

---

### Post by eldragon on 2008-08-03
go into the bios, and relax timings a bit. CAS, RAS...if you are allowed to underclock the DDR bus, do it by 1 or 2 mhz

that should make memory disparity disappear (or not matter).

---

### Post by wpshooter on 2008-08-03
> **Crath said:**
> yes i here are the configs i tried sofar, and seemed to have issues. 1gb(a) will indicate the 1st of 2 sticks, and (b) the other

Bad Configurations
1gb(a) 1gb(b)

Good Configurations
1gb(a) 512mb
1gb(b) 512mb
1gb(a)
1gb(b)
512mb

Now, about this dual channel stuff, what is going to be the difference between the 2 sticks that will determin which goes in which slot? I read my motherboard manual and it didn't say anything about certains lots for certain chips.

From the above, my "guess" is that the 1gb modules are NOT an exact matching pair, i.e. there is at least some minor difference in these 2 modules that is causing the problem.

On a motherboard that I installed in a system recently, it came with (2) 256mb modules that were both supposed to be and were even label that same as PC2100 memory but from the problems that I was having to get them to work together, I highly suspect that one of the 2 modules was mis-labeled and was in actuality a 128mb module instead of a 256md module.  Mistakes do happen !!!

---

### Post by Crath on 2008-08-03
the ram should be the same because it was 1 package

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231039](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231039)

---

### Post by Crath on 2008-08-03
i just realized i had the title backwards, lol!

---

### Post by xen-uno on 2008-08-03
What mother board? If relatively new, it may require DDR2 533 as a minimum but that wouldn't explain it running fine under XP.

---

### Post by Crath on 2008-08-03
its probably about 5 years old now? :\

the processor is 800mhz fsb, yuck

---


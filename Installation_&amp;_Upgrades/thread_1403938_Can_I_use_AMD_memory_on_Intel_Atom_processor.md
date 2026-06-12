---
title: "Can I use AMD memory on Intel Atom processor?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by bama7474 on 2010-02-10
I just purchased a Toshiba NB305-nb410bl, it came with 1 Gib of RAM...I have a HP Pavilion with 4 Gib of Ram...Can I swap one of the 2 Gib modules out of my HP and replace the 1Gib module in my toshiba?  The HP uses a AMD processor and my Toshiba Netbook uses an Intel Atom Processor.

Specs on the HP Ram:
667Mhz 2Rx8 PC2-5300 2Gib

Specs on the Toshiba:
800Mhz 2Rx16 PC2-6400 1Gib

Thanks

---

### Post by northrup on 2010-02-10
You could, since they are both SO-DIMMs and are both DDR2, but there are some considerations you need to be aware of:

First, you're replacing 800 MHz RAM with 667 MHz RAM.  Although this would theoretically work fine, in reality, the slower clock speed will actually negate the performance advantage of the higher amount of RAM.  You can reduce hard drive seek times by relying less on swap space, but your CPU's access to the RAM itself will slow down.

Second, verify that the Toshiba's mainboard supports the additional RAM.

Third, if there are two SO-DIMMs in your Toshiba, and you're only replacing one, the mismatched clock speeds will cause problems.

Fourth, check the speed of the Atom CPU.  Not it's internal speed, but the other MHz value.  Make sure it supports the 667 MHz RAM.

Basically, the FSB speed (frequency of the communication between the CPU and RAM) is only as fast as the slowest component.  Therefore, 667 MHz RAM and a CPU with, say 1000 MHz FSB clock rate will only have an FSB speed of 667 MHz, and vice versa.  Keep that in mind.

Personally, I would just check eBay or Amazon (both are my friend in computer building) and find an 800 MHz 2 GB DDR2 SO-DIMM.  But that's just me.

---

### Post by bama7474 on 2010-02-10
Thanks Northrup,

I found out that my Processor has a 667Mhz FSB so I should be ok, right?  I'm wondering why they would put an 800Mhz module in if my CPU was only as fast as 667Mhz?  My Netbook only has one memory slot so the clock speed match isn't a problem, but thanks for telling me cause I was going to put the 800Mhz chip in my HP with the 667Mhz.  My biggest concern was that the memory was designed for an AMD processor and I have a new Intel Atom processor which is unfamiliar to me.  I didn't know if AMD and Intel were that kind of friends#-o to make compatible memory modules...Thanks for your reply though, you shed the light on some things I wasn't aware of.

---


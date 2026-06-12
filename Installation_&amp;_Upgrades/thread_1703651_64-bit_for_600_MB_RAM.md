---
title: "64-bit for 600 MB RAM?"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Bucic on 2011-03-09
Is it worth it to install 64-bit version of Ubuntu on 600 MB RAM low-end computer? All FAQs and posts mention 3 GB RAM limit as the main  culprit of 32-bit versions but obviously it's not my concern.

---

### Post by kerry_s on 2011-03-09
yes, it's fine. i had 64bit with 512mb starting out.
the purpose of 64bit is to take advantage of 64bit features, not just support more ram, it does more than that.

make sure you make at least a gig of swap, 64bit will use about a 100mb more memory than 32bit would use, your system will still be faster with 64bit.

---

### Post by TenPlus1 on 2011-03-09
Having a 64-bit Ubuntu running will use more memory than the standard 32-bit version because of the longer memory addresses so it's probably easier to simple use 32-bit ubuntu until you get more than 1gb memory to use...

---

### Post by Bucic on 2011-03-10
So, it looks like a draw and I need more opinions. :)

---

### Post by Hedgehog1 on 2011-03-10
Another opinion then:

Buy more RAM, and install the 64 bit.

If you will are not able to buy more RAM, go 32 bit, as this is compatible with even the oldest processors.

***The Hedge***

:KS

---

### Post by Dutch70 on 2011-03-10
I say if your processor can handle 64-bit, why not take advantage of it? 
[[COLOR="Blue"]64 bit or 32 bit[/COLOR]]("https://help.ubuntu.com/community/32bit_and_64bit#What%20should%20I%20choose%20-%2032%20or%2064%20bit?")
As previously suggested, I would go with at least 1GB of swap, or more if you plan to upgrade your RAM in the future.
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")
You may want to increase the recommended amounts here due to the 64-bit version.

---

### Post by Hedgehog1 on 2011-03-10
And the votes are even once again...  :D

---

### Post by kerry_s on 2011-03-10
it don't matter, really. performance gains are minimal. 

i like the feeling of 64bit on my system, just feels faster.

currently i'm running 32bit 11.04, because i made a usb installer for a friend & figured i'd just use what i got & switch to 64bit when 11.04 is released.

---

### Post by Bucic on 2011-03-10
Buying more RAM is not an option. I bought this zombie-laptop for a reason ;) and the compatible SODIMMs are overpriced as hell! A minimum sensible memory upgrade would cost me ~30% of what I have paid for the laptop.

**II**:
What I was hoping for is that negligible performance boost due to 64 bit would be followed by a more significant boost due to 64 bit systems and apps being compiled for newer CPU architecture (mine is AMD Turion 64). AFAIK all 32-bit Ubuntus and apps are compiled "to be on teh safe side" i.e. for crappy generic i386 architecture.

If the **II** is not true I >will< stick to 32-bit and install 64-bit only when I'll be doing a completely fresh Ubuntu install (without restoring any backed up settings).

---

### Post by Dutch70 on 2011-03-10
The best thing to do here is try it out first hand on your computer. 

If you're creating a partition for /home, then you'll be able to try one out for a few days & if you don't like it. It takes less than an hour to install the other.

---

### Post by Bucic on 2011-03-11
> **Dutch70 said:**
> The best thing to do here is try it out first hand on your computer. 

If you're creating a partition for /home, then you'll be able to try one out for a few days & if you don't like it. It takes less than an hour to install the other.
You know perfectly well that even in case of one compatibility problem  installing is nothing compared to configuring. And I face two compatibility problems on my laptop.

---

### Post by CrooKxD on 2011-03-11
If your processor can handle it I would do it for shits and grins, but I will say this I am using 64 bit Ubuntu and I dare say 90% of whats running in my processes are 32bit apps...Id upgrade the RAM before going 64bit since the 64bit OS isnt as widely supported as the 32bit (Your not going to be taking full advantage of the 64 bit OS if the apps are 32bit and the larger memory addresses will probably hang u up at some point)

---

### Post by Dutch70 on 2011-03-11
> **Bucic said:**
> You know perfectly well that even in case of one compatibility problem  installing is nothing compared to configuring. And I face two compatibility problems on my laptop.

You're quite welcome! :roll:

---

### Post by Bucic on 2011-03-11
@CrooKxD
So 64-bit system alone doesn't give considerable benefits? After all system components need memory and CPU too.

@Dutch70
I didn't mean to sound like an ungrateful bustard, sorry ;)

---

### Post by An Sanct on 2011-03-11
I'd say, go for the 64bit option - always. (if the processor supports it)

---

### Post by Bucic on 2011-03-11
> **An Sanct said:**
> I'd say, go for the 64bit option - always. (if the processor supports it)
Why? Lets say I'm marketing-proof :-k

---

### Post by An Sanct on 2011-03-11
64bit ... hm :) well, is more than 32bit ;)

okay, here is an example stolen from [wikipedia]("http://en.wikipedia.org/wiki/64-bit"):

>  Some 64-bit architectures, such as [x86-64]("http://en.wikipedia.org/wiki/X86-64"),   allow for more general purpose registers than their 32-bit   counterparts. This is a significant speed increase for tight loops since   the processor doesn't have to fetch data from the cache or main memory   if the data can fit in the available registers. Example in [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29"):
```
for (a=0; a<100; a++)
{   
   b = a; 
   c = b;   
   d = c;   
   e = d; 
}
```If a processor only has the ability to keep two three values/variables  in registers it would need to move some values between the stack and  registers to be able to process variable d and e as well; this is a  process that takes a lot of CPU cycles. A processor that is capable of  holding all the values/variables in registers can simply just loop  through this without needing to move data between registers and memory  for each iteration. This behavior can easily be compared with virtual  memory, although any effects are contingent upon the compiler.
And yes, 64bit OS uses more ram then 32bit OS.

PS. I would go 64bit for sure, even with 512Mb ram...
Take a look at the [wikipedia]("http://en.wikipedia.org/wiki/64-bit") article, it has a "pro/con" side, so you can choose easier.

---

### Post by Bucic on 2011-03-23
In the end I bought 1 GB of RAM for the zombie. It used to run on 1x250 MB and 1x512 MB of RAM. I replaced the 250 one with a 1 GB piece. Not only it used to be a low amount of RAM for a contemporary computer but also the 250 piece was running... at 133 MHz! :shock: So my whole memory package used to work at 133 MHz.

Now all work at 333 MHz with 1.3 GB available for system (excluding the portion reserved by graphics). It's a whole new system now.

I was also planning on buying "the fastest HDD for notebooks" (Samsung something) but it turned out that it's not much better than my original one in terms of access times, which parameter is crucial for desktop applications (continuous read/write speed being much less important). A huge thanks to **HD Tune** team and their database! =D>

---

